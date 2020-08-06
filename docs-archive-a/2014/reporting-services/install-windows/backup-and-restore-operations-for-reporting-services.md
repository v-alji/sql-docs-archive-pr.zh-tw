---
title: Reporting Services 的備份與還原作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e895733457fe0c8892294540bbe8345cb121f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598751"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a><span data-ttu-id="5cba5-102">Reporting Services 的備份與還原作業</span><span class="sxs-lookup"><span data-stu-id="5cba5-102">Backup and Restore Operations for Reporting Services</span></span>
  <span data-ttu-id="5cba5-103">此主題提供所有用於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝中資料檔案的概觀，並說明備份這些檔案的時機與方法。</span><span class="sxs-lookup"><span data-stu-id="5cba5-103">This topic provides an overview of all data files used in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation and describes when and how you should back up the files.</span></span> <span data-ttu-id="5cba5-104">復原策略中最重要的部分，就是訂定報表伺服器資料庫檔案的備份與還原計劃。</span><span class="sxs-lookup"><span data-stu-id="5cba5-104">Developing a backup and restore plan for the report server database files is the most important part of a recovery strategy.</span></span> <span data-ttu-id="5cba5-105">但是，更加完整的復原策略應該要包括加密金鑰、自訂組件或延伸模組、組態檔以及報表和模型之來源檔案的備份。</span><span class="sxs-lookup"><span data-stu-id="5cba5-105">However, a more comprehensive recovery strategy would include backups of the encryption keys, custom assemblies or extensions, configuration files, and source files for reports and models.</span></span>  
  
 <span data-ttu-id="5cba5-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="5cba5-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>  
  
 <span data-ttu-id="5cba5-107">備份和還原作業常用於移動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝的全部或一部分：</span><span class="sxs-lookup"><span data-stu-id="5cba5-107">Backup and restore operations are often used to move all or part of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation:</span></span>  
  
-   <span data-ttu-id="5cba5-108">如果僅移動報表伺服器資料庫，您可以透過備份與還原或是附加與卸離作業，將資料庫重新放置到不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="5cba5-108">If you are moving just the report server databases, you can use backup and restore or attach and detach to relocate the databases on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="5cba5-109">如需詳細資訊，請參閱 [將報表伺服器資料庫移至其他電腦 &#40;SSRS 原生模式&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="5cba5-109">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>  
  
-   <span data-ttu-id="5cba5-110">將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝移動到新的電腦上，稱為移轉。</span><span class="sxs-lookup"><span data-stu-id="5cba5-110">Moving a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new computer is called a migration.</span></span> <span data-ttu-id="5cba5-111">您移轉安裝時，會執行安裝程式以安裝新的報表伺服器執行個體，然後將執行個體資料複製到新的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5cba5-111">When you migrate an installation, you run Setup to install a new report server instance and then copy instance data to the new computer.</span></span> <span data-ttu-id="5cba5-112">如需有關移轉 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cba5-112">For more information about migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="5cba5-113">升級和移轉 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="5cba5-113">Upgrade and Migrate Reporting Services</span></span>](upgrade-and-migrate-reporting-services.md)  
  
    -   [<span data-ttu-id="5cba5-114">遷移 Reporting Services 安裝 &#40;SharePoint 模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5cba5-114">Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;</span></span>](migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [<span data-ttu-id="5cba5-115">遷移 Reporting Services 安裝 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="5cba5-115">Migrate a Reporting Services Installation &#40;Native Mode&#41;</span></span>](migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a><span data-ttu-id="5cba5-116">備份報表伺服器資料庫</span><span class="sxs-lookup"><span data-stu-id="5cba5-116">Backing Up the Report Server Databases</span></span>  
 <span data-ttu-id="5cba5-117">由於報表伺服器是無狀態伺服器，因此所有應用程式資料都會儲存在 **執行個體上執行的** reportserver **與** reportservertempdb [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5cba5-117">Because a report server is a stateless server, all application data is stored in the **reportserver** and **reportservertempdb** databases that run on a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span> <span data-ttu-id="5cba5-118">您可以使用其中一種支援的 **資料庫備份方法，備份** reportserver **與** reportservertempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-118">You can backup the **reportserver** and **reportservertempdb** databases using one of the supported methods for backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="5cba5-119">報表伺服器資料庫的特定建議事項如下：</span><span class="sxs-lookup"><span data-stu-id="5cba5-119">Recommendations that are specific to the report server databases include the following:</span></span>  
  
-   <span data-ttu-id="5cba5-120">使用完整復原模式備份 **reportserver** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-120">Use the full recovery model to backup the **reportserver** database.</span></span>  
  
-   <span data-ttu-id="5cba5-121">使用簡易復原模式備份 **reportservertempdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-121">Use the simple recovery model to backup the **reportservertempdb** database.</span></span>  
  
-   <span data-ttu-id="5cba5-122">您可以針對每個資料庫使用不同的備份排程。</span><span class="sxs-lookup"><span data-stu-id="5cba5-122">You can use different backup schedules for each database.</span></span> <span data-ttu-id="5cba5-123">備份 **reportservertempdb** 的唯一理由，是避免在發生硬體故障時必須重新建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-123">The only reason to backup the **reportservertempdb** is to avoid having to recreate it if there is a hardware failure.</span></span> <span data-ttu-id="5cba5-124">如果發生硬體故障，您不必復原 **reportservertempdb**中的資料，只需要資料表結構。</span><span class="sxs-lookup"><span data-stu-id="5cba5-124">In the event of hardware failure, it is not necessary to recover the data in **reportservertempdb**, but you do need the table structure.</span></span> <span data-ttu-id="5cba5-125">如果您遺失 **reportservertempdb**，要再度獲得資料庫的唯一方法是重新建立報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-125">If you lose **reportservertempdb**, the only way to get it back is to recreate the report server database.</span></span> <span data-ttu-id="5cba5-126">如果您重新建立 **reportservertempdb**，請務必確認此資料庫的名稱與主要報表伺服器資料庫的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="5cba5-126">If you recreate the **reportservertempdb**, it is important that it have the same name as the primary report server database.</span></span>  
  
 <span data-ttu-id="5cba5-127">如需備份和復原 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 關聯式資料庫的詳細資訊，請參閱 [SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="5cba5-127">For more information about backup and recovery of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5cba5-128">如果您的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 報表伺服器處於 SharePoint 模式，則要連接其他資料庫，包括 SharePoint 組態資料庫和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 警示資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-128">If your [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server is in SharePoint mode, there are additional databases to be concerned with, including SharePoint configuration databases and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] alerting database.</span></span> <span data-ttu-id="5cba5-129">在 SharePoint 模式下，系統會針對每個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式建立三個資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-129">In SharePoint mode, three databases are created for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="5cba5-130">**reportserver**、 **reportservertempdb**和 **dataalerting** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cba5-130">The **reportserver**, **reportservertempdb**, and **dataalerting** databases.</span></span> <span data-ttu-id="5cba5-131">如需詳細資訊，請參閱 [備份與還原 Reporting Services SharePoint 服務應用程式](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="5cba5-131">For more information see [Backup and Restore Reporting Services SharePoint Service Applications](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span></span>  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="5cba5-132">備份加密金鑰</span><span class="sxs-lookup"><span data-stu-id="5cba5-132">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="5cba5-133">當您第一次設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝時，應該要備份加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="5cba5-133">You should backup the encryption keys when you configure a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation for the first time.</span></span> <span data-ttu-id="5cba5-134">每次變更服務帳戶的身分或重新命名電腦時，您也應該同時備份加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="5cba5-134">You should also backup the keys any time you change the identity of the service accounts or rename the computer.</span></span> <span data-ttu-id="5cba5-135">如需詳細資訊，請參閱 [備份與還原 Reporting Services 加密金鑰](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="5cba5-135">For more information, see [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span> <span data-ttu-id="5cba5-136">若為 SharePoint 模式的報表伺服器，請參閱[管理 Reporting Services SharePoint 服務應用程式](../manage-a-reporting-services-sharepoint-service-application.md)的「金鑰管理」一節。</span><span class="sxs-lookup"><span data-stu-id="5cba5-136">For SharePoint mode report servers, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
## <a name="backing-up-the-configuration-files"></a><span data-ttu-id="5cba5-137">備份組態檔</span><span class="sxs-lookup"><span data-stu-id="5cba5-137">Backing Up the Configuration Files</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5cba5-138">會使用組態檔來儲存應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="5cba5-138">uses configuration files to store application settings.</span></span> <span data-ttu-id="5cba5-139">您應該在第一次設定伺服器時，以及部署任何自訂延伸模組之後，備份組態檔。</span><span class="sxs-lookup"><span data-stu-id="5cba5-139">You should backup the files when you first configure the server and after you deploy any custom extensions.</span></span> <span data-ttu-id="5cba5-140">要備份的檔案包括：</span><span class="sxs-lookup"><span data-stu-id="5cba5-140">Files to back up include:</span></span>  
  
-   <span data-ttu-id="5cba5-141">RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="5cba5-141">Rsreportserver.config</span></span>  
  
-   <span data-ttu-id="5cba5-142">Rssvrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="5cba5-142">Rssvrpolicy.config</span></span>  
  
-   <span data-ttu-id="5cba5-143">Rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="5cba5-143">Rsmgrpolicy.config</span></span>  
  
-   <span data-ttu-id="5cba5-144">Reportingservicesservice.exe.config</span><span class="sxs-lookup"><span data-stu-id="5cba5-144">Reportingservicesservice.exe.config</span></span>  
  
-   <span data-ttu-id="5cba5-145">報表伺服器和報表管理員 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式的 Web.config</span><span class="sxs-lookup"><span data-stu-id="5cba5-145">Web.config for both the Report Server and Report Manager [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications</span></span>  
  
-   <span data-ttu-id="5cba5-146">Machine.config [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cba5-146">Machine.config for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span></span>  
  
## <a name="backing-up-data-files"></a><span data-ttu-id="5cba5-147">備份資料檔案</span><span class="sxs-lookup"><span data-stu-id="5cba5-147">Backing Up Data Files</span></span>  
 <span data-ttu-id="5cba5-148">備份您在報表設計師和模型設計師中建立與維護的檔案。</span><span class="sxs-lookup"><span data-stu-id="5cba5-148">Backup the files that you create and maintain in Report Designer and Model Designer.</span></span> <span data-ttu-id="5cba5-149">這些包括報表定義 (.rdl) 檔案、報表模型 (.smdl) 檔案、共用資料來源 (.rds) 檔案、資料檢視 (.dv) 檔案、資料來源 (.ds) 檔案、報表伺服器專案 (.rptproj) 檔案，以及報表方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="5cba5-149">These include report definition (.rdl) files, report model (.smdl) files, shared data source (.rds) files, data view (.dv) files, data source (.ds) files, report server project (.rptproj) files, and report solution (.sln) files.</span></span>  
  
 <span data-ttu-id="5cba5-150">請記得備份任何為管理或部署工作所建立的指令碼檔案 (.rss)。</span><span class="sxs-lookup"><span data-stu-id="5cba5-150">Remember to backup any script files (.rss) that you created for administration or deployment tasks.</span></span>  
  
 <span data-ttu-id="5cba5-151">確認您有所使用之任何自訂延伸模組與自訂組件的備份副本。</span><span class="sxs-lookup"><span data-stu-id="5cba5-151">Verify that you have a backup copy of any custom extensions and custom assemblies you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cba5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cba5-152">See Also</span></span>  
 <span data-ttu-id="5cba5-153">[&#40;SSRS 原生模式的報表伺服器資料庫&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5cba5-153">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="5cba5-154">[Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="5cba5-154">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="5cba5-155">[&#40;SSRS&#41;的 rskeymgmt 公用程式](../tools/rskeymgmt-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5cba5-155">[rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span></span>  
 <span data-ttu-id="5cba5-156">[使用備份與還原複製資料庫](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="5cba5-156">[Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span></span>  
 <span data-ttu-id="5cba5-157">[&#40;SSRS 原生模式管理報表伺服器資料庫&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="5cba5-157">[Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="5cba5-158">設定和管理加密金鑰 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="5cba5-158">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
