---
title: " (Analysis Services-多維度資料) 的 [還原資料庫] 對話方塊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710886"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f0d4e-102">還原資料庫對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f0d4e-102">Restore Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f0d4e-103">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [還原資料庫]\*\*\*\* 對話方塊，即可從使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 備份檔案 (.abf) 格式的備份檔案還原 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-103">Use the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database from a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f0d4e-104">對於每個備份檔案，執行還原命令的使用者必須擁有從針對每個檔案所指定之備份位置讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="f0d4e-105">若要還原沒有安裝在伺服器上的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者也必須是該 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="f0d4e-106">若要覆寫 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在即將還原之資料庫上擁有「完整控制 (系統管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0d4e-107">還原現有的資料庫之後，還原資料庫的使用者可能會喪失已還原資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="f0d4e-108">如果在執行備份時，使用者不是伺服器角色的成員，也不是擁有完整控制權 (管理員) 權限的資料庫角色成員，就可能會發生存取權喪失的情況。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="f0d4e-109">**顯示還原資料庫對話方塊**</span><span class="sxs-lookup"><span data-stu-id="f0d4e-109">**To display the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="f0d4e-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的 [資料庫]\*\*\*\* 資料夾或**物件總管**中的資料庫，然後按一下 [還原]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Restore**.</span></span>  
  
 <span data-ttu-id="f0d4e-111">**[還原資料庫]** 對話方塊包含下列頁面。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-111">The **Restore Database** dialog box contains the following pages.</span></span>  
  
## <a name="pages"></a><span data-ttu-id="f0d4e-112">頁面</span><span class="sxs-lookup"><span data-stu-id="f0d4e-112">Pages</span></span>  
 <span data-ttu-id="f0d4e-113">**一般**</span><span class="sxs-lookup"><span data-stu-id="f0d4e-113">**General**</span></span>  
 <span data-ttu-id="f0d4e-114">使用此頁面即可選取要還原的資料庫、用來還原資料庫的備份檔案，以及還原資料庫時使用的一般選項與密碼。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-114">Use this page to select the database to restore, the backup file from which to restore the database, as well as the general options and password to use while restoring the database.</span></span> <span data-ttu-id="f0d4e-115">如需此頁面的詳細資訊，請參閱[一般 &#40;還原資料庫對話方塊&#41; &#40;Analysis Services – 多維度資料&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-115">For more information about this page, see [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="f0d4e-116">**資料分割**</span><span class="sxs-lookup"><span data-stu-id="f0d4e-116">**Partitions**</span></span>  
 <span data-ttu-id="f0d4e-117">使用此頁面即可將本機資料分割還原至指定的位置，以及從遠端備份檔案還原遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-117">Use this page to restore local partitions to specified locations, and to restore remote partitions from remote backup files.</span></span> <span data-ttu-id="f0d4e-118">如需此頁面的詳細資訊，請參閱[資料分割 &#40;還原資料庫對話方塊&#41; &#40;Analysis Services – 多維度資料&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d4e-118">For more information about this page, see [Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d4e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0d4e-119">See Also</span></span>  
 <span data-ttu-id="f0d4e-120">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f0d4e-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f0d4e-121">備份與還原 Analysis Services 資料庫</span><span class="sxs-lookup"><span data-stu-id="f0d4e-121">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
