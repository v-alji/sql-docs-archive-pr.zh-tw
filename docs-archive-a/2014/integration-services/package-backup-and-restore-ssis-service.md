---
title: " (SSIS 服務) 的套件備份和還原 |Microsoft Docs"
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4cd6f3856b69485c01e4b38d89e2f7e2ec56f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599587"
---
# <a name="package-backup-and-restore-ssis-service"></a><span data-ttu-id="e0e1b-102">封裝備份和還原 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="e0e1b-102">Package Backup and Restore (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="e0e1b-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="e0e1b-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="e0e1b-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e0e1b-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 套件可以儲存至檔案系統或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 系統資料庫 msdb。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages can be saved to the file system or msdb, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system database.</span></span> <span data-ttu-id="e0e1b-107">儲存至 msdb 的封裝可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 備份和還原功能進行備份和還原。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-107">Packages saved to msdb can be backed up and restored using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] backup and restore features.</span></span>  
  
 <span data-ttu-id="e0e1b-108">如需備份和還原 msdb 資料庫的詳細資訊，請按一下下列主題之一：</span><span class="sxs-lookup"><span data-stu-id="e0e1b-108">For more information about backing up and restoring the msdb database, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e0e1b-109">SQL Server 資料庫的備份與還原</span><span class="sxs-lookup"><span data-stu-id="e0e1b-109">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [<span data-ttu-id="e0e1b-110">系統資料庫的備份與還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e0e1b-110">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e0e1b-111">包含可用來管理封裝的 **dtutil** 命令提示公用程式 (dtutil.exec)。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-111">includes the **dtutil** command-prompt utility (dtutil.exec), which you can use to manage packages.</span></span> <span data-ttu-id="e0e1b-112">如需詳細資訊，請參閱 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-112">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e0e1b-113">組態檔</span><span class="sxs-lookup"><span data-stu-id="e0e1b-113">Configuration Files</span></span>  
 <span data-ttu-id="e0e1b-114">封存包含的所有組態檔都儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-114">Any configuration files that the packages include are stored in the file system.</span></span> <span data-ttu-id="e0e1b-115">備份 msdb 資料庫時並不會備份這些檔案；因此，作為儲存至 msdb 之封裝保護計畫的一部份，您應確保定期備份組態檔。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-115">These files are not backed up when you back up the msdb database; therefore, you should make sure that the configuration files are backed up regularly as part of your plan for securing packages saved to msdb.</span></span> <span data-ttu-id="e0e1b-116">若要在 msdb 資料庫的備份中包含組態，應考慮使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態類型而不是以檔案為基礎的組態。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-116">To include configurations in the backup of the msdb database, you should consider using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type instead of file-based configurations.</span></span>  
  
## <a name="packages-stored-in-the-file-system"></a><span data-ttu-id="e0e1b-117">儲存在檔案系統中的封裝</span><span class="sxs-lookup"><span data-stu-id="e0e1b-117">Packages Stored in the File System</span></span>  
 <span data-ttu-id="e0e1b-118">儲存至檔案系統之封裝的備份應納入備份伺服器檔案系統的計畫中。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-118">The backup of packages that are saved to the file system should be included in the plan for backing up the file system of the server.</span></span> <span data-ttu-id="e0e1b-119">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務組態檔 (預設名稱為 MsDtsSrvr.ini.xml) 會列出服務監視之伺服器上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-119">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service configuration file, which has the default name MsDtsSrvr.ini.xml, lists the folders on the server that the service monitors.</span></span> <span data-ttu-id="e0e1b-120">您應確定已備份這些資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-120">You should make sure these folders are backed up.</span></span> <span data-ttu-id="e0e1b-121">另外，封裝也可能儲存在伺服器上的其他資料夾中，您應確保在備份中包含這些資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0e1b-121">Additionally, packages may be stored in other folders on the server and you should make sure to include these folders in the backup.</span></span>  
  
  
