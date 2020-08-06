---
title: 選取備份目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ffd1d2529dd13e42689bcf168c972d757fb5499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598452"
---
# <a name="select-backup-destination"></a><span data-ttu-id="b4625-102">選取備份目的地</span><span class="sxs-lookup"><span data-stu-id="b4625-102">Select Backup Destination</span></span>
  <span data-ttu-id="b4625-103">使用 [選取備份目的地]  對話方塊，即可選取裝置作為備份目的地。</span><span class="sxs-lookup"><span data-stu-id="b4625-103">Use the **Select Backup Destination** dialog box to select a device as your backup destination.</span></span> <span data-ttu-id="b4625-104">備份目的地可以是磁碟或是邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="b4625-104">A backup destination can be either a disk or a logical backup device.</span></span>  
  
 <span data-ttu-id="b4625-105">**若要使用 SQL Server Management Studio 備份資料庫**</span><span class="sxs-lookup"><span data-stu-id="b4625-105">**To use SQL Server Management Studio to back up a database**</span></span>  
  
-   [<span data-ttu-id="b4625-106">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4625-106">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="b4625-107">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4625-107">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="b4625-108">備份檔案和檔案群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4625-108">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="b4625-109">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4625-109">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="b4625-110">選項。</span><span class="sxs-lookup"><span data-stu-id="b4625-110">Options</span></span>  
 <span data-ttu-id="b4625-111">此對話方塊的選項，會視您選取的目的地是磁碟還是磁帶而定。</span><span class="sxs-lookup"><span data-stu-id="b4625-111">The options of this dialog box depend on whether you are selecting a destination on disk or on tape.</span></span>  
  
 <span data-ttu-id="b4625-112">**磁碟上的目的地**</span><span class="sxs-lookup"><span data-stu-id="b4625-112">**Destination on disk**</span></span>  
 <span data-ttu-id="b4625-113">若要指定備份目的地，請選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="b4625-113">To specify a backup destination, choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4625-114">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="b4625-114">**File name**</span></span>|<span data-ttu-id="b4625-115">選擇這個選項，即可在文字方塊中輸入本機或遠端檔案，做為備份目的地。</span><span class="sxs-lookup"><span data-stu-id="b4625-115">Choose this option to enter a local or remote file as the backup destination in the text box.</span></span><br /><br /> <span data-ttu-id="b4625-116">若要指定本機檔案，請按一下文字方塊右邊的 [流覽] 按鈕，並流覽至執行伺服器之電腦的固定磁片磁碟機上的檔案，或是直接輸入完整路徑和檔案名;例如， `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak` 。</span><span class="sxs-lookup"><span data-stu-id="b4625-116">To specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.</span></span><br /><br /> <span data-ttu-id="b4625-117">若要指定遠端檔案做為備份目的地，請輸入其完整的通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="b4625-117">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="b4625-118">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="b4625-118">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span><br /><br /> <span data-ttu-id="b4625-119">**\*\* 重要 \*\*** 透過網路備份資料可能會受到網路錯誤的影響，因此，建議您在備份作業完成之後要進行驗證。</span><span class="sxs-lookup"><span data-stu-id="b4625-119">**\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="b4625-120">如需詳細資訊，請參閱 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b4625-120">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>|  
|<span data-ttu-id="b4625-121">**備份裝置**</span><span class="sxs-lookup"><span data-stu-id="b4625-121">**Backup device**</span></span>|<span data-ttu-id="b4625-122">選擇這個選項，即可選取邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="b4625-122">Choose this option to select a logical backup device.</span></span><br /><br /> <span data-ttu-id="b4625-123">注意:如需如何建立磁碟備份裝置的資訊，請參閱[定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b4625-123">Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).</span></span>|  
  
 <span data-ttu-id="b4625-124">**磁帶上的目的地**</span><span class="sxs-lookup"><span data-stu-id="b4625-124">**Destination on tape**</span></span>  
 <span data-ttu-id="b4625-125">在磁帶機上指定備份目的地，此磁帶機實際連接到執行伺服器的電腦 (亦即 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="b4625-125">Specify a backup destination on a tape drive physically connected to the computer running the server (that is, the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]).</span></span> <span data-ttu-id="b4625-126">請選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="b4625-126">Choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4625-127">**磁帶機**</span><span class="sxs-lookup"><span data-stu-id="b4625-127">**Tape drive**</span></span>|<span data-ttu-id="b4625-128">選擇這個選項，即可從實際連接到執行伺服器執行個體之電腦的磁帶機清單中選取磁帶機，做為備份目的地。</span><span class="sxs-lookup"><span data-stu-id="b4625-128">Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="b4625-129">注意:遠端電腦上的磁帶備份裝置並不是有效的備份目的地。</span><span class="sxs-lookup"><span data-stu-id="b4625-129">Note: Tape backup devices on remote computers are not valid backup destinations.</span></span>|  
|<span data-ttu-id="b4625-130">**備份裝置**</span><span class="sxs-lookup"><span data-stu-id="b4625-130">**Backup device**</span></span>|<span data-ttu-id="b4625-131">選擇這個選項，即可選取現有的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="b4625-131">Choose this option to select an existing logical backup device.</span></span> <span data-ttu-id="b4625-132">這些邏輯備份裝置會對應至實際連接到執行伺服器執行個體之電腦的磁帶機。</span><span class="sxs-lookup"><span data-stu-id="b4625-132">These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="b4625-133">注意:如需如何建立磁帶備份裝置的資訊，請參閱[定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b4625-133">Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4625-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4625-134">See Also</span></span>  
 <span data-ttu-id="b4625-135">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4625-135">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="b4625-136">媒體集、媒體家族與備份組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b4625-136">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
