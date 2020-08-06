---
title: '[備份資料庫] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 48cf094353c53213864dae656af94ae791442105
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593160"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="aec25-102">備份資料庫對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="aec25-102">Backup Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="aec25-103">透過 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [備份資料庫]\*\*\*\* 對話方塊，即可使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 備份檔 (.abf) 格式，將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫備份至備份檔案中。</span><span class="sxs-lookup"><span data-stu-id="aec25-103">Use the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to back up an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aec25-104">對於每個備份檔案，執行備份命令的使用者必須擁有寫入針對每個檔案所指定之備份位置的權限。</span><span class="sxs-lookup"><span data-stu-id="aec25-104">For each backup file, the user who runs the backup command must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="aec25-105">此外，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在即將備份之資料庫上擁有「完整控制 (系統管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="aec25-105">Also, the user must have one of the following roles: a member of a server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
 <span data-ttu-id="aec25-106">**顯示備份資料庫對話方塊**</span><span class="sxs-lookup"><span data-stu-id="aec25-106">**To display the Backup Database dialog box**</span></span>  
  
-   <span data-ttu-id="aec25-107">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的 [資料庫]\*\*\*\* 資料夾或物件總管\*\*\*\* 中的資料庫，然後按一下 [備份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aec25-107">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Backup**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aec25-108">選項</span><span class="sxs-lookup"><span data-stu-id="aec25-108">Options</span></span>  
 <span data-ttu-id="aec25-109">**指令碼**</span><span class="sxs-lookup"><span data-stu-id="aec25-109">**Script**</span></span>  
 <span data-ttu-id="aec25-110">根據在對話方塊中選取的選項，建立備份指令碼。</span><span class="sxs-lookup"><span data-stu-id="aec25-110">Creates a backup script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="aec25-111">此還原指令碼是以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 撰寫而成。</span><span class="sxs-lookup"><span data-stu-id="aec25-111">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="aec25-112">依預設，按一下**指令碼**圖示就會將備份指令碼傳送至新的查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="aec25-112">Clicking the **Script** icon sends the backup script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="aec25-113">按一下 [指令碼]\*\*\*\* 箭號就會顯示功能表，讓您選擇要傳送備份指令碼的目標位置：</span><span class="sxs-lookup"><span data-stu-id="aec25-113">Clicking the **Script** arrow displays a menu that allows you to choose where to send the backup script:</span></span>  
  
-   <span data-ttu-id="aec25-114">傳送到新的查詢視窗 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="aec25-114">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="aec25-115">傳送到檔案。</span><span class="sxs-lookup"><span data-stu-id="aec25-115">To a file.</span></span>  
  
-   <span data-ttu-id="aec25-116">傳送到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="aec25-116">To the clipboard.</span></span>  
  
-   <span data-ttu-id="aec25-117">傳送到作業。</span><span class="sxs-lookup"><span data-stu-id="aec25-117">To a job.</span></span>  
  
 <span data-ttu-id="aec25-118">**Database**</span><span class="sxs-lookup"><span data-stu-id="aec25-118">**Database**</span></span>  
 <span data-ttu-id="aec25-119">顯示目前選取的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="aec25-119">Displays the name of the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="aec25-120">**[備份檔案]**</span><span class="sxs-lookup"><span data-stu-id="aec25-120">**Backup file**</span></span>  
 <span data-ttu-id="aec25-121">鍵入要使用的備份檔案之完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="aec25-121">Type the full path and file name of the backup file to use.</span></span>  
  
 <span data-ttu-id="aec25-122">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="aec25-122">**Browse**</span></span>  
 <span data-ttu-id="aec25-123">按一下即可顯示 [另存新檔]\*\*\*\* 對話方塊，並選取要使用的備份檔案之路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="aec25-123">Click to display the **Save File As** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="aec25-124">如需 [另存新檔]\*\*\*\* 對話方塊的詳細資訊，請參閱[另存新檔對話方塊 &#40;Analysis Services - 多維度資料&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="aec25-124">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="aec25-125">**允許檔案覆寫**</span><span class="sxs-lookup"><span data-stu-id="aec25-125">**Allow file overwrite**</span></span>  
 <span data-ttu-id="aec25-126">選取即可覆寫現有的備份檔案或遠端備份檔案 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="aec25-126">Select to overwrite an existing backup file or remote backup file, if one exists.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aec25-127">如果未選取此選項，且 [備份檔案]\*\*\*\* 中指定的備份檔案或 [遠端備份檔案]\*\*\*\* 中指定的遠端備份檔案存在的話，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="aec25-127">If this option is not selected and the backup file specified in **Backup file** or a remote backup file specified in **Remote backup file** exists, an error occurs.</span></span>  
  
 <span data-ttu-id="aec25-128">**套用壓縮**</span><span class="sxs-lookup"><span data-stu-id="aec25-128">**Apply compression**</span></span>  
 <span data-ttu-id="aec25-129">選取即可壓縮備份檔案的內容，如果指定的話，也會壓縮遠端備份檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="aec25-129">Select to compress the contents of the backup file and, if specified, remote backup files.</span></span>  
  
 <span data-ttu-id="aec25-130">**加密備份檔案**</span><span class="sxs-lookup"><span data-stu-id="aec25-130">**Encrypt backup file**</span></span>  
 <span data-ttu-id="aec25-131">選取即可使用 [密碼]\*\*\*\* 中提供的密碼，為備份檔案加密。</span><span class="sxs-lookup"><span data-stu-id="aec25-131">Select to encrypt the backup file using the password supplied in **Password**.</span></span>  
  
 <span data-ttu-id="aec25-132">**密碼**</span><span class="sxs-lookup"><span data-stu-id="aec25-132">**Password**</span></span>  
 <span data-ttu-id="aec25-133">鍵入加密備份檔案時使用的密碼，如果指定的話，也會適用於遠端備份檔案的加密。</span><span class="sxs-lookup"><span data-stu-id="aec25-133">Type the password to use when encrypting the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aec25-134">唯有選取了 [加密備份檔案]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="aec25-134">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="aec25-135">**確認密碼**</span><span class="sxs-lookup"><span data-stu-id="aec25-135">**Confirm Password**</span></span>  
 <span data-ttu-id="aec25-136">鍵入 [密碼]\*\*\*\* 中輸入的密碼，以確認備份檔案的密碼，如果指定的話，也會適用於遠端備份檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="aec25-136">Type the password entered in **Password** to confirm the password for the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aec25-137">唯有選取了 [加密備份檔案]\*\*\*\* 時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="aec25-137">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="aec25-138">**備份遠端資料分割**</span><span class="sxs-lookup"><span data-stu-id="aec25-138">**Backup remote partition(s)**</span></span>  
 <span data-ttu-id="aec25-139">選取即可在備份檔案中，包含位置資訊和遠端資料分割的資料。</span><span class="sxs-lookup"><span data-stu-id="aec25-139">Select to include location information and data for remote partitions in the backup file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aec25-140">只有目前選取的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫有使用遠端資料分割時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="aec25-140">This option is enabled only if the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database uses remote partitions.</span></span>  
  
 <span data-ttu-id="aec25-141">**遠端資料分割備份位置**</span><span class="sxs-lookup"><span data-stu-id="aec25-141">**Remote partition backup location**</span></span>  
 <span data-ttu-id="aec25-142">顯示與所選取資料庫相關聯的遠端資料分割位置，以及用來備份遠端資料分割的資料和中繼資料之遠端備份檔案。</span><span class="sxs-lookup"><span data-stu-id="aec25-142">Displays the location of remote partitions associated with the selected database, as well as the remote backup file used to back up the data and metadata for the remote partitions.</span></span> <span data-ttu-id="aec25-143">下列是可使用的資料行：</span><span class="sxs-lookup"><span data-stu-id="aec25-143">The following columns are available:</span></span>  
  
|<span data-ttu-id="aec25-144">資料行</span><span class="sxs-lookup"><span data-stu-id="aec25-144">Column</span></span>|<span data-ttu-id="aec25-145">描述</span><span class="sxs-lookup"><span data-stu-id="aec25-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="aec25-146">**Server**</span><span class="sxs-lookup"><span data-stu-id="aec25-146">**Server**</span></span>|<span data-ttu-id="aec25-147">顯示管理遠端資料分割的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="aec25-147">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partitions.</span></span>|  
|<span data-ttu-id="aec25-148">**Database**</span><span class="sxs-lookup"><span data-stu-id="aec25-148">**Database**</span></span>|<span data-ttu-id="aec25-149">顯示包含遠端資料分割的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="aec25-149">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that contains the remote partitions.</span></span>|  
|<span data-ttu-id="aec25-150">**資料分割清單**</span><span class="sxs-lookup"><span data-stu-id="aec25-150">**Partition List**</span></span>|<span data-ttu-id="aec25-151">顯示 [資料庫]\*\*\*\* 中顯示的資料庫，所包含的遠端資料分割清單。</span><span class="sxs-lookup"><span data-stu-id="aec25-151">Displays the list of remote partitions contained by the database displayed in **Database**.</span></span>|  
|<span data-ttu-id="aec25-152">**遠端備份檔案**</span><span class="sxs-lookup"><span data-stu-id="aec25-152">**Remote backup file**</span></span>|<span data-ttu-id="aec25-153">鍵入要使用的遠端備份檔案之完整路徑和檔案名稱；或按一下省略符號按鈕 (**...**) 來顯示 [另存新檔]\*\*\*\* 對話方塊，並選取要使用的遠端備份檔案之路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="aec25-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Save File As** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="aec25-154">如需 [另存新檔]\*\*\*\* 對話方塊的詳細資訊，請參閱[另存新檔對話方塊 &#40;Analysis Services - 多維度資料&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="aec25-154">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aec25-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aec25-155">See Also</span></span>  
 <span data-ttu-id="aec25-156">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="aec25-156">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="aec25-157">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="aec25-157">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
