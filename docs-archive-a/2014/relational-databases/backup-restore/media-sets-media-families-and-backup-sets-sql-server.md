---
title: 媒體集、媒體家族與備份組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media sets [SQL Server], about media sets
- backup media [SQL Server], about backup media
- backups [SQL Server], media sets
- media sets [SQL Server]
- media headers [SQL Server]
- backup sets [SQL Server], about backup sets
- backup media [SQL Server], media sets
- backups [SQL Server], media families
- backup media [SQL Server], media families
- media families [SQL Server]
- backups [SQL Server], backup sets
- backup sets [SQL Server]
ms.assetid: 2b8f19a2-ee9d-4120-b194-fbcd2076a489
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 853451ea5a7c43cd073fdf75703b3c4651b442d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598486"
---
# <a name="media-sets-media-families-and-backup-sets-sql-server"></a><span data-ttu-id="511ee-102">媒體集、媒體家族與備份組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="511ee-102">Media Sets, Media Families, and Backup Sets (SQL Server)</span></span>
  <span data-ttu-id="511ee-103">本主題介紹 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原的基本備份媒體詞彙，適合供初次使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="511ee-103">This topic introduces the basic backup-media terminology of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore and is intended for readers who are new to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="511ee-104">此主題描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用於備份媒體的格式、備份媒體與備份裝置之間的對應、備份在備份媒體上的組織，以及媒體集和媒體家族的數個考量。</span><span class="sxs-lookup"><span data-stu-id="511ee-104">This topic describes the format that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for backup media, the correspondence between backup media and backup devices, the organization of backups on backup media, and several considerations for media sets and media families.</span></span> <span data-ttu-id="511ee-105">此主題也描述第一次使用備份媒體，或將舊媒體集取代為新媒體集之前初始化或格式化備份媒體的步驟、如何覆寫媒體集中舊備份組的步驟，以及如何將新備份組附加至媒體集的步驟。</span><span class="sxs-lookup"><span data-stu-id="511ee-105">The topic also describes the steps initializing or formatting backup media before you use it for the first time or replace an old media set with a new media set, how to overwrite old backup sets in a media set, and how to append new backup sets to a media set.</span></span>

> [!NOTE]
>  <span data-ttu-id="511ee-106">如需 SQL Server 備份至 Azure Blob 儲存體服務的詳細資訊，請參閱[SQL Server 使用 Azure Blob 儲存體服務的備份與還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="511ee-106">For more information on SQL Server backup to the Azure Blob storage service,, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>


##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="511ee-107">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="511ee-107">Terms and Definitions</span></span>
 <span data-ttu-id="511ee-108">媒體集 按順序排列的備份媒體集合 (磁帶或磁碟檔案)，由一個或多個備份作業使用固定的備份裝置類型與數量寫入。</span><span class="sxs-lookup"><span data-stu-id="511ee-108">media set An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>

 <span data-ttu-id="511ee-109">媒體家族 在單一非鏡像裝置上或媒體集的一組鏡像裝置上所建立的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-109">media family Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>

 <span data-ttu-id="511ee-110">備份組 透過成功的備份作業，加入至媒體集的備份內容。</span><span class="sxs-lookup"><span data-stu-id="511ee-110">backup set The backup content that is added to a media set by a successful backup operation.</span></span>


##  <a name="overview-of-media-sets-media-families-and-backup-sets"></a><a name="OvMediaSetsFamiliesBackupSets"></a><span data-ttu-id="511ee-111">媒體集、媒體家族和備份組的總覽</span><span class="sxs-lookup"><span data-stu-id="511ee-111">Overview of Media Sets, Media Families, and Backup Sets</span></span>
 <span data-ttu-id="511ee-112">單一媒體集是由一組一個或多個備份媒體上的備份組成。</span><span class="sxs-lookup"><span data-stu-id="511ee-112">The backups on a set of one or more backup media compose a single media set.</span></span> <span data-ttu-id="511ee-113">「媒體集」  (Media Set) 是按順序排列的「備份媒體」  (Backup Media) 集合 (磁帶、磁碟檔案或Azure Blob)，由一個或多個備份作業使用固定的備份裝置類型與數量寫入。</span><span class="sxs-lookup"><span data-stu-id="511ee-113">A *media set* is an ordered collection of *backup media*, tapes or disk files, or Azure Blobs, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="511ee-114">給定的媒體集會使用磁帶機、磁碟機或Azure Blob，但是不得為兩個以上的組合。</span><span class="sxs-lookup"><span data-stu-id="511ee-114">A given media set uses tape drives, or disk drives or Azure blobs, but not a combination of two or more.</span></span> <span data-ttu-id="511ee-115">例如，與媒體集相關的備份裝置可能是三個磁帶機，分別稱為 `\\.\TAPE0`、 `\\.\TAPE1`與 `\\.\TAPE2`。</span><span class="sxs-lookup"><span data-stu-id="511ee-115">For example, the backup devices associated with a media set might be three tape drives named `\\.\TAPE0`, `\\.\TAPE1`, and `\\.\TAPE2`.</span></span> <span data-ttu-id="511ee-116">此媒體集僅包含磁帶，一開始最少有三個磁帶 (每個磁帶機一個)。</span><span class="sxs-lookup"><span data-stu-id="511ee-116">That media set contains only tapes, starting with a minimum of three tapes (one per drive).</span></span> <span data-ttu-id="511ee-117">備份裝置類型與數量是在媒體集建立時確立，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="511ee-117">The type and number of backup devices are established when a media set is created, and they cannot be changed.</span></span> <span data-ttu-id="511ee-118">不過，可在必要時以相同類型的裝置取代備份和還原作業間的指定裝置。</span><span class="sxs-lookup"><span data-stu-id="511ee-118">However, if necessary, between backup and restore operations a given device can be replaced with a device of the same type.</span></span>

 <span data-ttu-id="511ee-119">媒體集是在備份作業格式化備份媒體期間，於備份媒體上建立。</span><span class="sxs-lookup"><span data-stu-id="511ee-119">A media set is created on the backup media during a backup operation by formatting the backup media.</span></span> <span data-ttu-id="511ee-120">如需詳細資訊，請參閱本主題稍後的 [建立新媒體集](#CreatingMediaSet)。</span><span class="sxs-lookup"><span data-stu-id="511ee-120">For more information, see [Creating a New Media Set](#CreatingMediaSet), later in this topic.</span></span> <span data-ttu-id="511ee-121">完成格式化後，每個檔案或磁帶會包含媒體集的媒體標頭，且備妥要接收備份內容。</span><span class="sxs-lookup"><span data-stu-id="511ee-121">After formatting, each file or tape contains a media header for the media set and is ready to receive backup content.</span></span> <span data-ttu-id="511ee-122">有了適當的標頭，備份作業就可以在指定供作業使用的所有備份裝置上，繼續將指定的資料備份至備份媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-122">With the header in place, the backup operation proceeds to back up the specified data to the backup media on all of the backup devices specified for the operation.</span></span>

> [!NOTE]
>  <span data-ttu-id="511ee-123">媒體集可以鏡像，避免損毀媒體磁碟區 (磁帶或磁碟檔案)。</span><span class="sxs-lookup"><span data-stu-id="511ee-123">Media sets can be mirrored to protect against a damaged media volume (a tape or disk file).</span></span> <span data-ttu-id="511ee-124">如需詳細資訊，請參閱本主題稍後的 [鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="511ee-124">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="511ee-125">或更新版本可以讀取壓縮的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-125">or later can read compressed backups.</span></span> <span data-ttu-id="511ee-126">如需詳細資訊，請參閱[備份壓縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="511ee-126">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


### <a name="media-families"></a><span data-ttu-id="511ee-127">媒體家族</span><span class="sxs-lookup"><span data-stu-id="511ee-127">Media Families</span></span>
 <span data-ttu-id="511ee-128">在單一非鏡像裝置上或媒體集鏡像裝置組上所建立的備份，即構成一個 *「媒體家族」* (Media family)。</span><span class="sxs-lookup"><span data-stu-id="511ee-128">Backups created on a single nonmirrored device or a set of mirrored devices in a media set constitute a *media family*.</span></span> <span data-ttu-id="511ee-129">媒體集使用的備份裝置數量決定媒體集內的媒體家族數。</span><span class="sxs-lookup"><span data-stu-id="511ee-129">The number of backup devices used for the media set determines the number of media families in a media set.</span></span> <span data-ttu-id="511ee-130">例如，如果媒體集使用兩個非鏡像的備份裝置，此媒體集即包含兩個媒體家族。</span><span class="sxs-lookup"><span data-stu-id="511ee-130">For example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>

> [!NOTE]
>  <span data-ttu-id="511ee-131">在鏡像的媒體集中，每個媒體家族都是鏡像。</span><span class="sxs-lookup"><span data-stu-id="511ee-131">In a mirrored media set, each media family is mirrored.</span></span> <span data-ttu-id="511ee-132">例如，如果使用六個備份裝置格式化媒體集，其中兩個使用鏡像，共有三個媒體家族，每個都包含兩份等量的備份資料。</span><span class="sxs-lookup"><span data-stu-id="511ee-132">For example, if six backup devices are used to format a media set, where two mirrors are used, there are three media families, each containing two equivalent copies of backup data.</span></span> <span data-ttu-id="511ee-133">如需鏡像媒體集的詳細資訊，請參閱 [鏡像備份媒體集 &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="511ee-133">For more information about mirrored media sets, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 <span data-ttu-id="511ee-134">媒體家族內的每個磁帶或磁碟都會指派一個 *「媒體序號」* 。</span><span class="sxs-lookup"><span data-stu-id="511ee-134">Each tape or disk in a media family is assigned a *media sequence number*.</span></span> <span data-ttu-id="511ee-135">磁碟的媒體序號永遠是 1。</span><span class="sxs-lookup"><span data-stu-id="511ee-135">The media sequence number of a disk is always 1.</span></span> <span data-ttu-id="511ee-136">在磁帶媒體家族中，初始磁帶的序號為 1，第二個磁帶的序號為 2，以此類推。</span><span class="sxs-lookup"><span data-stu-id="511ee-136">In a tape media family, the sequence number of the initial tape is 1, the sequence number of the second tape is 2, and so forth.</span></span> <span data-ttu-id="511ee-137">如需詳細資訊，請參閱 [使用媒體集和家族](#ConsiderationsForMediaSetFamilies)。</span><span class="sxs-lookup"><span data-stu-id="511ee-137">For more information, see [Using Media Sets and Families](#ConsiderationsForMediaSetFamilies).</span></span>

#### <a name="the-media-header"></a><span data-ttu-id="511ee-138">媒體標頭</span><span class="sxs-lookup"><span data-stu-id="511ee-138">The Media Header</span></span>
 <span data-ttu-id="511ee-139">備份媒體 (磁碟檔案或磁帶) 的每個磁碟區都包含一個媒體標頭，此標頭是由使用磁帶 (或磁碟) 的第一個備份作業所建立。</span><span class="sxs-lookup"><span data-stu-id="511ee-139">Every volume of backup media (disk file or tape) contains a media header that is created when by the first backup operation that uses the tape (or disk).</span></span> <span data-ttu-id="511ee-140">此標頭會保持不變，直到重新格式化媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-140">That header remains intact until the media is reformatted.</span></span>

 <span data-ttu-id="511ee-141">媒體標頭包含識別媒體 (磁碟檔案或磁帶) 所需的所有資訊，而標頭會位在所屬的媒體家族內。</span><span class="sxs-lookup"><span data-stu-id="511ee-141">The media header contains all of the information required to identify the media (disk file or tape) and its place within the media family to which it belongs.</span></span> <span data-ttu-id="511ee-142">此資訊包括：</span><span class="sxs-lookup"><span data-stu-id="511ee-142">This information includes:</span></span>

-   <span data-ttu-id="511ee-143">媒體的名稱。</span><span class="sxs-lookup"><span data-stu-id="511ee-143">The name of the media.</span></span>

     <span data-ttu-id="511ee-144">(選擇性) 建議您使用可清楚識別媒體的媒體名稱。</span><span class="sxs-lookup"><span data-stu-id="511ee-144">The media name is optionally, but we recommend consistently using media names that clearly identify your media.</span></span> <span data-ttu-id="511ee-145">媒體名稱是由格式化該媒體的人指派。</span><span class="sxs-lookup"><span data-stu-id="511ee-145">A media name is assigned by whoever formats the media.</span></span>

-   <span data-ttu-id="511ee-146">媒體集的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="511ee-146">The unique identification number of the media set.</span></span>

-   <span data-ttu-id="511ee-147">媒體集內的媒體家族編號。</span><span class="sxs-lookup"><span data-stu-id="511ee-147">The number of media families in the media set.</span></span>

-   <span data-ttu-id="511ee-148">包含此媒體之媒體家族的序號。</span><span class="sxs-lookup"><span data-stu-id="511ee-148">The sequence number of the media family containing this media.</span></span>

-   <span data-ttu-id="511ee-149">媒體家族的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="511ee-149">The unique identification number for the media family.</span></span>

-   <span data-ttu-id="511ee-150">媒體家族內此媒體的序號。</span><span class="sxs-lookup"><span data-stu-id="511ee-150">The sequence number of this media in the media family.</span></span> <span data-ttu-id="511ee-151">對於磁碟檔案，這個值永遠為 1。</span><span class="sxs-lookup"><span data-stu-id="511ee-151">For a disk file, this value is always 1.</span></span>

-   <span data-ttu-id="511ee-152">媒體描述是否包含 MTF 媒體標籤或媒體描述。</span><span class="sxs-lookup"><span data-stu-id="511ee-152">Whether the media description contains an MTF media label or a media description.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="511ee-153">用於備份或還原作業的所有媒體都使用名為的標準備份格式， [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] 保留由另一個應用程式所寫入的任何 mtf 媒體標籤，但是不會寫入 mtf 媒體標籤。</span><span class="sxs-lookup"><span data-stu-id="511ee-153">All media that is used for a backup or restore operation use a standard backup format called [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] preserves any MTF media label written by another application but does not write MTF media labels.</span></span>

-   <span data-ttu-id="511ee-154">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format 媒體標籤或媒體描述 (自由形式文字)。</span><span class="sxs-lookup"><span data-stu-id="511ee-154">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format media label or the media description (in free-form text).</span></span>

-   <span data-ttu-id="511ee-155">寫入標籤的備份軟體名稱。</span><span class="sxs-lookup"><span data-stu-id="511ee-155">The name of the backup software that wrote the label.</span></span>

-   <span data-ttu-id="511ee-156">格式化媒體之軟體廠商的唯一廠商識別碼。</span><span class="sxs-lookup"><span data-stu-id="511ee-156">The unique vendor identification number of the software vendor that formatted the media.</span></span>

-   <span data-ttu-id="511ee-157">寫入標籤時的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="511ee-157">The date and time the label was written.</span></span>

-   <span data-ttu-id="511ee-158">媒體集內的鏡像數目 (1-4)；1 代表無鏡像裝置。</span><span class="sxs-lookup"><span data-stu-id="511ee-158">The number of mirrors in the set (1-4); 1 indicates an unmirrored device.</span></span>

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="511ee-159">可處理由舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]格式化的媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-159">can process media formatted by earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

### <a name="backup-sets"></a><span data-ttu-id="511ee-160">備份組</span><span class="sxs-lookup"><span data-stu-id="511ee-160">Backup Sets</span></span>
 <span data-ttu-id="511ee-161">成功的備份作業會將一個 *「備份組」* (Backup set) 加入至媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-161">A successful backup operation adds a single *backup set* to the media set.</span></span> <span data-ttu-id="511ee-162">這個備份組是根據備份所屬的媒體集加以描述。</span><span class="sxs-lookup"><span data-stu-id="511ee-162">The backup set is described in terms of the media set to which the backup belongs.</span></span> <span data-ttu-id="511ee-163">如果備份媒體僅由一個媒體家族組成，則該家族就包含整個備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-163">If the backup media consists of only one media family, that family contains the entire backup set.</span></span> <span data-ttu-id="511ee-164">如果備份媒體由多個媒體家族組成，則備份組會分散於其中。</span><span class="sxs-lookup"><span data-stu-id="511ee-164">If the backup media consists of multiple media families, the backup set is distributed among them.</span></span> <span data-ttu-id="511ee-165">在每個媒體上，備份組都會包含描述該備份組的標頭。</span><span class="sxs-lookup"><span data-stu-id="511ee-165">On each medium, the backup set contains a header that describes the backup set.</span></span>

 <span data-ttu-id="511ee-166">以下範例顯示一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，為使用三個磁帶機做為備份裝置的 `MyAdvWorks_MediaSet_1` 資料庫，建立稱為 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-166">The following example shows a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates a media set called `MyAdvWorks_MediaSet_1` for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database using three tape drives as backup devices:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   FORMAT,
   MEDIANAME = 'MyAdvWorks_MediaSet_1'
```

 <span data-ttu-id="511ee-167">如果成功，此備份作業會產生新的媒體集，內含新的媒體標頭與一個分佈於三個磁帶的備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-167">If successful, this backup operation results in a new media set containing a new media header and one backup set spread across three tapes.</span></span> <span data-ttu-id="511ee-168">下圖說明這些結果：</span><span class="sxs-lookup"><span data-stu-id="511ee-168">The following figure illustrates these results:</span></span>

 <span data-ttu-id="511ee-169">![媒體標頭和 3 個磁帶上的第一個備份集](../../database-engine/media/bnr-mediaset-new.gif "媒體標頭和 3 個磁帶上的第一個備份集")</span><span class="sxs-lookup"><span data-stu-id="511ee-169">![Media header and first backup set on 3 tapes](../../database-engine/media/bnr-mediaset-new.gif "Media header and first backup set on 3 tapes")</span></span>

 <span data-ttu-id="511ee-170">一般來說，媒體集建立之後，隨後接連發生的備份作業，將會它們的備份組附加到媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-170">Typically, after a media set is created, subsequent backup operations, one after another, append their backup sets to the media set.</span></span> <span data-ttu-id="511ee-171">媒體集是由備份組使用的所有媒體組成，不論包含的媒體或備份裝置數目為何。</span><span class="sxs-lookup"><span data-stu-id="511ee-171">All of the media used by a backup set make up the media set, regardless of the number of media or backup devices involved.</span></span> <span data-ttu-id="511ee-172">備份組會根據它們在媒體集內的位置連續編號，您可以用以指定要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-172">Backup sets are sequentially numbered by their position in the media set, allowing you to specify which backup set to restore.</span></span>

 <span data-ttu-id="511ee-173">媒體集的每個備份作業必須寫入同一個的備份裝置編號與類型。</span><span class="sxs-lookup"><span data-stu-id="511ee-173">Every backup operation to a media set must write to the same number and type of backup devices.</span></span> <span data-ttu-id="511ee-174">如同第一個備份組一樣有多個裝置，隨後每個備份組的內容會分佈在所有裝置上的備份媒體中。</span><span class="sxs-lookup"><span data-stu-id="511ee-174">With multiple devices, as with the first backup set, the content of every subsequent backup set is distributed among the backup media on all of the devices.</span></span> <span data-ttu-id="511ee-175">繼續上述範例，第二個備份作業 (差異備份) 將資訊附加到相同的媒體集：</span><span class="sxs-lookup"><span data-stu-id="511ee-175">To continue the above example, a second backup operation (a differential backup) appends information to the same media set:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   NOINIT,
   MEDIANAME = 'AdventureWorksMediaSet1',
   DIFFERENTIAL
```

> [!NOTE]
>  <span data-ttu-id="511ee-176">NOINIT 選項是預設值，為了表明而包括於上。</span><span class="sxs-lookup"><span data-stu-id="511ee-176">The NOINIT option is the default, but is included for clarity.</span></span>

 <span data-ttu-id="511ee-177">如果第二個備份作業成功，就會將第二個備份組寫入媒體集，接連散發備份內容：</span><span class="sxs-lookup"><span data-stu-id="511ee-177">If the second backup operation succeeds, it writes a second backup set to the media set, with the following distribution of backup content:</span></span>

 <span data-ttu-id="511ee-178">![分散在 3 個媒體集磁帶上的第二個備份集](../../database-engine/media/bnr-mediaset-appendedto.gif "分散在 3 個媒體集磁帶上的第二個備份集")</span><span class="sxs-lookup"><span data-stu-id="511ee-178">![Second backup set spread across 3 media-set tapes](../../database-engine/media/bnr-mediaset-appendedto.gif "Second backup set spread across 3 media-set tapes")</span></span>

 <span data-ttu-id="511ee-179">當您要還原備份時，可以使用 FILE 選項來指定所要使用的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-179">When you are restoring backups, you can use you the FILE option to specify which backups you want to use.</span></span> <span data-ttu-id="511ee-180">下列範例示範 FILE **=** _backup_set_file_number_ 子句在還原 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的完整資料庫備份時的用法，並接著示範在相同媒體集上進行差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-180">The following example shows the use of FILE **=**_backup_set_file_number_ clauses when restoring a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database followed by a differential database backup on the same media set.</span></span> <span data-ttu-id="511ee-181">這個媒體集使用三個備份磁帶，分別位於磁帶機 `\\.\tape0`、 `tape1`和 `tape2`。</span><span class="sxs-lookup"><span data-stu-id="511ee-181">The media set uses three backup tapes, which are on tape drives `\\.\tape0`, `tape1`, and `tape2`.</span></span>

```
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=1, 
   NORECOVERY;
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2' 
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=2, 
   RECOVERY;
GO
```

 <span data-ttu-id="511ee-182">如需儲存媒體集與其媒體家族及備份組相關資訊之記錄資料表的相關資訊，請參閱 [備份記錄與標頭資訊 &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="511ee-182">For information about the history tables that store information about media sets and their media families and backup sets, see [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md).</span></span>

 <span data-ttu-id="511ee-183">媒體集內的備份媒體數量取決於數個因素：</span><span class="sxs-lookup"><span data-stu-id="511ee-183">The number of backup media in a media set depends on several factors:</span></span>

-   <span data-ttu-id="511ee-184">備份裝置數量</span><span class="sxs-lookup"><span data-stu-id="511ee-184">Number of backup devices</span></span>

-   <span data-ttu-id="511ee-185">備份裝置類型</span><span class="sxs-lookup"><span data-stu-id="511ee-185">Type of backup devices</span></span>

-   <span data-ttu-id="511ee-186">備份組數量</span><span class="sxs-lookup"><span data-stu-id="511ee-186">Number of backup sets</span></span>

##  <a name="using-media-sets-and-families"></a><a name="ConsiderationsForMediaSetFamilies"></a><span data-ttu-id="511ee-187">使用媒體集和家族</span><span class="sxs-lookup"><span data-stu-id="511ee-187">Using Media Sets and Families</span></span>
 <span data-ttu-id="511ee-188">本節討論使用媒體集與媒體家族的一些考量。</span><span class="sxs-lookup"><span data-stu-id="511ee-188">This section discusses several considerations for using media sets and media families.</span></span>



###  <a name="creating-a-new-media-set"></a><a name="CreatingMediaSet"></a><span data-ttu-id="511ee-189">建立新的媒體集</span><span class="sxs-lookup"><span data-stu-id="511ee-189">Creating a New Media Set</span></span>
 <span data-ttu-id="511ee-190">若要建立新的媒體集，您必須將備份媒體 (一個或多個磁帶或磁碟檔案) 格式化。</span><span class="sxs-lookup"><span data-stu-id="511ee-190">To create a new media set, you must format the backup media (one or more tapes or disk files).</span></span> <span data-ttu-id="511ee-191">格式化的過程會變更備份媒體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="511ee-191">The formatting process changes the backup media as follows:</span></span>

1.  <span data-ttu-id="511ee-192">刪除舊標頭 (若有的話)，有效率地刪除備份媒體上先前的內容。</span><span class="sxs-lookup"><span data-stu-id="511ee-192">Deletes the old header (if any), effectively deleting the previous contents of the backup media.</span></span>

     <span data-ttu-id="511ee-193">將磁帶裝置格式化，會刪除目前所掛載磁帶上的所有先前內容。</span><span class="sxs-lookup"><span data-stu-id="511ee-193">Formatting a tape device deletes all previous contents of the currently mounted tape.</span></span> <span data-ttu-id="511ee-194">將磁碟格式化，則只會影響您指定給備份作業的檔案。</span><span class="sxs-lookup"><span data-stu-id="511ee-194">Formatting a disk affects only the file that you specify for the backup operation</span></span>

2.  <span data-ttu-id="511ee-195">在每個備份裝置的備份媒體 (磁帶或磁碟檔案) 上寫入新的媒體標頭。</span><span class="sxs-lookup"><span data-stu-id="511ee-195">Writes a new media header on the backup media (tape or disk file) on each of the backup devices.</span></span>


###  <a name="backing-up-to-an-existing-media-set"></a><a name="UseExistingMediaSet"></a><span data-ttu-id="511ee-196">備份至現有的媒體集</span><span class="sxs-lookup"><span data-stu-id="511ee-196">Backing Up to an Existing Media Set</span></span>
 <span data-ttu-id="511ee-197">備份至現有的媒體集時，您有下列兩個選項：</span><span class="sxs-lookup"><span data-stu-id="511ee-197">When you are backing up to an existing media set, you have the following two options:</span></span>

-   <span data-ttu-id="511ee-198">附加至現有的媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-198">Append to the existing backup set.</span></span>

     <span data-ttu-id="511ee-199">為了盡可能善用可用空間，新的備份組通常會附加至現有的媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-199">To make the best possible use of the available space, new backup sets typically are appended to existing media set.</span></span> <span data-ttu-id="511ee-200">附加至備份會保留任何先前的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-200">Appending to the backup preserves any prior backups.</span></span> <span data-ttu-id="511ee-201">如需詳細資訊，請參閱本節稍後的 [附加至現有備份組](#Appending)。</span><span class="sxs-lookup"><span data-stu-id="511ee-201">For more information, see [Appending to Existing Backup Sets](#Appending), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="511ee-202">附加動作是 BACKUP 的預設行為，可以使用 NOINIT 選項明確地指定。</span><span class="sxs-lookup"><span data-stu-id="511ee-202">Appending, which is the default behavior of the BACKUP, can be explicitly specified by using the NOINIT option.</span></span>

-   <span data-ttu-id="511ee-203">以目前的備份來覆寫所有現有的備份組，將目前的媒體標頭留在原處。</span><span class="sxs-lookup"><span data-stu-id="511ee-203">Overwrite all existing backup sets with the current backup, leaving the current media header in place.</span></span>

     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="511ee-204">備份具有保護機制，可防止您在無意中覆寫媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-204">backup has safeguards to prevent you from accidentally overwriting media.</span></span> <span data-ttu-id="511ee-205">但是若備份組已達到預先定義的期限，備份就會自動覆寫備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-205">However, backup can automatically overwrite backup sets that have reached a predefined expiration date.</span></span>

     <span data-ttu-id="511ee-206">針對磁帶標頭，適當地保留標頭有其意義。</span><span class="sxs-lookup"><span data-stu-id="511ee-206">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="511ee-207">如需詳細資訊，請參閱本節稍後的 [覆寫備份組](#Overwriting)。</span><span class="sxs-lookup"><span data-stu-id="511ee-207">For more information, see [Overwriting Backup Sets](#Overwriting), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="511ee-208">若要覆寫現有的備份組，可以使用 BACKUP 陳述式的 INIT 選項來指定。</span><span class="sxs-lookup"><span data-stu-id="511ee-208">Overwriting existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span>

####  <a name="appending-to-existing-backup-sets"></a><a name="Appending"></a><span data-ttu-id="511ee-209">附加至現有的備份組</span><span class="sxs-lookup"><span data-stu-id="511ee-209">Appending to Existing Backup Sets</span></span>
 <span data-ttu-id="511ee-210">不同時間執行的備份可以寫在相同的媒體上，不論是不是來自相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="511ee-210">Backups performed at different times from the same or different databases can be stored on the same media.</span></span> <span data-ttu-id="511ee-211">藉由將另一個備份組附加至現有媒體的方法，就可以不影響媒體原先的內容，而在媒體最後一個備份結尾處寫入新的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-211">By appending another backup set to existing media, the previous contents of the media remain intact, and the new backup is written after the end of the last backup on the media.</span></span>

 <span data-ttu-id="511ee-212">依預設值， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一定會將新備份附加至媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-212">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always appends new backups to media.</span></span> <span data-ttu-id="511ee-213">附加只可以發生在媒體結尾。</span><span class="sxs-lookup"><span data-stu-id="511ee-213">Appending can occur only at the end of the media.</span></span> <span data-ttu-id="511ee-214">例如，如果媒體磁碟區包含五個備份組，就無法跳過前三個備份組，而使用新的備份組覆寫第四個備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-214">For example, if a media volume contains five backup sets, it is not possible to skip the first three backup sets to overwrite the fourth backup set with a new backup set.</span></span>

 <span data-ttu-id="511ee-215">如果磁帶備份採用 BACKUP WITH NOREWIND，則在作業結束後，磁帶會保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="511ee-215">If you use BACKUP WITH NOREWIND for a tape backup, the tape will be left open at the end of the operation.</span></span> <span data-ttu-id="511ee-216">這樣您就可以在磁帶上附加其他備份，否則就得將磁帶倒帶，再向前搜尋，找出最後的備份組。</span><span class="sxs-lookup"><span data-stu-id="511ee-216">This allows you to append further backups to the tape without rewinding the tape and then scanning forward again to find the last backup set.</span></span> <span data-ttu-id="511ee-217">您可以在 **sys.dm_io_backup_tapes** 動態管理檢視中找出開啟的磁帶機清單。如需詳細資訊，請參閱 [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="511ee-217">You can find the list of open tape drives in the **sys.dm_io_backup_tapes** dynamic management view; for more information, see [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql).</span></span>

 <span data-ttu-id="511ee-218">Microsoft Windows 備份和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份可以共用相同的媒體，但是無法相互操作。</span><span class="sxs-lookup"><span data-stu-id="511ee-218">Microsoft Windows backups and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups can share the same media, but they are not interoperable.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="511ee-219">備份無法備份 Windows 資料。</span><span class="sxs-lookup"><span data-stu-id="511ee-219">backup cannot back up Windows data.</span></span>

> [!IMPORTANT]
>  [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="511ee-220">或更新版本可以讀取壓縮的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-220">or later versions can read compressed backups.</span></span> <span data-ttu-id="511ee-221">如需詳細資訊，請參閱[備份壓縮 &#40;SQL Server&#41;](backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="511ee-221">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


####  <a name="overwriting-backup-sets"></a><a name="Overwriting"></a><span data-ttu-id="511ee-222">覆寫備份組</span><span class="sxs-lookup"><span data-stu-id="511ee-222">Overwriting Backup Sets</span></span>
 <span data-ttu-id="511ee-223">若要覆寫現有的備份組，可以使用 BACKUP 陳述式的 INIT 選項來指定。</span><span class="sxs-lookup"><span data-stu-id="511ee-223">Overwriting of existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span> <span data-ttu-id="511ee-224">這個選項會覆寫媒體中的所有備份組，並保留媒體標頭 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="511ee-224">This option overwrites all the backup sets on the media and preserve the media header, if any.</span></span> <span data-ttu-id="511ee-225">如果沒有媒體標頭，就會加以建立。</span><span class="sxs-lookup"><span data-stu-id="511ee-225">If no media header exists, one is created.</span></span>

 <span data-ttu-id="511ee-226">針對磁帶標頭，適當地保留標頭有其意義。</span><span class="sxs-lookup"><span data-stu-id="511ee-226">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="511ee-227">對於磁碟備份媒體而言，只有備份作業中指定的備份裝置所用的檔案會被覆寫，磁碟上的其他檔案則不受影響。</span><span class="sxs-lookup"><span data-stu-id="511ee-227">For disk backup media, only the files used by the backup devices specified in the backup operation are overwritten; other files on the disk are unaffected.</span></span> <span data-ttu-id="511ee-228">覆寫備份時會保留任何現有的媒體標頭，而新的備份會建立為備份裝置上的第一個備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-228">When overwriting backups, any existing media header is preserved, and the new backup is created as the first backup on the backup device.</span></span> <span data-ttu-id="511ee-229">如果沒有現有的媒體標頭，則會自動寫入含相關媒體名稱與媒體描述的有效媒體標頭。</span><span class="sxs-lookup"><span data-stu-id="511ee-229">If there is no existing media header, a valid media header with an associated media name and media description is written automatically.</span></span> <span data-ttu-id="511ee-230">如果現有的媒體標頭無效，備份作業會終止。</span><span class="sxs-lookup"><span data-stu-id="511ee-230">If the existing media header is invalid, the backup operation terminates.</span></span> <span data-ttu-id="511ee-231">若為空白媒體，則會以給定的 MEDIANAME、MEDIAPASSWORD 與 MEDIADESCRIPTION (若有的話) 來產生新的媒體標頭。</span><span class="sxs-lookup"><span data-stu-id="511ee-231">If the media is empty, the new media header is generated with the given MEDIANAME, MEDIAPASSWORD, and MEDIADESCRIPTION, if any.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="511ee-232">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，MEDIAPASSWORD 選項無法再用於建立備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-232">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the MEDIAPASSWORD option is discontinued for creating backups.</span></span> <span data-ttu-id="511ee-233">不過，您還是可以還原以密碼建立的備份。</span><span class="sxs-lookup"><span data-stu-id="511ee-233">However, you can still restore backups created with passwords.</span></span>

 <span data-ttu-id="511ee-234">若發生下列其中一種情況，就不會覆寫備份媒體：</span><span class="sxs-lookup"><span data-stu-id="511ee-234">Backup media is not overwritten if either of the following conditions exists:</span></span>

-   <span data-ttu-id="511ee-235">媒體上的現有備份尚未到期</span><span class="sxs-lookup"><span data-stu-id="511ee-235">The existing backups on the media have not expired.</span></span> <span data-ttu-id="511ee-236">(若指定了 SKIP，則不會檢查到期日)。</span><span class="sxs-lookup"><span data-stu-id="511ee-236">(If SKIP is specified, expiration is not checked.)</span></span>

     <span data-ttu-id="511ee-237">到期日會指定備份過期的日期，之後就可以被別的備份覆寫。</span><span class="sxs-lookup"><span data-stu-id="511ee-237">The expiration date specifies the date that the backup expires and can be overwritten by another backup.</span></span> <span data-ttu-id="511ee-238">建立備份時，可以指定到期日。</span><span class="sxs-lookup"><span data-stu-id="511ee-238">You can specify the expiration date when a backup is created.</span></span> <span data-ttu-id="511ee-239">依預設，到期日是由 **sp_configure** 所設定的 **media retention**選項來決定。</span><span class="sxs-lookup"><span data-stu-id="511ee-239">By default, the expiration date is determined by the **media retention** option set with **sp_configure**.</span></span> <span data-ttu-id="511ee-240">如需詳細資訊，請參閱本主題稍後的 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)的使用者閱讀。</span><span class="sxs-lookup"><span data-stu-id="511ee-240">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>

-   <span data-ttu-id="511ee-241">媒體名稱 (如果提供的話) 不符合備份媒體的名稱。</span><span class="sxs-lookup"><span data-stu-id="511ee-241">The media name, if provided, does not match the name on the backup media.</span></span>

     <span data-ttu-id="511ee-242">媒體名稱是為了易於識別媒體而用的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="511ee-242">The media name is a descriptive name used for easy identification of the media.</span></span>

 <span data-ttu-id="511ee-243">如果確定要覆寫現有媒體 (例如，如果知道已不再需要磁帶上的備份)，就可以明確地略過這些檢查。</span><span class="sxs-lookup"><span data-stu-id="511ee-243">If you are sure you want to overwrite the existing media (for example, if you know that the backups on the tape are no longer needed), you can explicitly skip these checks.</span></span>

 <span data-ttu-id="511ee-244">若備份媒體受到 Microsoft Windows 的密碼保護，Microsoft SQL Server 就無法寫入此媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-244">If the backup media is password protected by Microsoft Windows, Microsoft SQL Server does not write to the media.</span></span> <span data-ttu-id="511ee-245">若要覆寫受到密碼保護的媒體，您必須重新初始化該媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-245">To overwrite media that is password protected, you must reinitialize the media.</span></span>


###  <a name="sequence-numbers"></a><a name="SequenceNumbers"></a><span data-ttu-id="511ee-246">序號</span><span class="sxs-lookup"><span data-stu-id="511ee-246">Sequence Numbers</span></span>
 <span data-ttu-id="511ee-247">對於媒體集或媒體家族內的多個備份媒體而言，有正確的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="511ee-247">The correct order is important for multiple media families within a media set or multiple backup media within a media family.</span></span> <span data-ttu-id="511ee-248">因此，備份會依照下列方式指派序號：</span><span class="sxs-lookup"><span data-stu-id="511ee-248">Therefore, backup assigns sequence numbers in the following ways:</span></span>

-   <span data-ttu-id="511ee-249">媒體集內的連續媒體家族</span><span class="sxs-lookup"><span data-stu-id="511ee-249">Sequential media families within a media set</span></span>

     <span data-ttu-id="511ee-250">媒體集內的媒體家族，會根據其在媒體集內的位置依順序編號。</span><span class="sxs-lookup"><span data-stu-id="511ee-250">Within a media set, the media families are numbered sequentially according to their position in the media set.</span></span> <span data-ttu-id="511ee-251">媒體家族的編號是記錄在 **backupmediafamily** 資料表的 **family_sequence_number** 資料行中。</span><span class="sxs-lookup"><span data-stu-id="511ee-251">The media-family number is recorded in the **family_sequence_number** column of the **backupmediafamily** table.</span></span>

-   <span data-ttu-id="511ee-252">媒體家族內的實體媒體</span><span class="sxs-lookup"><span data-stu-id="511ee-252">Physical media within a media family</span></span>

     <span data-ttu-id="511ee-253">媒體序號代表實體媒體在媒體家族內的順序。</span><span class="sxs-lookup"><span data-stu-id="511ee-253">A media sequence number indicates the order of the physical media within a media family.</span></span> <span data-ttu-id="511ee-254">初始備份媒體的序號是 1。</span><span class="sxs-lookup"><span data-stu-id="511ee-254">The sequence number is 1 for the initial backup media.</span></span> <span data-ttu-id="511ee-255">這會標記為 1；第二個 (第一個接續磁帶) 會標記為 2；依此類推。</span><span class="sxs-lookup"><span data-stu-id="511ee-255">This is tagged with 1; the second (the first continuation tape) is tagged with 2; and so on.</span></span> <span data-ttu-id="511ee-256">在還原備份組時，媒體序號可確保還原備份的操作員以正確的順序掛載正確的媒體。</span><span class="sxs-lookup"><span data-stu-id="511ee-256">When the backup set is restored, the media sequence numbers make sure that the operator restoring the backup mounts the correct media in the correct order.</span></span>

###  <a name="multiple-devices"></a><a name="MultipleDevices"></a> <span data-ttu-id="511ee-257">多個裝置</span><span class="sxs-lookup"><span data-stu-id="511ee-257">Multiple Devices</span></span>
 <span data-ttu-id="511ee-258">使用多個磁帶機或磁碟檔案時，需考量以下事項：</span><span class="sxs-lookup"><span data-stu-id="511ee-258">When you use multiple tape drives or disk files, the following considerations apply:</span></span>

-   <span data-ttu-id="511ee-259">備份方面：</span><span class="sxs-lookup"><span data-stu-id="511ee-259">For backup:</span></span>

     <span data-ttu-id="511ee-260">後續的所有備份作業必須使用備份作業所建立的整個媒體集。</span><span class="sxs-lookup"><span data-stu-id="511ee-260">The complete media set that is created by a backup operation must be used by all subsequent backup operations.</span></span> <span data-ttu-id="511ee-261">例如，如果使用兩個磁帶備份裝置建立媒體集，後續涉及相同媒體集的所有備份作業都必須使用兩個備份裝置。</span><span class="sxs-lookup"><span data-stu-id="511ee-261">For example, if a media set was created by using two tape backup devices, all subsequent backup operations that involve the same media set must use two backup devices.</span></span>

-   <span data-ttu-id="511ee-262">還原方面：</span><span class="sxs-lookup"><span data-stu-id="511ee-262">For restore:</span></span>

     <span data-ttu-id="511ee-263">對磁碟備份中的任何還原以及任何線上還原而言，必須同時掛載全體媒體家族中的所有家族。</span><span class="sxs-lookup"><span data-stu-id="511ee-263">For any restore from disk backups and for any online restore, all the all media families must be concurrently mounted.</span></span> <span data-ttu-id="511ee-264">若要從磁帶備份中進行離線還原，則可以較少的備份裝置處理媒體家族。</span><span class="sxs-lookup"><span data-stu-id="511ee-264">For an offline restore from tape backups, you can process the media families from fewer backup devices.</span></span> <span data-ttu-id="511ee-265">對每個媒體家族而言，其處理必須先完成，另一個媒體家族的處理才會開始。</span><span class="sxs-lookup"><span data-stu-id="511ee-265">Each media family must be processed completely before starting to process another media family.</span></span> <span data-ttu-id="511ee-266">媒體家族永遠會平行處理，除非是以單一裝置進行還原。</span><span class="sxs-lookup"><span data-stu-id="511ee-266">Media families are always processed in parallel, unless they are being restored with a single device.</span></span>

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="511ee-267">相關工作</span><span class="sxs-lookup"><span data-stu-id="511ee-267">Related Tasks</span></span>
 <span data-ttu-id="511ee-268">**建立新的媒體集**</span><span class="sxs-lookup"><span data-stu-id="511ee-268">**To create a new media set**</span></span>

-   <span data-ttu-id="511ee-269">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ([備份至新的媒體集，並清除所有現有的備份組]  選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-269">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Back up to a new media set, and erase all existing backup sets** option)</span></span>

-   <span data-ttu-id="511ee-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT 選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT option)</span></span>

-   <xref:Microsoft.SqlServer.Management.Smo.Backup.FormatMedia%2A>

 <span data-ttu-id="511ee-271">**將新備份附加至現有媒體**</span><span class="sxs-lookup"><span data-stu-id="511ee-271">**To append a new backup to existing media**</span></span>

-   <span data-ttu-id="511ee-272">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ([附加至現有的備份組]  選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-272">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Append to the existing backup set** option)</span></span>

-   <span data-ttu-id="511ee-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT 選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT option)</span></span>

 <span data-ttu-id="511ee-274">**覆寫現有備份組**</span><span class="sxs-lookup"><span data-stu-id="511ee-274">**To overwrite existing backup sets**</span></span>

-   <span data-ttu-id="511ee-275">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) ([覆寫所有現有的備份組]  選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-275">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Overwrite all existing backup sets** option)</span></span>

-   <span data-ttu-id="511ee-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT 選項)</span><span class="sxs-lookup"><span data-stu-id="511ee-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT option)</span></span>

 <span data-ttu-id="511ee-277">**設定到期日**</span><span class="sxs-lookup"><span data-stu-id="511ee-277">**To set the expiration date**</span></span>

-   [<span data-ttu-id="511ee-278">設定備份的到期日 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-278">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)

 <span data-ttu-id="511ee-279">**檢視媒體順序與家族序號**</span><span class="sxs-lookup"><span data-stu-id="511ee-279">**To view the media sequence and family sequence numbers**</span></span>

-   [<span data-ttu-id="511ee-280">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-280">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   <span data-ttu-id="511ee-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** 資料行)</span><span class="sxs-lookup"><span data-stu-id="511ee-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** column)</span></span>

 <span data-ttu-id="511ee-282">**檢視特定備份裝置上的備份組**</span><span class="sxs-lookup"><span data-stu-id="511ee-282">**To view the backup sets on a particular backup device**</span></span>

-   [<span data-ttu-id="511ee-283">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-283">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)

-   [<span data-ttu-id="511ee-284">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-284">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   [<span data-ttu-id="511ee-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)

 <span data-ttu-id="511ee-286">**若要讀取備份裝置上媒體的媒體標頭**</span><span class="sxs-lookup"><span data-stu-id="511ee-286">**To read the media header of the media on a backup device**</span></span>

-   [<span data-ttu-id="511ee-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="511ee-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)


## <a name="see-also"></a><span data-ttu-id="511ee-288">另請參閱</span><span class="sxs-lookup"><span data-stu-id="511ee-288">See Also</span></span>
 <span data-ttu-id="511ee-289">備份與還原[SQL Server 資料庫](back-up-and-restore-of-sql-server-databases.md)[在備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [備份歷程記錄和標頭資訊](backup-history-and-header-information-sql-server.md) [&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) [&#40;備份 SQL Server transact-sql&#41;](/sql/t-sql/statements/backup-transact-sql) [還原](/sql/t-sql/statements/restore-statements-transact-sql)&#40;transact-sql&#41;[&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) [&#40;transact-sql&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="511ee-289">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span></span>


