---
title: 備份裝置 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592074"
---
# <a name="backup-device-general-page"></a><span data-ttu-id="a3cad-102">備份裝置 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="a3cad-102">Backup Device (General Page)</span></span>
  <span data-ttu-id="a3cad-103">使用 **[一般]** 頁面，可指定或檢視邏輯備份裝置的一般屬性。</span><span class="sxs-lookup"><span data-stu-id="a3cad-103">Use the **General** page to specify or view the general properties of a logical backup device.</span></span>  
  
 <span data-ttu-id="a3cad-104">**若要使用 SQL Server Management Studio 檢視備份裝置的內容**</span><span class="sxs-lookup"><span data-stu-id="a3cad-104">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="a3cad-105">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-105">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-106">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-106">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="a3cad-107">選項。</span><span class="sxs-lookup"><span data-stu-id="a3cad-107">Options</span></span>  
 <span data-ttu-id="a3cad-108">**裝置名稱**</span><span class="sxs-lookup"><span data-stu-id="a3cad-108">**Device name**</span></span>  
 <span data-ttu-id="a3cad-109">檢視現有邏輯備份裝置的名稱，或是指定新邏輯備份裝置的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3cad-109">View the name of an existing logical backup device or specify the name of a new logical backup device.</span></span>  
  
 <span data-ttu-id="a3cad-110">**磁帶**</span><span class="sxs-lookup"><span data-stu-id="a3cad-110">**Tape**</span></span>  
 <span data-ttu-id="a3cad-111">在 [磁帶]  清單中檢視或選取目的地磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="a3cad-111">View or select the destination tape device in the **Tape** list.</span></span> <span data-ttu-id="a3cad-112">只有當磁帶機已連結到執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體的電腦上時，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="a3cad-112">This option is available only if a tape drive is attached to the computer that is running the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3cad-113">遠端電腦上的磁帶備份裝置並不是有效的備份目的地。</span><span class="sxs-lookup"><span data-stu-id="a3cad-113">Tape backup devices on remote computers are not valid backup destinations.</span></span>  
  
 <span data-ttu-id="a3cad-114">**檔案**</span><span class="sxs-lookup"><span data-stu-id="a3cad-114">**File**</span></span>  
 <span data-ttu-id="a3cad-115">檢視現有邏輯備份裝置的目的地檔案，或是指定新邏輯備份裝置的目的地檔案。</span><span class="sxs-lookup"><span data-stu-id="a3cad-115">View the destination file of an existing logical backup device, or specify a destination file for a new logical backup device.</span></span>  
  
-   <span data-ttu-id="a3cad-116">如果是現有的邏輯備份裝置，則會顯示備份檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3cad-116">For an existing logical backup device, the path of the backup file is displayed.</span></span> <span data-ttu-id="a3cad-117">**[檔案]** 欄位無法編輯，而且 [瀏覽] 按鈕無法使用。</span><span class="sxs-lookup"><span data-stu-id="a3cad-117">The **File** field is not editable, and the Browse button is unavailable.</span></span>  
  
-   <span data-ttu-id="a3cad-118">如果是新的邏輯備份裝置，您必須提供要定義邏輯備份裝置之備份檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a3cad-118">For a new logical backup device, you must supply the path of the backup file for which you are defining the logical backup device.</span></span> <span data-ttu-id="a3cad-119">這個檔案目前尚不存在。</span><span class="sxs-lookup"><span data-stu-id="a3cad-119">This file does not have to exist yet.</span></span>  
  
     <span data-ttu-id="a3cad-120">若要指定邏輯備份檔案，可以按一下 **[檔案]** 文字方塊右邊的 [瀏覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a3cad-120">To specify a local backup file, you can click the Browse button to the right of the **File** text box.</span></span> <span data-ttu-id="a3cad-121">接著，您可以在 **[尋找資料庫檔案]** 對話方塊中，導覽至執行伺服器執行個體之電腦中任何固定磁碟機上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="a3cad-121">Then, in the **Locate Database Files** dialog box, you can navigate to any location on any of the fixed drives on the computer running the server instance.</span></span> <span data-ttu-id="a3cad-122">如果備份檔案尚不存在，則您必須在該對話方塊的 **[檔案名稱]** 欄位中輸入您要使用的檔名。</span><span class="sxs-lookup"><span data-stu-id="a3cad-122">If the backup file does not exist yet, you must enter the filename you want to use in the **File name** field of that dialog box.</span></span>  
  
     <span data-ttu-id="a3cad-123">或者，您可以用手動方式編輯 **[檔案]** 欄位，以覆寫預設的路徑、檔案名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="a3cad-123">Alternatively, you can edit the **File** field manually to override the default path, file name, and extension.</span></span> <span data-ttu-id="a3cad-124">若要指定遠端檔案做為備份目的地，請輸入其完整的通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="a3cad-124">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="a3cad-125">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="a3cad-125">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a3cad-126">透過網路備份資料可能會受到網路錯誤的影響，因此，建議您在備份作業完成之後要進行確認。</span><span class="sxs-lookup"><span data-stu-id="a3cad-126">Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="a3cad-127">如需詳細資訊，請參閱 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a3cad-127">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3cad-128">備註</span><span class="sxs-lookup"><span data-stu-id="a3cad-128">Remarks</span></span>  
 <span data-ttu-id="a3cad-129">單一媒體集是由一組一個或多個備份裝置上的備份所組成。</span><span class="sxs-lookup"><span data-stu-id="a3cad-129">The backups on a set of one or more backup devices compose a single media set.</span></span> <span data-ttu-id="a3cad-130">*「媒體集」* 是按順序排列的備份媒體集合 (磁帶或磁碟檔案)，由一個或多個的備份作業使用固定的備份裝置類型與數量寫入。</span><span class="sxs-lookup"><span data-stu-id="a3cad-130">A *media set* is an ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="a3cad-131">如需媒體集的一般資訊，請參閱 [媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)之執行個體的電腦上時，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="a3cad-131">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="a3cad-132">將媒體集中的第一個備份寫入邏輯備份裝置時，會初始化對應於邏輯備份裝置的實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="a3cad-132">The physical backup device corresponding to a logical backup device is initialized when the first backup in the media set is written to the logical backup device.</span></span> <span data-ttu-id="a3cad-133">如果實體備份裝置是目前尚不存在的檔案，在初始化時便會建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="a3cad-133">If the physical backup device is a file that does not exist yet, it is created at that time.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a3cad-134">相關工作</span><span class="sxs-lookup"><span data-stu-id="a3cad-134">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a3cad-135">定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-135">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-136">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-136">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-137">指定磁碟或磁帶作為備份目的地 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-137">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-138">刪除備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-138">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-139">設定備份的到期日 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-139">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-140">檢視備份磁帶或檔案的內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-140">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-141">檢視備份組中的資料和記錄檔 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-141">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-142">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-142">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="a3cad-143">從裝置還原備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-143">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3cad-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3cad-144">See Also</span></span>  
 <span data-ttu-id="a3cad-145">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a3cad-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="a3cad-146">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a3cad-146">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
