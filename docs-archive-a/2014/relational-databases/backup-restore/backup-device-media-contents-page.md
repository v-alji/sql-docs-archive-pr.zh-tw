---
title: 備份裝置 (媒體內容頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.contents.f1
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07204b5e05ce9fc17e6ea23450066f9f58b7cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596736"
---
# <a name="backup-device-media-contents-page"></a><span data-ttu-id="4147f-102">備份裝置 (媒體內容頁面)</span><span class="sxs-lookup"><span data-stu-id="4147f-102">Backup Device (Media Contents Page)</span></span>
  <span data-ttu-id="4147f-103">使用 **[備份裝置]** 對話方塊來檢視備份資訊。</span><span class="sxs-lookup"><span data-stu-id="4147f-103">Use the **Backup Device** dialog box to view the backup information.</span></span> <span data-ttu-id="4147f-104">這個資訊描述裝置、媒體、媒體集，以及備份組。</span><span class="sxs-lookup"><span data-stu-id="4147f-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="4147f-105">**若要使用 SQL Server Management Studio 檢視備份裝置的內容**</span><span class="sxs-lookup"><span data-stu-id="4147f-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="4147f-106">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="4147f-107">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="4147f-108">選項。</span><span class="sxs-lookup"><span data-stu-id="4147f-108">Options</span></span>  
 <span data-ttu-id="4147f-109">檢視有關個別媒體、媒體集和備份組的資訊。</span><span class="sxs-lookup"><span data-stu-id="4147f-109">View information about the individual media, media set, and backup sets.</span></span>  
  
 <span data-ttu-id="4147f-110">**媒體**</span><span class="sxs-lookup"><span data-stu-id="4147f-110">**Media**</span></span>  
 <span data-ttu-id="4147f-111">儲存備份資訊的磁碟或磁帶集。</span><span class="sxs-lookup"><span data-stu-id="4147f-111">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="4147f-112">**媒體順序**</span><span class="sxs-lookup"><span data-stu-id="4147f-112">**Media sequence**</span></span>  
 <span data-ttu-id="4147f-113">列出媒體序號、家族序號，以及鏡像識別碼 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="4147f-113">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="4147f-114">各個實體備份媒體都標記有媒體序號，指出媒體使用時的順序。</span><span class="sxs-lookup"><span data-stu-id="4147f-114">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="4147f-115">初始備份媒體會標記為 1，第二個 (第一個接續磁帶) 則會標記為 2，依此類推。</span><span class="sxs-lookup"><span data-stu-id="4147f-115">The initial backup media is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="4147f-116">在還原備份組時，媒體序號可確保還原備份的操作員以正確的順序掛載正確的媒體。</span><span class="sxs-lookup"><span data-stu-id="4147f-116">When the backup set is restored, the media sequence numbers ensure that the operator restoring the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="4147f-117">**建立於**</span><span class="sxs-lookup"><span data-stu-id="4147f-117">**Created on**</span></span>  
 <span data-ttu-id="4147f-118">顯示媒體集的建立日期和時間。</span><span class="sxs-lookup"><span data-stu-id="4147f-118">Displays the creation date and time of the media set.</span></span>  
  
 <span data-ttu-id="4147f-119">**媒體集**</span><span class="sxs-lookup"><span data-stu-id="4147f-119">**Media Set**</span></span>  
 <span data-ttu-id="4147f-120">媒體集是備份媒體的已排序集合，在其中使用固定數目的備份裝置寫入一個或多個備份作業。</span><span class="sxs-lookup"><span data-stu-id="4147f-120">A media set is an ordered collection of backup media to which one or more backup operations have written by using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="4147f-121">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4147f-121">**Name**</span></span>  
 <span data-ttu-id="4147f-122">顯示媒體集的名稱 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="4147f-122">Displays the name of the media set, if any.</span></span>  
  
 <span data-ttu-id="4147f-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="4147f-123">**Description**</span></span>  
 <span data-ttu-id="4147f-124">顯示媒體集的描述 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="4147f-124">Displays the description of the media set, if any.</span></span>  
  
 <span data-ttu-id="4147f-125">**媒體家族計數**</span><span class="sxs-lookup"><span data-stu-id="4147f-125">**Media family count**</span></span>  
 <span data-ttu-id="4147f-126">顯示媒體集內的家族數目。</span><span class="sxs-lookup"><span data-stu-id="4147f-126">Displays the number of families in the media set.</span></span> <span data-ttu-id="4147f-127">各個媒體集皆是一個或多個媒體家族的集合。</span><span class="sxs-lookup"><span data-stu-id="4147f-127">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="4147f-128">所有輸出到給定的單一備份裝置 (或鏡像的備份裝置群組)，即形成一個單一媒體家族。</span><span class="sxs-lookup"><span data-stu-id="4147f-128">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="4147f-129">每一個媒體集都會針對個別的裝置 (或鏡像裝置的群組) 組成一個媒體家族；例如，如果媒體集使用兩個非鏡像的備份裝置，媒體集就會包含兩個媒體家族。</span><span class="sxs-lookup"><span data-stu-id="4147f-129">Each media set contains one media family per separate device (or group of mirrored devices); for instance, if a media set uses two non-mirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="4147f-130">**備份組**</span><span class="sxs-lookup"><span data-stu-id="4147f-130">**Backup sets**</span></span>  
 <span data-ttu-id="4147f-131">顯示有關媒體上包含的備份組的資訊。</span><span class="sxs-lookup"><span data-stu-id="4147f-131">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="4147f-132">備份組是成功備份作業的結果，其內容會散發在備份裝置集的媒體上。</span><span class="sxs-lookup"><span data-stu-id="4147f-132">A backup set is the result of a successful backup operation, whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="4147f-133">頁首</span><span class="sxs-lookup"><span data-stu-id="4147f-133">Header</span></span>|<span data-ttu-id="4147f-134">值</span><span class="sxs-lookup"><span data-stu-id="4147f-134">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="4147f-135">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4147f-135">**Name**</span></span>|<span data-ttu-id="4147f-136">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4147f-136">The name of the backup set.</span></span>|  
|<span data-ttu-id="4147f-137">**型別**</span><span class="sxs-lookup"><span data-stu-id="4147f-137">**Type**</span></span>|<span data-ttu-id="4147f-138">備份的物件：資料庫、檔案或 *\<blank>* (適用於交易記錄)。</span><span class="sxs-lookup"><span data-stu-id="4147f-138">The backed-up object: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="4147f-139">**元件**</span><span class="sxs-lookup"><span data-stu-id="4147f-139">**Component**</span></span>|<span data-ttu-id="4147f-140">執行的備份類型：[完整]、[差異] 或 [交易記錄]。</span><span class="sxs-lookup"><span data-stu-id="4147f-140">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="4147f-141">**Server**</span><span class="sxs-lookup"><span data-stu-id="4147f-141">**Server**</span></span>|<span data-ttu-id="4147f-142">執行備份作業之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="4147f-142">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="4147f-143">**Database**</span><span class="sxs-lookup"><span data-stu-id="4147f-143">**Database**</span></span>|<span data-ttu-id="4147f-144">已備份資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4147f-144">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="4147f-145">**位置**</span><span class="sxs-lookup"><span data-stu-id="4147f-145">**Position**</span></span>|<span data-ttu-id="4147f-146">備份組在磁碟區中的位置。</span><span class="sxs-lookup"><span data-stu-id="4147f-146">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="4147f-147">**日期**</span><span class="sxs-lookup"><span data-stu-id="4147f-147">**Date**</span></span>|<span data-ttu-id="4147f-148">備份作業完成時的日期和時間，會出現在用戶端的地區設定中。</span><span class="sxs-lookup"><span data-stu-id="4147f-148">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="4147f-149">**大小**</span><span class="sxs-lookup"><span data-stu-id="4147f-149">**Size**</span></span>|<span data-ttu-id="4147f-150">備份組的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="4147f-150">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="4147f-151">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="4147f-151">**User Name**</span></span>|<span data-ttu-id="4147f-152">執行備份作業的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4147f-152">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="4147f-153">**到期**</span><span class="sxs-lookup"><span data-stu-id="4147f-153">**Expiration**</span></span>|<span data-ttu-id="4147f-154">備份組過期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="4147f-154">The date and time the backup set expires.</span></span>|  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4147f-155">相關工作</span><span class="sxs-lookup"><span data-stu-id="4147f-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4147f-156">定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-156">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="4147f-157">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-157">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="4147f-158">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-158">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="4147f-159">刪除備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-159">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="4147f-160">設定備份的到期日 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-160">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="4147f-161">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-161">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="4147f-162">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-162">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="4147f-163">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-163">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="4147f-164">從裝置還原備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-164">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4147f-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4147f-165">See Also</span></span>  
 <span data-ttu-id="4147f-166">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4147f-166">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="4147f-167">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4147f-167">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
