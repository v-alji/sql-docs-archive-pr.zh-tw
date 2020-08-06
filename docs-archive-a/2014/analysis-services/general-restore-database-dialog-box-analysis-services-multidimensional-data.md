---
title: 一般 (還原資料庫] 對話方塊)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25a49e17227fc2ed6b7b18d2e0964cd8812cbdcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606484"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d6dee-102">一般 (還原資料庫對話方塊) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="d6dee-102">General (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d6dee-103">在 **中，使用** [還原資料庫] **對話方塊的** [一般] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 頁面，即可指定在還原 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫時使用的備份檔案和一般設定。</span><span class="sxs-lookup"><span data-stu-id="d6dee-103">Use the **General** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the backup file and general settings to use when restoring an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d6dee-104">對於每個備份檔案，執行還原命令的使用者必須擁有從針對每個檔案所指定之備份位置讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="d6dee-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="d6dee-105">若要還原沒有安裝在伺服器上的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者也必須是該 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d6dee-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="d6dee-106">若要覆寫 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在即將還原之資料庫上擁有「完整控制 (系統管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="d6dee-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6dee-107">還原現有的資料庫之後，還原資料庫的使用者可能會喪失已還原資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="d6dee-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="d6dee-108">如果在執行備份時，使用者不是伺服器角色的成員，也不是擁有完整控制權 (管理員) 權限的資料庫角色成員，就可能會發生存取權喪失的情況。</span><span class="sxs-lookup"><span data-stu-id="d6dee-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="d6dee-109">**在還原資料庫對話方塊中顯示一般頁面**</span><span class="sxs-lookup"><span data-stu-id="d6dee-109">**To display the General page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="d6dee-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的 [資料庫]\*\*\*\* 資料夾或物件總管\*\*\*\* 中的資料庫、按一下 [還原]\*\*\*\*，然後按一下 [選取頁面]\*\*\*\* 底下的 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d6dee-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **General**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d6dee-111">選項</span><span class="sxs-lookup"><span data-stu-id="d6dee-111">Options</span></span>  
 <span data-ttu-id="d6dee-112">**指令碼**</span><span class="sxs-lookup"><span data-stu-id="d6dee-112">**Script**</span></span>  
 <span data-ttu-id="d6dee-113">根據在對話方塊中選取的選項，建立還原指令碼。</span><span class="sxs-lookup"><span data-stu-id="d6dee-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="d6dee-114">此還原指令碼是以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 指令碼語言 (ASSL) 撰寫而成。</span><span class="sxs-lookup"><span data-stu-id="d6dee-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="d6dee-115">根據預設，按一下 **[指令碼]** 圖示就會將還原指令碼傳送至新的查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="d6dee-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="d6dee-116">按一下 **[指令碼]** 箭號就會顯示功能表，讓您選擇要傳送還原指令碼的目標位置：</span><span class="sxs-lookup"><span data-stu-id="d6dee-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="d6dee-117">傳送到新的查詢視窗 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="d6dee-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="d6dee-118">傳送到檔案。</span><span class="sxs-lookup"><span data-stu-id="d6dee-118">To a file.</span></span>  
  
-   <span data-ttu-id="d6dee-119">傳送到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="d6dee-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="d6dee-120">傳送到作業。</span><span class="sxs-lookup"><span data-stu-id="d6dee-120">To a job.</span></span>  
  
 <span data-ttu-id="d6dee-121">**還原資料庫**</span><span class="sxs-lookup"><span data-stu-id="d6dee-121">**Restore database**</span></span>  
 <span data-ttu-id="d6dee-122">選取要還原的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6dee-122">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to restore.</span></span>  
  
 <span data-ttu-id="d6dee-123">**從備份檔案**</span><span class="sxs-lookup"><span data-stu-id="d6dee-123">**From backup file**</span></span>  
 <span data-ttu-id="d6dee-124">選取備份檔案，從該備份檔案中還原選取的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6dee-124">Select the backup file from which to restore the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d6dee-125">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="d6dee-125">**Browse**</span></span>  
 <span data-ttu-id="d6dee-126">按一下即可顯示 [尋找資料庫檔案]\*\*\*\* 對話方塊，並選取要使用之備份檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d6dee-126">Click to display the **Locate Database Files** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="d6dee-127">如需 [尋找資料庫檔案]\*\*\*\* 對話方塊的詳細資訊，請參閱[尋找資料庫檔案對話方塊 &#40;Analysis Services - 多維度資料&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d6dee-127">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="d6dee-128">**允許資料庫覆寫**</span><span class="sxs-lookup"><span data-stu-id="d6dee-128">**Allow database overwrite**</span></span>  
 <span data-ttu-id="d6dee-129">選取即可允許 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 還原所選取備份檔案的內容，並覆寫所選取 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中的任何現有物件。</span><span class="sxs-lookup"><span data-stu-id="d6dee-129">Select to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to restore the contents of the selected backup file over any existing objects in the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d6dee-130">**包含安全性資訊**</span><span class="sxs-lookup"><span data-stu-id="d6dee-130">**Include security information**</span></span>  
 <span data-ttu-id="d6dee-131">選取即可複製備份檔案中儲存的任何安全性資訊至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6dee-131">Select to copy any security information stored in the backup file to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d6dee-132">如果選取此選項，您就可以從選取此選項所啟用的下拉式清單中，選擇安全性資訊的數量。</span><span class="sxs-lookup"><span data-stu-id="d6dee-132">If this option is selected, you can choose the amount of security information from the drop-down list enabled by selecting this option.</span></span> <span data-ttu-id="d6dee-133">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="d6dee-133">The following options are available:</span></span>  
  
|<span data-ttu-id="d6dee-134">選項</span><span class="sxs-lookup"><span data-stu-id="d6dee-134">Option</span></span>|<span data-ttu-id="d6dee-135">描述</span><span class="sxs-lookup"><span data-stu-id="d6dee-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d6dee-136">**全部複製**</span><span class="sxs-lookup"><span data-stu-id="d6dee-136">**Copy All**</span></span>|<span data-ttu-id="d6dee-137">還原備份檔案包含的資料庫角色，以及角色相關聯的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d6dee-137">Restores the database roles contained in the backup file, as well as the user accounts associated with the roles.</span></span>|  
|<span data-ttu-id="d6dee-138">**略過成員資格**</span><span class="sxs-lookup"><span data-stu-id="d6dee-138">**Skip Membership**</span></span>|<span data-ttu-id="d6dee-139">還原備份檔案包含的資料庫角色，但不還原角色相關聯的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d6dee-139">Restores the database roles contained in the backup file, but does not restore the user accounts associated with the roles.</span></span>|  
  
 <span data-ttu-id="d6dee-140">**密碼**</span><span class="sxs-lookup"><span data-stu-id="d6dee-140">**Password**</span></span>  
 <span data-ttu-id="d6dee-141">如果備份檔案已加密，請鍵入用來加密備份檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="d6dee-141">If the backup file is encrypted, type the password used to encrypt the backup file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dee-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6dee-142">See Also</span></span>  
 <span data-ttu-id="d6dee-143">[[還原資料庫] 對話方塊 &#40;Analysis Services-多維度資料&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d6dee-143">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d6dee-144">[分割區 &#40;[還原資料庫] 對話方塊&#41; &#40;Analysis Services 多維度資料&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d6dee-144">[Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d6dee-145">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="d6dee-145">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
