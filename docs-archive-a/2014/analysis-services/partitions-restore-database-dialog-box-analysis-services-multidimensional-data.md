---
title: 資料分割 ([還原資料庫] 對話方塊)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599226"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="dd7f5-102">資料分割 (還原資料庫對話方塊) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="dd7f5-102">Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="dd7f5-103">在 **中，使用** [還原資料庫] **對話方塊的** [資料分割] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 頁面，即可指定本機資料分割的還原位置和是否還原遠端資料分割，以及指定還原遠端資料分割時所使用的遠端備份檔案。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-103">Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dd7f5-104">對於每個備份檔案，執行還原命令的使用者必須擁有從針對每個檔案所指定之備份位置讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="dd7f5-105">若要還原沒有安裝在伺服器上的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者也必須是該 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="dd7f5-106">若要覆寫 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在即將還原之資料庫上擁有「完整控制 (系統管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd7f5-107">還原現有的資料庫之後，還原資料庫的使用者可能會喪失已還原資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="dd7f5-108">如果在執行備份時，使用者不是伺服器角色的成員，也不是擁有完整控制權 (管理員) 權限的資料庫角色成員，就可能會發生存取權喪失的情況。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="dd7f5-109">**若要在還原資料庫對話方塊中顯示分割區頁面**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-109">**To display the Partitions page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="dd7f5-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的 [資料庫]\*\*\*\* 資料夾或物件總管\*\*\*\* 中的資料庫，按一下 [還原]\*\*\*\*，然後按一下 [選取頁面]\*\*\*\* 底下的 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="dd7f5-111">選項</span><span class="sxs-lookup"><span data-stu-id="dd7f5-111">Options</span></span>  
 <span data-ttu-id="dd7f5-112">**指令碼**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-112">**Script**</span></span>  
 <span data-ttu-id="dd7f5-113">根據在對話方塊中選取的選項，建立還原指令碼。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="dd7f5-114">此還原指令碼是以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 撰寫而成。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="dd7f5-115">根據預設，按一下 **[指令碼]** 圖示就會將還原指令碼傳送至新的查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="dd7f5-116">按一下 **[指令碼]** 箭號就會顯示功能表，讓您選擇要傳送還原指令碼的目標位置：</span><span class="sxs-lookup"><span data-stu-id="dd7f5-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="dd7f5-117">傳送到新的查詢視窗 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="dd7f5-118">傳送到檔案。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-118">To a file.</span></span>  
  
-   <span data-ttu-id="dd7f5-119">傳送到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="dd7f5-120">傳送到作業。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-120">To a job.</span></span>  
  
 <span data-ttu-id="dd7f5-121">**還原至原始位置**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-121">**Restore to original locations**</span></span>  
 <span data-ttu-id="dd7f5-122">選取即可將備份檔案包含的本機資料分割，還原至它們的原始位置。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-122">Select to restore local partitions contained in the backup file to their original locations.</span></span>  
  
 <span data-ttu-id="dd7f5-123">**選取另外的位置**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-123">**Select different locations**</span></span>  
 <span data-ttu-id="dd7f5-124">選取即可指定不同的位置，來還原本機資料分割。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-124">Select to specify different locations in which to restore local partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd7f5-125">唯有對 Cube 中的資料分割指定預設位置以外的位置時，您才能變更本機資料分割的還原資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-125">You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.</span></span>  
  
 <span data-ttu-id="dd7f5-126">下列方格會在選取此選項之後啟用，它是用來指定每一個本機資料分割的還原資料夾：</span><span class="sxs-lookup"><span data-stu-id="dd7f5-126">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="dd7f5-127">資料行</span><span class="sxs-lookup"><span data-stu-id="dd7f5-127">Column</span></span>|<span data-ttu-id="dd7f5-128">描述</span><span class="sxs-lookup"><span data-stu-id="dd7f5-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dd7f5-129">**Cube**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-129">**Cube**</span></span>|<span data-ttu-id="dd7f5-130">顯示包含本機資料分割的 Cube 名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-130">Displays the name of the cube that contains the local partition.</span></span>|  
|<span data-ttu-id="dd7f5-131">**MeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-131">**MeasureGroup**</span></span>|<span data-ttu-id="dd7f5-132">顯示包含本機資料分割之量值群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-132">Displays the name of the measure group that contains the local partition.</span></span>|  
|<span data-ttu-id="dd7f5-133">**資料分割**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-133">**Partition**</span></span>|<span data-ttu-id="dd7f5-134">顯示本機資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-134">Displays the name of the local partition.</span></span>|  
|<span data-ttu-id="dd7f5-135">**大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-135">**Size (MB)**</span></span>|<span data-ttu-id="dd7f5-136">顯示本機資料分割的大小，以 MB 為單位。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-136">Displays the size, in megabytes, of the local partition.</span></span>|  
|<span data-ttu-id="dd7f5-137">**原始資料夾**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-137">**Original Folder**</span></span>|<span data-ttu-id="dd7f5-138">顯示儲存本機資料分割之原始資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-138">Displays the name of the original folder in which the local partition was stored.</span></span>|  
|<span data-ttu-id="dd7f5-139">**還原資料夾**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-139">**Restoration Folder**</span></span>|<span data-ttu-id="dd7f5-140">輸入本機資料分割的還原資料夾名稱，或按一下省略符號按鈕 (**...**)，以顯示 [瀏覽遠端資料夾]\*\*\*\* 對話方塊並選取要使用的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-140">Type the name of the restoration folder for the local partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="dd7f5-141">如需 [瀏覽遠端資料夾]\*\*\*\* 對話方塊的詳細資訊，請參閱[瀏覽遠端資料夾對話方塊 &#40;Analysis Services - 多維度資料&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-141">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
 <span data-ttu-id="dd7f5-142">**還原遠端資料分割**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-142">**Restore remote partitions**</span></span>  
 <span data-ttu-id="dd7f5-143">選取即可還原遠端備份檔案中儲存的遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-143">Select to restore remote partitions stored in remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd7f5-144">只有在備份檔案包含遠端資料分割的參考時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-144">This option is enabled only if the backup file contains references to remote partitions.</span></span>  
  
 <span data-ttu-id="dd7f5-145">下列方格會在選取此選項之後啟用，它是用來指定每一個本機資料分割的還原資料夾：</span><span class="sxs-lookup"><span data-stu-id="dd7f5-145">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="dd7f5-146">資料行</span><span class="sxs-lookup"><span data-stu-id="dd7f5-146">Column</span></span>|<span data-ttu-id="dd7f5-147">描述</span><span class="sxs-lookup"><span data-stu-id="dd7f5-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dd7f5-148">**Server**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-148">**Server**</span></span>|<span data-ttu-id="dd7f5-149">顯示管理遠端資料分割的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-149">Displays the name of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partition.</span></span>|  
|<span data-ttu-id="dd7f5-150">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-150">**Data Source**</span></span>|<span data-ttu-id="dd7f5-151">顯示備份檔案中的資料來源名稱，此資料來源代表包含遠端資料分割的資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-151">Displays the name of the data source in the backup file that represents the database that contains the remote partition.</span></span>|  
|<span data-ttu-id="dd7f5-152">**備份檔案**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-152">**Backup File**</span></span>|<span data-ttu-id="dd7f5-153">輸入要使用之遠端備份檔案的完整路徑和檔案名稱，或按一下省略符號按鈕 (**...**)，以顯示 [尋找資料庫檔案]\*\*\*\* 對話方塊並選取要使用之遠端備份檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="dd7f5-154">如需 [尋找資料庫檔案]\*\*\*\* 對話方塊的詳細資訊，請參閱[尋找資料庫檔案對話方塊 &#40;Analysis Services - 多維度資料&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-154">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="dd7f5-155">**...**</span><span class="sxs-lookup"><span data-stu-id="dd7f5-155">**...**</span></span>|<span data-ttu-id="dd7f5-156">按一下即可顯示 [遠端資料分割 - 進階設定]\*\*\*\* 對話方塊，並修改還原遠端資料分割的進階選項，例如資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-156">Click to display the **Remote Partitions - Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition.</span></span> <span data-ttu-id="dd7f5-157">如需 [遠端資料分割 - 進階設定]\*\*\*\* 對話方塊的詳細資訊，請參閱[遠端資料分割 - 進階設定對話方塊 &#40;Analysis Services - 多維度資料&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="dd7f5-157">For more information about the **Remote Partitions - Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd7f5-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd7f5-158">See Also</span></span>  
 <span data-ttu-id="dd7f5-159">[[還原資料庫] 對話方塊 &#40;Analysis Services-多維度資料&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dd7f5-159">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="dd7f5-160">[[一般] &#40;[還原資料庫] 對話方塊&#41; &#40;Analysis Services-多維度資料&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="dd7f5-160">[General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="dd7f5-161">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="dd7f5-161">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
