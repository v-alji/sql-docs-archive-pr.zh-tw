---
title: 備份資料庫 (一般頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c315c827e1c8b206b2098009510bf6468bd7d74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606932"
---
# <a name="back-up-database-general-page"></a><span data-ttu-id="70b46-102">備份資料庫 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="70b46-102">Back Up Database (General Page)</span></span>
  <span data-ttu-id="70b46-103">使用 **[備份資料庫]** 對話方塊上的 **[一般]** 頁面，檢視或修改資料庫備份作業設定。</span><span class="sxs-lookup"><span data-stu-id="70b46-103">Use the **General** page of the **Back Up Database** dialog box to view or modify settings for a database back up operation.</span></span>  
  
 <span data-ttu-id="70b46-104">如需基本備份概念的詳細資訊，請參閱[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70b46-104">For more information about basic backup concepts, see [Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70b46-105">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 指定備份工作時，您可以按下 [指令碼]  按鈕，然後選取指令碼的目的地，以產生相對應的 [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) 指令碼。</span><span class="sxs-lookup"><span data-stu-id="70b46-105">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
 <span data-ttu-id="70b46-106">**若要使用 SQL Server Management Studio 建立備份**</span><span class="sxs-lookup"><span data-stu-id="70b46-106">**To use SQL Server Management Studio to create a backup**</span></span>  
  
-   [<span data-ttu-id="70b46-107">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70b46-107">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="70b46-108">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70b46-108">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="70b46-109">您可以定義資料庫維護計畫來建立資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="70b46-109">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="70b46-110">如需詳細資訊，請參閱《 [線上叢書》中的](../maintenance-plans/maintenance-plans.md) 資料庫維護計畫 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="70b46-110">For more information, see [Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="70b46-111">**建立部分備份**</span><span class="sxs-lookup"><span data-stu-id="70b46-111">**To create a partial backup**</span></span>  
  
-   <span data-ttu-id="70b46-112">如需部分備份，您必須使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式搭配 PARTIAL 選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-112">For a partial backup, you must use the [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement with the PARTIAL option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70b46-113">選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-113">Options</span></span>  
  
### <a name="source"></a><span data-ttu-id="70b46-114">來源</span><span class="sxs-lookup"><span data-stu-id="70b46-114">Source</span></span>  
 <span data-ttu-id="70b46-115">**[來源]** 面板的選項會識別資料庫，並指定備份作業的備份類型和元件。</span><span class="sxs-lookup"><span data-stu-id="70b46-115">The options of the **Source** panel identify the database and specify the backup type and component for the back up operation.</span></span>  
  
 <span data-ttu-id="70b46-116">**Database**</span><span class="sxs-lookup"><span data-stu-id="70b46-116">**Database**</span></span>  
 <span data-ttu-id="70b46-117">選取要備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="70b46-117">Select the database to back up.</span></span>  
  
 <span data-ttu-id="70b46-118">**復原模式**</span><span class="sxs-lookup"><span data-stu-id="70b46-118">**Recovery model**</span></span>  
 <span data-ttu-id="70b46-119">檢視選取的資料庫所顯示的復原模式 (SIMPLE、FULL 或 BULK_LOGGED)。</span><span class="sxs-lookup"><span data-stu-id="70b46-119">View the recovery model (SIMPLE, FULL, or BULK_LOGGED) displayed for the selected database.</span></span>  
  
 <span data-ttu-id="70b46-120">**備份類型**</span><span class="sxs-lookup"><span data-stu-id="70b46-120">**Backup type**</span></span>  
 <span data-ttu-id="70b46-121">選取要在指定的資料庫上執行的備份類型。</span><span class="sxs-lookup"><span data-stu-id="70b46-121">Select the type of backup you want to perform on the specified database.</span></span>  
  
|<span data-ttu-id="70b46-122">備份類型</span><span class="sxs-lookup"><span data-stu-id="70b46-122">Backup type</span></span>|<span data-ttu-id="70b46-123">可使用於</span><span class="sxs-lookup"><span data-stu-id="70b46-123">Available for</span></span>|<span data-ttu-id="70b46-124">限制</span><span class="sxs-lookup"><span data-stu-id="70b46-124">Restrictions</span></span>|  
|-----------------|-------------------|------------------|  
|<span data-ttu-id="70b46-125">完整</span><span class="sxs-lookup"><span data-stu-id="70b46-125">Full</span></span>|<span data-ttu-id="70b46-126">資料庫、檔案及檔案群組</span><span class="sxs-lookup"><span data-stu-id="70b46-126">Databases, files, and filegroups</span></span>|<span data-ttu-id="70b46-127">在 **master** 資料庫上，只能使用完整備份。</span><span class="sxs-lookup"><span data-stu-id="70b46-127">On the **master** database, only full backups are possible.</span></span><br /><br /> <span data-ttu-id="70b46-128">在簡單復原模式之下，檔案和檔案群組備份只可用於唯讀檔案群組。</span><span class="sxs-lookup"><span data-stu-id="70b46-128">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="70b46-129">差異</span><span class="sxs-lookup"><span data-stu-id="70b46-129">Differential</span></span>|<span data-ttu-id="70b46-130">資料庫、檔案及檔案群組</span><span class="sxs-lookup"><span data-stu-id="70b46-130">Databases, files, and filegroups</span></span>|<span data-ttu-id="70b46-131">在簡單復原模式之下，檔案和檔案群組備份只可用於唯讀檔案群組。</span><span class="sxs-lookup"><span data-stu-id="70b46-131">Under the Simple Recovery Model, file and filegroup backups are available only for read-only filegroups.</span></span>|  
|<span data-ttu-id="70b46-132">交易記錄</span><span class="sxs-lookup"><span data-stu-id="70b46-132">Transaction Log</span></span>|<span data-ttu-id="70b46-133">交易記錄</span><span class="sxs-lookup"><span data-stu-id="70b46-133">Transaction logs</span></span>|<span data-ttu-id="70b46-134">交易記錄備份無法使用於簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="70b46-134">Transaction log backups are not available for the Simple Recovery Model.</span></span>|  
  
 <span data-ttu-id="70b46-135">**只複製備份**</span><span class="sxs-lookup"><span data-stu-id="70b46-135">**Copy Only Backup**</span></span>  
 <span data-ttu-id="70b46-136">選取此選項，即可建立只複製備份。</span><span class="sxs-lookup"><span data-stu-id="70b46-136">Select to create a copy-only backup.</span></span> <span data-ttu-id="70b46-137">「只複製備份」  是與傳統 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份順序無關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份。</span><span class="sxs-lookup"><span data-stu-id="70b46-137">A *copy-only backup* is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup that is independent of the sequence of conventional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups.</span></span> <span data-ttu-id="70b46-138">如需詳細資訊，請參閱[只複製備份 &#40;SQL Server&#41;](copy-only-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70b46-138">For more information, see [Copy-Only Backups &#40;SQL Server&#41;](copy-only-backups-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70b46-139">選取 **[差異]** 選項時，您無法建立「只複製」備份。</span><span class="sxs-lookup"><span data-stu-id="70b46-139">When the **Differential** option is selected, you cannot create a copy-only backup.</span></span>  
  
 <span data-ttu-id="70b46-140">**備份元件**</span><span class="sxs-lookup"><span data-stu-id="70b46-140">**Backup component**</span></span>  
 <span data-ttu-id="70b46-141">選取要備份的資料庫元件。</span><span class="sxs-lookup"><span data-stu-id="70b46-141">Select the database component to be backed up.</span></span> <span data-ttu-id="70b46-142">如果 **[備份類型]** 清單中已選取 **[交易記錄]** ，則不會啟動此選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-142">If **Transaction Log** is selected in the **Backup type** list, this option is not activated.</span></span>  
  
 <span data-ttu-id="70b46-143">選取下列選項按鈕之一：</span><span class="sxs-lookup"><span data-stu-id="70b46-143">Select one of the following option buttons:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70b46-144">**Database**</span><span class="sxs-lookup"><span data-stu-id="70b46-144">**Database**</span></span>|<span data-ttu-id="70b46-145">指定備份整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="70b46-145">Specifies that the entire database be backed up.</span></span>|  
|<span data-ttu-id="70b46-146">**檔案與檔案群組**</span><span class="sxs-lookup"><span data-stu-id="70b46-146">**Files and filegroups**</span></span>|<span data-ttu-id="70b46-147">指定備份指定的檔案和 (或) 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="70b46-147">Specifies that the specified files and/or filegroups be backed up.</span></span><br /><br /> <span data-ttu-id="70b46-148">選取這個選項會開啟 **[選取檔案與檔案群組]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="70b46-148">Selecting this option, opens the **Select Files and Filegroups** dialog box.</span></span> <span data-ttu-id="70b46-149">在選取了要備份的檔案群組或檔案，並按一下 **[確定]** 之後，選取項目就會出現在 **[檔案群組與檔案]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="70b46-149">After you select the filegroups or files you want to back up and click **Ok**, your selections appear in the **Filegroups and files** box.</span></span>|  
  
### <a name="destination"></a><span data-ttu-id="70b46-150">Destination</span><span class="sxs-lookup"><span data-stu-id="70b46-150">Destination</span></span>  
 <span data-ttu-id="70b46-151">**[目的地]** 面板的選項可讓您指定備份作業的備份裝置類型，並尋找現有的邏輯或實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-151">The options of the **Destination** panel allow for you to specify the type of backup device for the back up operation and find an existing logical or physical backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70b46-152">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份裝置的相關資訊，請參閱[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="70b46-152">For information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="70b46-153">**備份至**</span><span class="sxs-lookup"><span data-stu-id="70b46-153">**Back up to**</span></span>  
 <span data-ttu-id="70b46-154">選取下列要備份之媒體類型的其中之一。</span><span class="sxs-lookup"><span data-stu-id="70b46-154">Select one of the following types of media to which to back up.</span></span> <span data-ttu-id="70b46-155">您選取的目的地會出現在 **[備份至]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="70b46-155">The destinations you select appear in the **Back up to** list.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70b46-156">**磁碟**</span><span class="sxs-lookup"><span data-stu-id="70b46-156">**Disk**</span></span>|<span data-ttu-id="70b46-157">備份至磁碟。</span><span class="sxs-lookup"><span data-stu-id="70b46-157">Backs up to disk.</span></span> <span data-ttu-id="70b46-158">這可能是針對資料庫所建立的系統檔案，或以磁碟為基礎的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-158">This may be a system file or a disk-based logical backup device created for the database.</span></span> <span data-ttu-id="70b46-159">目前選取的磁碟會出現在 **[備份至]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="70b46-159">The currently selected disks appear in the **Back up to** list.</span></span> <span data-ttu-id="70b46-160">您最多可以為備份作業選取 64 個磁碟裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-160">You can select up to 64 disk devices for your backup operation.</span></span>|  
|<span data-ttu-id="70b46-161">**磁帶**</span><span class="sxs-lookup"><span data-stu-id="70b46-161">**Tape**</span></span>|<span data-ttu-id="70b46-162">備份至磁帶。</span><span class="sxs-lookup"><span data-stu-id="70b46-162">Backs up to tape.</span></span> <span data-ttu-id="70b46-163">這可能是針對資料庫所建立的本機磁帶機，或以磁帶為基礎的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-163">This may be a local tape drive or a tape-based logical backup device created for the database.</span></span> <span data-ttu-id="70b46-164">目前選取的磁帶會出現在 **[備份至]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="70b46-164">The currently selected tapes appear in the **Back up to** list.</span></span> <span data-ttu-id="70b46-165">最大數目是 64。</span><span class="sxs-lookup"><span data-stu-id="70b46-165">The maximum number is 64.</span></span> <span data-ttu-id="70b46-166">如果伺服器上沒有附加磁帶裝置，則會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-166">If there are no tape devices attached to the server, this option is deactivated.</span></span> <span data-ttu-id="70b46-167">您選取的磁帶會列在 **[備份至]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="70b46-167">The tapes you select are listed in the **Back up to** list.</span></span><br /><br /> <span data-ttu-id="70b46-168">注意:未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中將會移除磁帶備份裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="70b46-168">Note: Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="70b46-169">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="70b46-169">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>|  
|<span data-ttu-id="70b46-170">**URL**</span><span class="sxs-lookup"><span data-stu-id="70b46-170">**URL**</span></span>|<span data-ttu-id="70b46-171">備份至 Azure Blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="70b46-171">Backs up to Azure Blob storage.</span></span>|  
  
 <span data-ttu-id="70b46-172">所顯示的下一組選項取決於選取的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="70b46-172">The next set of options displayed depends on the type of destination selected.</span></span> <span data-ttu-id="70b46-173">如果選取 [磁碟] 或 [磁帶]，則會顯示下列選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-173">If you select Disk or Tape, the following options are displayed.</span></span>  
  
 <span data-ttu-id="70b46-174">**加入**</span><span class="sxs-lookup"><span data-stu-id="70b46-174">**Add**</span></span>  
 <span data-ttu-id="70b46-175">將檔案或裝置加入至 **[備份至]** 清單。</span><span class="sxs-lookup"><span data-stu-id="70b46-175">Adds a file or device to the **Back up to** list.</span></span> <span data-ttu-id="70b46-176">您在本機磁碟或遠端磁碟上，最多可以同時備份到 64 個裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-176">You can back up to 64 devices simultaneously on a local disk or remote disk.</span></span> <span data-ttu-id="70b46-177">若要指定遠端磁碟上的檔案，請使用完整的通用命名慣例 (UNC) 名稱。</span><span class="sxs-lookup"><span data-stu-id="70b46-177">To specify a file on a remote disk, use the fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="70b46-178">如需詳細資訊，請參閱 [備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md)執行個體上建立資料庫備份，就需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="70b46-178">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
 <span data-ttu-id="70b46-179">**移除**</span><span class="sxs-lookup"><span data-stu-id="70b46-179">**Remove**</span></span>  
 <span data-ttu-id="70b46-180">從 **[備份至]** 清單中，移除一個或多個目前選取的裝置。</span><span class="sxs-lookup"><span data-stu-id="70b46-180">Removes one or more currently selected devices from the **Back up to** list.</span></span>  
  
 <span data-ttu-id="70b46-181">**Contents**</span><span class="sxs-lookup"><span data-stu-id="70b46-181">**Contents**</span></span>  
 <span data-ttu-id="70b46-182">顯示選取之裝置的媒體內容。</span><span class="sxs-lookup"><span data-stu-id="70b46-182">Displays the media contents for the selected device.</span></span>  
  
 <span data-ttu-id="70b46-183">如果選取 URL 做為備份目的地，則會顯示下列選項：</span><span class="sxs-lookup"><span data-stu-id="70b46-183">If you select URL as the backup destination, the following options are displayed:</span></span>  
  
 <span data-ttu-id="70b46-184">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="70b46-184">**File Name**</span></span>  
 <span data-ttu-id="70b46-185">指定備份檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="70b46-185">Specify the name of the backup file.</span></span>  
  
 <span data-ttu-id="70b46-186">**SQL 認證**</span><span class="sxs-lookup"><span data-stu-id="70b46-186">**SQL credential**</span></span>  
 <span data-ttu-id="70b46-187">選取用來驗證 Azure 儲存體的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="70b46-187">Select a SQL Credential used to authenticate to  Azure Storage.</span></span> <span data-ttu-id="70b46-188">如果沒有現有可用的 SQL 認證，請按一下 **[建立]** 按鈕建立新的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="70b46-188">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="70b46-189">在您按一下 **[建立]** 時開啟的對話方塊需要管理憑證或訂閱的發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="70b46-189">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="70b46-190">如果您無法存取管理憑證或發行設定檔，可以使用 Transact-SQL 或 SQL Server Management Studio 來指定儲存體帳戶名稱和存取金鑰資訊，藉以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="70b46-190">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="70b46-191">請參閱中的範例程式碼，[以建立認證](../security/authentication-access/create-a-credential.md#Credential)主題，以使用 transact-sql 來建立認證。</span><span class="sxs-lookup"><span data-stu-id="70b46-191">See the sample code in the in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="70b46-192">或者，使用 SQL Server Management Studio，在資料庫引擎執行個體中，以滑鼠右鍵按一下 **[安全性]**、選取 **[新增]**，然後選取 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="70b46-192">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="70b46-193">針對 **[識別]** 指定儲存體帳戶名稱，並且在 **[密碼]** 欄位中指定存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="70b46-193">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
 <span data-ttu-id="70b46-194">**Azure 儲存體容器**</span><span class="sxs-lookup"><span data-stu-id="70b46-194">**Azure storage container**</span></span>  
 <span data-ttu-id="70b46-195">指定 Azure 儲存體容器的名稱</span><span class="sxs-lookup"><span data-stu-id="70b46-195">Specify the name of the Azure storage container</span></span>  
  
 <span data-ttu-id="70b46-196">**URL 前置詞：**</span><span class="sxs-lookup"><span data-stu-id="70b46-196">**URL prefix:**</span></span>  
 <span data-ttu-id="70b46-197">這會根據儲存在 SQL 認證中的儲存體帳戶資訊，以及您指定的 Azure 儲存體容器名稱自動產生。</span><span class="sxs-lookup"><span data-stu-id="70b46-197">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="70b46-198">建議您除非使用的網域採用 **\<storage account>.blob.core.windows.net** 以外的格式，否則請勿編輯此欄位中的資訊。</span><span class="sxs-lookup"><span data-stu-id="70b46-198">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b46-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b46-199">See Also</span></span>  
 <span data-ttu-id="70b46-200">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70b46-200">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="70b46-201">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70b46-201">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="70b46-202">[定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70b46-202">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="70b46-203">[定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="70b46-203">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="70b46-204">復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="70b46-204">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
