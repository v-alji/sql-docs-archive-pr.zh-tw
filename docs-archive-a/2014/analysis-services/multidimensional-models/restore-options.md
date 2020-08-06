---
title: 還原選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3fa8da816e656521fb04ae7beb1127786e04e178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710913"
---
# <a name="restore-options"></a><span data-ttu-id="a0af3-102">還原選項</span><span class="sxs-lookup"><span data-stu-id="a0af3-102">Restore Options</span></span>
  <span data-ttu-id="a0af3-103">有許多方法可以還原您的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，這些都需要您具備伺服器電腦和資料庫的系統管理員許可權 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a0af3-103">There are many ways to restore your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases, all of which require that you have administrator permissions for both the server computer and the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="a0af3-104">若要還原 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中開啟 [還原資料庫]\*\*\*\* 對話方塊，選取適當的選項組態，然後從對話方塊執行還原。</span><span class="sxs-lookup"><span data-stu-id="a0af3-104">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, you can open the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration and then run the restore from the dialog box.</span></span> <span data-ttu-id="a0af3-105">或者，您可以使用檔案中已經指定的設定來建立指令碼；然後儲存指令碼並視需要執行。</span><span class="sxs-lookup"><span data-stu-id="a0af3-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as often as needed.</span></span> <span data-ttu-id="a0af3-106">如此即可使用 XMLA 來完成還原，如下節中的描述。</span><span class="sxs-lookup"><span data-stu-id="a0af3-106">In this way, the restore is completed by using XMLA, as described in the next section.</span></span>  
  
## <a name="restoring-databases-using-xmla"></a><span data-ttu-id="a0af3-107">使用 XMLA 還原資料庫</span><span class="sxs-lookup"><span data-stu-id="a0af3-107">Restoring Databases Using XMLA</span></span>  
 <span data-ttu-id="a0af3-108">XMLA Restore 命令是依據 .abf 檔案執行還原，以自動化還原處理序的方法。</span><span class="sxs-lookup"><span data-stu-id="a0af3-108">The XMLA Restore command is a way to automate the restore process by running a restore based on an .abf file.</span></span> <span data-ttu-id="a0af3-109">Restore 命令有數個屬性可供設定，以指定安全性定義、儲存遠端資料分割的位置，以及關聯式 OLAP (ROLAP) 物件的重新放置。</span><span class="sxs-lookup"><span data-stu-id="a0af3-109">The Restore command has a number of properties that can be set to specify security definitions, where remote partitions should be stored, and the relocation of relational OLAP (ROLAP) objects.</span></span> <span data-ttu-id="a0af3-110">如需詳細資訊，請參閱 [Restore 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla)。</span><span class="sxs-lookup"><span data-stu-id="a0af3-110">For more information, see [Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a0af3-111">對於每個備份檔案，執行還原命令的使用者必須擁有從針對每個檔案所指定之備份位置讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="a0af3-111">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="a0af3-112">若要還原沒有安裝在伺服器上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，使用者也必須是該 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="a0af3-112">To restore an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="a0af3-113">若要覆寫 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之伺服器角色的成員，或在即將還原之資料庫上擁有「完整控制 (系統管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="a0af3-113">To overwrite an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0af3-114">還原現有的資料庫之後，還原資料庫的使用者可能會喪失已還原資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="a0af3-114">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="a0af3-115">如果在執行備份時，使用者不是伺服器角色的成員，也不是擁有完整控制權 (管理員) 權限的資料庫角色成員，就可能會發生存取權喪失的情況。</span><span class="sxs-lookup"><span data-stu-id="a0af3-115">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0af3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0af3-116">See Also</span></span>  
 <span data-ttu-id="a0af3-117">[[還原資料庫] 對話方塊 &#40;Analysis Services-多維度資料&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a0af3-117">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="a0af3-118">[備份與還原 Analysis Services 資料庫](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a0af3-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="a0af3-119">[Restore 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="a0af3-119">[Restore Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) </span></span>  
 [<span data-ttu-id="a0af3-120">備份、還原和同步處理資料庫 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="a0af3-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
