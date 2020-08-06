---
title: 備份選項 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
ms.openlocfilehash: f9fc674e699a3078ebd39d50fde96d632ae20493
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585649"
---
# <a name="backup-options"></a><span data-ttu-id="f2b27-102">備份選項</span><span class="sxs-lookup"><span data-stu-id="f2b27-102">Backup Options</span></span>
  <span data-ttu-id="f2b27-103">有許多方法可以備份您的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，而且它們都需要您具備伺服器管理員和資料庫管理員許可權。</span><span class="sxs-lookup"><span data-stu-id="f2b27-103">There are many ways to back up your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and they all require that you have server administrator and database administrator permissions.</span></span> <span data-ttu-id="f2b27-104">您可以在 **中開啟** [備份] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]對話方塊，選取適當的選項組態，然後從對話方塊本身執行備份。</span><span class="sxs-lookup"><span data-stu-id="f2b27-104">You can open the **Backup** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the appropriate options configuration, and then run the backup from the dialog box itself.</span></span> <span data-ttu-id="f2b27-105">或者，您可以使用該檔案中已指定的設定來建立指令碼；然後可以儲存指令碼，並視需要來執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="f2b27-105">Or, you can create a script using the settings already specified in the file; the script can then be saved and run as frequently as required.</span></span>  
  
## <a name="backup-and-synchronize"></a><span data-ttu-id="f2b27-106">備份和同步處理</span><span class="sxs-lookup"><span data-stu-id="f2b27-106">Backup and Synchronize</span></span>  
 <span data-ttu-id="f2b27-107">如果資料庫位於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的遠端執行個體，您可以使用同步處理功能，將資料庫備份至本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="f2b27-107">If the database is located on a remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the synchronization feature to back up the database to the local instance.</span></span> <span data-ttu-id="f2b27-108">資料庫的開發建置可以此方式移到實際作業環境。</span><span class="sxs-lookup"><span data-stu-id="f2b27-108">Development builds of a database can be moved into production in this manner.</span></span> <span data-ttu-id="f2b27-109">您也可以使用傳統的檔案型備份與還原，來將開發建置移到實際作業環境，但同步處理可提供更多的功能。</span><span class="sxs-lookup"><span data-stu-id="f2b27-109">You can also use the conventional, file based, backup and restore to move the development build into production, but synchronization provides additional functionality.</span></span> <span data-ttu-id="f2b27-110">例如，在開發電腦和實際作業電腦上，您可以有不同的安全性設定；同步處理會提供維護這些設定的選項，並同步處理角色以外的所有物件。</span><span class="sxs-lookup"><span data-stu-id="f2b27-110">For example, you can have security settings which are different for the development and production computers; synchronization will provide you the option to maintain those settings and synchronize all objects other than roles.</span></span> <span data-ttu-id="f2b27-111">此外，同步處理通常會執行累加更新，來更新來源電腦和目的地電腦不同的物件。</span><span class="sxs-lookup"><span data-stu-id="f2b27-111">Also, synchronization typically does an incremental update of those objects which are different for the source and destination computers.</span></span> <span data-ttu-id="f2b27-112">使用備份/還原功能無法進行累加備份。</span><span class="sxs-lookup"><span data-stu-id="f2b27-112">This kind of incremental backup is not available using the backup/restore feature.</span></span> <span data-ttu-id="f2b27-113">如需詳細資訊，請參閱 [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="f2b27-113">For more information, see [Synchronize Analysis Services Databases](synchronize-analysis-services-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f2b27-114">Analysis Services 服務帳戶必須擁有針對每個檔案所指定之備份位置的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="f2b27-114">The Analysis Services service account must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="f2b27-115">此外，使用者必須具有下列其中一個角色： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的管理員角色，或在要備份之資料庫上擁有「完整控制權 (管理員)」權限的資料庫角色成員。</span><span class="sxs-lookup"><span data-stu-id="f2b27-115">Also, the user must have one of the following roles: administrator role on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b27-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b27-116">See Also</span></span>  
 <span data-ttu-id="f2b27-117">[[備份資料庫] 對話方塊 &#40;Analysis Services-多維度資料&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2b27-117">[Backup Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f2b27-118">[備份與還原 Analysis Services 資料庫](backup-and-restore-of-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="f2b27-118">[Backup and Restore of Analysis Services Databases](backup-and-restore-of-analysis-services-databases.md) </span></span>  
 <span data-ttu-id="f2b27-119">[Backup 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="f2b27-119">[Backup Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) </span></span>  
 [<span data-ttu-id="f2b27-120">備份、還原和同步處理資料庫 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="f2b27-120">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
