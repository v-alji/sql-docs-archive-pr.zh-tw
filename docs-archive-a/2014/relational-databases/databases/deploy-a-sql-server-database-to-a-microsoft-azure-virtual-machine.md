---
title: 將 SQL Server Database 部署到 Microsoft Azure 虛擬機器 | Microsoft 件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: d48c06db038a775811cba6705fbaf1d97a960f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705166"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a><span data-ttu-id="459f2-102">將 SQL Server Database 部署到 Microsoft Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="459f2-102">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>
  <span data-ttu-id="459f2-103">使用 [將**SQL Server 資料庫部署到 AZURE VM** ] wizard，將實例中的資料庫部署 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE 虛擬機器 (VM) 中的。</span><span class="sxs-lookup"><span data-stu-id="459f2-103">Use the **Deploy a SQL Server Database to an Azure VM** wizard to deploy a database from an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an Azure Virtual Machine (VM).</span></span> <span data-ttu-id="459f2-104">此精靈會利用完整的資料庫備份作業，因此它一定會從 SQL Server 使用者資料庫複製完整的資料庫結構描述和資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-104">The wizard utilizes a full database backup operation, so it always copies the complete database schema and the data from a SQL Server user database.</span></span> <span data-ttu-id="459f2-105">此精靈也會為您執行所有的 Azure VM 組態設定，因此不需要進行 VM 的預先組態設定。</span><span class="sxs-lookup"><span data-stu-id="459f2-105">The wizard also does all of the Azure VM configuration for you, so no pre-configuration of the VM is required.</span></span>  
  
 <span data-ttu-id="459f2-106">您不能針對差異備份使用此精靈，因為此精靈將不會覆寫資料庫名稱相同的現有資料庫。</span><span class="sxs-lookup"><span data-stu-id="459f2-106">You cannot use the wizard for differential backups because the wizard will not overwrite an existing database that has the same database name.</span></span> <span data-ttu-id="459f2-107">若要取代 VM 上現有的資料庫，您必須先卸除現有資料庫或變更資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-107">To replace an existing database on the VM, you must first drop the existing database or change the database name.</span></span> <span data-ttu-id="459f2-108">如果進行中部署作業的資料庫名稱與 VM 上的現有資料庫發生名稱衝突，此精靈將會建議針對進行中的資料庫附加資料庫名稱，好讓您完成作業。</span><span class="sxs-lookup"><span data-stu-id="459f2-108">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> <span data-ttu-id="459f2-109">開始之前</span><span class="sxs-lookup"><span data-stu-id="459f2-109">Before You Begin</span></span>  
 <span data-ttu-id="459f2-110">若要完成這個精靈，您必須提供下列資訊並且完成以下組態設定：</span><span class="sxs-lookup"><span data-stu-id="459f2-110">To complete this wizard, you must be able to provide the following information and have these configuration settings in place:</span></span>  
  
-   <span data-ttu-id="459f2-111">與您的 Azure 訂用帳戶相關聯的 Microsoft 帳戶詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-111">The Microsoft account details associated with your Azure subscription.</span></span>  
  
-   <span data-ttu-id="459f2-112">您的 Azure 發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="459f2-112">Your Azure publishing profile.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="459f2-113">SQL Server 目前支援發行設定檔 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="459f2-113">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="459f2-114">若要下載發行設定檔的支援版本，請參閱＜ [下載發行設定檔 2.0](https://go.microsoft.com/fwlink/?LinkId=396421)＞。</span><span class="sxs-lookup"><span data-stu-id="459f2-114">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
-   <span data-ttu-id="459f2-115">已上傳至您的 Azure 訂用帳戶的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="459f2-115">The management certificate uploaded to your Azure subscription.</span></span>  
  
-   <span data-ttu-id="459f2-116">儲存到精靈執行所在電腦上個人憑證存放區中的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="459f2-116">The management certificate saved into the personal certificate store on the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="459f2-117">您必須有暫時儲存位置，以供裝載 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的電腦使用。</span><span class="sxs-lookup"><span data-stu-id="459f2-117">You must have a temporary storage location that is available to the computer where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is hosted.</span></span> <span data-ttu-id="459f2-118">此暫時儲存位置也必須提供給執行此精靈的電腦使用。</span><span class="sxs-lookup"><span data-stu-id="459f2-118">The temporary storage location must also be available to the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="459f2-119">如果您將資料庫部署到現有 VM，則必須設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體來接聽 TCP/IP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="459f2-119">If you are deploying the database to an existing VM, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured to listen on a TCP/IP port.</span></span>  
  
-   <span data-ttu-id="459f2-120">您規劃用來建立 VM 的 Azure VM 或資源庫映射必須設定 SQL Server 雲端配接器，且正在執行。</span><span class="sxs-lookup"><span data-stu-id="459f2-120">Either an Azure VM or Gallery image you plan to use for creation of the VM must have the SQL Server Cloud Adapter configured and running.</span></span>  
  
-   <span data-ttu-id="459f2-121">您必須在具有私人埠11435的 Azure 閘道上，為您的 SQL Server 雲端配接器設定開放端點。</span><span class="sxs-lookup"><span data-stu-id="459f2-121">You must configure an open endpoint for your SQL Server Cloud Adapter on the Azure gateway with private port 11435.</span></span>  
  
 <span data-ttu-id="459f2-122">此外，如果您打算將資料庫部署到現有的 Azure VM，您也必須能夠提供：</span><span class="sxs-lookup"><span data-stu-id="459f2-122">In addition, if you plan to deploy your database into an existing Azure VM, you must also be able to provide:</span></span>  
  
-   <span data-ttu-id="459f2-123">裝載 VM 之雲端服務的 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-123">The DNS name of the cloud service that hosts your VM.</span></span>  
  
-   <span data-ttu-id="459f2-124">VM 的系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="459f2-124">Administrator credentials for the VM.</span></span>  
  
-   <span data-ttu-id="459f2-125">來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的來源執行個體，具有您打算部署之資料庫的備份操作員權限的認證。</span><span class="sxs-lookup"><span data-stu-id="459f2-125">Credentials with Backup operator privileges on the database you plan to deploy, from the source instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="459f2-126">如需在 Azure 虛擬機器中執行 SQL Server 的詳細資訊，請參閱[準備在 azure 虛擬機器中遷移至 SQL Server](https://msdn.microsoft.com/library/dn133142.aspx)。</span><span class="sxs-lookup"><span data-stu-id="459f2-126">For more information about running SQL Server in Azure virtual machines, see [Getting Ready to Migrate to SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx).</span></span>  
  
 <span data-ttu-id="459f2-127">您在執行 Windows Server 作業系統的電腦上，必須使用下列組態設定執行此精靈：</span><span class="sxs-lookup"><span data-stu-id="459f2-127">On computers running Windows Server operating systems, you must use the following configuration settings to run this wizard:</span></span>  
  
-   <span data-ttu-id="459f2-128">關閉增強式安全性設定：使用 [伺服器管理員] > [本機伺服器]，將 Internet Explorer 增強式安全性設定 (ESC) 設為 [關閉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="459f2-128">Turn off Enhanced Security Configuration:  Use Server Manager > Local Server to set Internet Explorer Enhanced Security Configuration (ESC) to **OFF**.</span></span>  
  
-   <span data-ttu-id="459f2-129">啟用 JavaScript：[Internet Explorer] > [網際網路選項] > [安全性] > [自訂等級] > [指令碼處理] > [動態指令碼處理]：[啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="459f2-129">Enable JavaScript:  Internet Explorer > Internet Options > Security > Customer Level > Scripting > Active Scripting: **Enable**.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> <span data-ttu-id="459f2-130">限制事項</span><span class="sxs-lookup"><span data-stu-id="459f2-130">Limitations and Restrictions</span></span>  
 <span data-ttu-id="459f2-131">此作業的資料庫大小限制為 1 TB。</span><span class="sxs-lookup"><span data-stu-id="459f2-131">The database size limitation for this operation is 1 TB.</span></span>  
  
 <span data-ttu-id="459f2-132">適用於 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]的 SQL Server Management Studio 中提供此部署功能。</span><span class="sxs-lookup"><span data-stu-id="459f2-132">This deployment feature is available in SQL Server Management Studio for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="459f2-133">這個部署功能只能搭配使用者資料庫使用，不支援部署系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="459f2-133">This deployment feature is for use only with user databases; deploying system databases is not supported.</span></span>  
  
 <span data-ttu-id="459f2-134">此部署功能不支援與相似性群組相關聯的託管服務。</span><span class="sxs-lookup"><span data-stu-id="459f2-134">The deployment feature does not support hosted services that are associated with an Affinity Group.</span></span> <span data-ttu-id="459f2-135">例如，不能選取與相似性群組相關聯的儲存體帳戶用於此精靈的 [部署設定] \*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="459f2-135">For example, storage accounts associated with an Affinity Group cannot be selected for use on the **Deployment Settings** page of this wizard.</span></span>  
  
 <span data-ttu-id="459f2-136">在 VM 中的 SQL Server 版本必須是與來源 SQL Server 版本相同或更新的版本。</span><span class="sxs-lookup"><span data-stu-id="459f2-136">The SQL Server version in the VM must be the same or later than the source SQL Server version.</span></span> <span data-ttu-id="459f2-137">SQL Server 可以使用此 wizard 部署至 Azure VM 的資料庫版本：</span><span class="sxs-lookup"><span data-stu-id="459f2-137">SQL Server database versions that can be deployed to an Azure VM using this wizard:</span></span>  
  
-   <span data-ttu-id="459f2-138">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="459f2-138">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="459f2-139">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="459f2-139">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="459f2-140">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="459f2-140">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="459f2-141">在 Azure VM 資料庫中執行 SQL Server 資料庫版本可以部署至：</span><span class="sxs-lookup"><span data-stu-id="459f2-141">SQL Server database versions running in an Azure VM database can be deployed to:</span></span>  
  
-   <span data-ttu-id="459f2-142">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="459f2-142">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="459f2-143">如果進行中部署作業的資料庫名稱與 VM 上的現有資料庫發生名稱衝突，此精靈將會建議針對進行中的資料庫附加資料庫名稱，好讓您完成作業。</span><span class="sxs-lookup"><span data-stu-id="459f2-143">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> <span data-ttu-id="459f2-144">將啟用 FILESTREAM 的資料庫部署至 Azure VM 的考量</span><span class="sxs-lookup"><span data-stu-id="459f2-144">Considerations for Deploying a FILESTREAM-enabled Database to an Azure VM</span></span>  
 <span data-ttu-id="459f2-145">所部署資料庫的 FILESTREAM 物件中有儲存的 BLOBS 時，請注意下列指導方針和限制：</span><span class="sxs-lookup"><span data-stu-id="459f2-145">Note the following guidelines and restrictions when deploying databases that have BLOBS stored in FILESTREAM objects:</span></span>  
  
-   <span data-ttu-id="459f2-146">部署功能無法將啟用 FILESTREAM 的資料庫部署至新的 VM。</span><span class="sxs-lookup"><span data-stu-id="459f2-146">The deployment feature cannot deploy a FILESTREAM-enabled database into a new VM.</span></span> <span data-ttu-id="459f2-147">如果在您執行精靈之前，FILESTREAM 未在 VM 中啟用，則資料庫還原作業將會失敗，而且精靈作業將無法順利完成。</span><span class="sxs-lookup"><span data-stu-id="459f2-147">If FILESTREAM is not enabled in the VM before you run the wizard, the database restore operation will fail and the wizard operation will not be able to complete successfully.</span></span> <span data-ttu-id="459f2-148">若要成功部署使用 FILESTREAM 的資料庫，請在啟動精靈之前，於主 VM 上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="459f2-148">To successfully deploy a database that uses FILESTREAM, enable FILESTREAM in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the host VM before launching the wizard.</span></span> <span data-ttu-id="459f2-149">如需詳細資訊，請參閱 [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx)。</span><span class="sxs-lookup"><span data-stu-id="459f2-149">For more information, see [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).</span></span>  
  
-   <span data-ttu-id="459f2-150">如果您的資料庫使用記憶體中 OLTP，則不需對資料庫進行任何修改，就可將資料庫部署到 Azure VM。</span><span class="sxs-lookup"><span data-stu-id="459f2-150">If your database utilizes In-Memory OLTP, you can deploy the database to an Azure VM without any modifications to the database.</span></span> <span data-ttu-id="459f2-151">如需詳細資訊，請參閱 [In-Memory OLTP (記憶體中最佳化)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="459f2-151">For more information, see [In-Memory OLTP (In-Memory Optimization)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).</span></span>  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a><span data-ttu-id="459f2-152">資產地理分佈的考慮</span><span class="sxs-lookup"><span data-stu-id="459f2-152">Considerations for Geographic Distribution of Assets</span></span>  
 <span data-ttu-id="459f2-153">請注意，下列資產必須位於同一個地理區域：</span><span class="sxs-lookup"><span data-stu-id="459f2-153">Note that the following assets must be located in the same geographic region:</span></span>  
  
-   <span data-ttu-id="459f2-154">服務雲端</span><span class="sxs-lookup"><span data-stu-id="459f2-154">Cloud Service</span></span>  
  
-   <span data-ttu-id="459f2-155">VM 位置</span><span class="sxs-lookup"><span data-stu-id="459f2-155">VM Location</span></span>  
  
-   <span data-ttu-id="459f2-156">資料磁碟儲存體服務</span><span class="sxs-lookup"><span data-stu-id="459f2-156">Data Disk Storage Service</span></span>  
  
 <span data-ttu-id="459f2-157">如果上列資產並非位於相同位置，則精靈將無法順利完成。</span><span class="sxs-lookup"><span data-stu-id="459f2-157">If the assets listed above are not co-located, the wizard will not be able to complete successfully.</span></span>  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a> <span data-ttu-id="459f2-158">精靈組態設定</span><span class="sxs-lookup"><span data-stu-id="459f2-158">Wizard Configuration Settings</span></span>  
 <span data-ttu-id="459f2-159">使用下列組態詳細資料修改設定，讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫部署至 Azure VM。</span><span class="sxs-lookup"><span data-stu-id="459f2-159">Use the following configuration details to modify settings for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database deployment to an Azure VM.</span></span>  
  
-   <span data-ttu-id="459f2-160">**組態檔的預設路徑** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span><span class="sxs-lookup"><span data-stu-id="459f2-160">**Default path for the configuration file** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span></span>  
  
-   <span data-ttu-id="459f2-161">**組態檔結構**</span><span class="sxs-lookup"><span data-stu-id="459f2-161">**Configuration file structure**</span></span>  
  
    -   \<DeploymentSettings>  
  
        -   <span data-ttu-id="459f2-162"><OtherSettings</span><span class="sxs-lookup"><span data-stu-id="459f2-162"><OtherSettings</span></span>  
  
            -   <span data-ttu-id="459f2-163">TraceLevel = "Debug"\<!-- Logging level --></span><span class="sxs-lookup"><span data-stu-id="459f2-163">TraceLevel="Debug" \<!-- Logging level --></span></span>  
  
            -   <span data-ttu-id="459f2-164">BackupPath = " \\ \\ [伺服器名稱] \\ [磁片區] \\ "\<!-- The last used path for backup. Used as default in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="459f2-164">BackupPath="\\\\[server name]\\[volume]\\" \<!-- The last used path for backup. Used as default in the wizard. --></span></span>  
  
            -   <span data-ttu-id="459f2-165">CleanupDisabled = False/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span><span class="sxs-lookup"><span data-stu-id="459f2-165">CleanupDisabled = False /> \<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span></span>  
  
        -   <span data-ttu-id="459f2-166"><PublishProfile\<!-- The last used publish profile information. --></span><span class="sxs-lookup"><span data-stu-id="459f2-166"><PublishProfile \<!-- The last used publish profile information. --></span></span>  
  
            -   <span data-ttu-id="459f2-167">Certificate = "12A34B567890123ABCD4EF567A8"\<!-- The certificate for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="459f2-167">Certificate="12A34B567890123ABCD4EF567A8" \<!-- The certificate for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="459f2-168">訂用帳戶 = "1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx-67d8-90ef-ab12-1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="459f2-168">Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- The subscription for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="459f2-169">名稱 = "我的訂用帳戶"\<!-- The name of the subscription. --></span><span class="sxs-lookup"><span data-stu-id="459f2-169">Name="My Subscription" \<!-- The name of the subscription. --></span></span>  
  
            -   <span data-ttu-id="459f2-170">Publisher="" /></span><span class="sxs-lookup"><span data-stu-id="459f2-170">Publisher="" /></span></span>  
  
    -   \</DeploymentSettings>  
  
 <span data-ttu-id="459f2-171">**組態檔值**</span><span class="sxs-lookup"><span data-stu-id="459f2-171">**Configuration file values**</span></span>  
  
###  <a name="permissions"></a><a name="permissions"></a> <span data-ttu-id="459f2-172">權限</span><span class="sxs-lookup"><span data-stu-id="459f2-172">Permissions</span></span>  
 <span data-ttu-id="459f2-173">部署的資料庫必須處於正常狀態、資料庫必須可供執行此精靈的使用者帳戶存取，而且使用者帳戶必須擁有執行備份作業的權限。</span><span class="sxs-lookup"><span data-stu-id="459f2-173">The database being deployed must be in a normal state, the database must be accessible to the user account running the wizard, and the user account must have permissions to perform a backup operation.</span></span>  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a><span data-ttu-id="459f2-174">使用將資料庫部署至 Azure VM Wizard</span><span class="sxs-lookup"><span data-stu-id="459f2-174">Using the Deploy Database to Azure VM Wizard</span></span>  
 <span data-ttu-id="459f2-175">**若要啟動此精靈，請使用下列步驟：**</span><span class="sxs-lookup"><span data-stu-id="459f2-175">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="459f2-176">使用 SQL Server Management Studio 連接到具有您想要部署之資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="459f2-176">Use SQL Server Management Studio to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the database you want to deploy.</span></span>  
  
2.  <span data-ttu-id="459f2-177">在 **[物件總管]** 中，展開執行個體名稱，然後展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="459f2-177">In **Object Explorer**, expand the instance name, then expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="459f2-178">以滑鼠右鍵按一下您想要部署的資料庫，**選取 [** 工作]，然後選取 [**將資料庫部署到 Azure VM** ]。</span><span class="sxs-lookup"><span data-stu-id="459f2-178">Right-click the database you want to deploy, select **Tasks**, and then select **Deploy Database to Azure VM...**</span></span>  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="459f2-179">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="459f2-179">Introduction Page</span></span>  
 <span data-ttu-id="459f2-180">此頁面說明**如何將 SQL Server 資料庫部署至 AZURE VM**的 wizard。</span><span class="sxs-lookup"><span data-stu-id="459f2-180">This page describes the **Deploy a SQL Server Database to an Azure VM** wizard.</span></span>  
  
 <span data-ttu-id="459f2-181">**選項**</span><span class="sxs-lookup"><span data-stu-id="459f2-181">**Options**</span></span>  
  
-   <span data-ttu-id="459f2-182">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="459f2-182">**Do not show this page again.**</span></span> <span data-ttu-id="459f2-183">- 按一下此核取方塊可不再顯示 [簡介] 頁面。</span><span class="sxs-lookup"><span data-stu-id="459f2-183">- Click this check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="459f2-184">**下一步** - 繼續進行 **[來源設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="459f2-184">**Next** - Proceeds to the **Source Settings** page.</span></span>  
  
-   <span data-ttu-id="459f2-185">**取消**-取消作業並關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="459f2-185">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
-   <span data-ttu-id="459f2-186">說明 **-啟動**嚮導的 MSDN 說明主題。</span><span class="sxs-lookup"><span data-stu-id="459f2-186">**Help** - Launches the MSDN Help topic for the wizard.</span></span>  
  
##  <a name="source-settings"></a><a name="Source_settings"></a><span data-ttu-id="459f2-187">來源設定</span><span class="sxs-lookup"><span data-stu-id="459f2-187">Source Settings</span></span>  
 <span data-ttu-id="459f2-188">使用此頁面來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 裝載您想要部署至 AZURE VM 之資料庫的實例。</span><span class="sxs-lookup"><span data-stu-id="459f2-188">Use this page to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database you want to deploy to the Azure VM.</span></span> <span data-ttu-id="459f2-189">您也會指定暫存位置，以便從本機電腦儲存檔案，然後再將它們傳輸至 Azure。</span><span class="sxs-lookup"><span data-stu-id="459f2-189">You will also specify a temporary location for files to be saved from the local machine before they are transferred to Azure.</span></span> <span data-ttu-id="459f2-190">這個位置可以是共用的網路位置。</span><span class="sxs-lookup"><span data-stu-id="459f2-190">This can be a shared, network location.</span></span>  
  
 <span data-ttu-id="459f2-191">**選項**</span><span class="sxs-lookup"><span data-stu-id="459f2-191">**Options**</span></span>  
  
-   <span data-ttu-id="459f2-192">按一下 [**連接 ...]** ，然後針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 裝載要部署之資料庫的實例指定連接詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-192">Click **Connect...** and then specify connection details for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database to deploy.</span></span>  
  
-   <span data-ttu-id="459f2-193">使用 **[選取資料庫]** 下拉式清單來指定要部署的資料庫。</span><span class="sxs-lookup"><span data-stu-id="459f2-193">Use the **Select Database** drop-down list to specify the database to deploy.</span></span>  
  
-   <span data-ttu-id="459f2-194">在 [**其他設定**] 欄位中，指定可供 Azure VM 服務存取的共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="459f2-194">In the **Other Settings** field, specify a shared folder that will be accessible to the Azure VM service.</span></span>  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a><span data-ttu-id="459f2-195">Azure 登入</span><span class="sxs-lookup"><span data-stu-id="459f2-195">Azure Sign-in</span></span>  
 <span data-ttu-id="459f2-196">使用此頁面來連線到 Azure，並提供管理憑證或發行設定檔詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-196">Use this page to connect to Azure and provide management certificate or publishing profile details.</span></span>  
  
 <span data-ttu-id="459f2-197">**選項**</span><span class="sxs-lookup"><span data-stu-id="459f2-197">**Options**</span></span>  
  
-   <span data-ttu-id="459f2-198">**管理憑證**-使用此選項可指定本機憑證存放區中的憑證，以符合來自 Azure 的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="459f2-198">**Management Certificate** - Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span>  
  
-   <span data-ttu-id="459f2-199">**發行設定檔**-如果您已將發行設定檔下載至電腦，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="459f2-199">**Publishing Profile** - Use this option if you already have a publishing profile downloaded to your computer.</span></span>  
  
-   <span data-ttu-id="459f2-200">登**入**-使用此選項可使用 Microsoft 帳戶（例如 Live ID 或 Hotmail 帳戶）來登入 Azure，以產生並下載新的管理憑證。</span><span class="sxs-lookup"><span data-stu-id="459f2-200">**Sign In** - Use this option to sign in to Azure using a Microsoft account - for example, a Live ID or Hotmail account - to generate and download a new management certificate.</span></span> <span data-ttu-id="459f2-201">請注意，每個訂用帳戶的憑證數目有限。</span><span class="sxs-lookup"><span data-stu-id="459f2-201">Note that the number of certificates per subscription is limited.</span></span>  
  
-   <span data-ttu-id="459f2-202">**訂**用帳戶-選取、輸入或貼上符合本機憑證存放區或發行設定檔之管理憑證的 Azure 訂用帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="459f2-202">**Subscription** - Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store or a publishing profile.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="459f2-203">[部署設定] 頁面</span><span class="sxs-lookup"><span data-stu-id="459f2-203">Deployment Settings Page</span></span>  
 <span data-ttu-id="459f2-204">使用此頁面來指定目的地伺服器以及提供新資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-204">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="459f2-205">**選項**</span><span class="sxs-lookup"><span data-stu-id="459f2-205">**Options**</span></span>  
  
-   <span data-ttu-id="459f2-206">**Azure 虛擬機器**-指定將主控 SQL Server 資料庫之 VM 的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="459f2-206">**Azure Virtual Machine** - Specify details for the VM that will host the SQL Server database:</span></span>  
  
-   <span data-ttu-id="459f2-207">**雲端服務名稱**-指定裝載 VM 的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-207">**Cloud Service name** - Specify the name of the service that hosts the VM.</span></span> <span data-ttu-id="459f2-208">若要建立新的雲端服務，請為新的雲端服務指定名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-208">To create a new Cloud Service, specify a name for the new Cloud Service.</span></span>  
  
-   <span data-ttu-id="459f2-209">**虛擬機器名稱**-指定將主控 SQL Server 資料庫的 VM 名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-209">**Virtual Machine name** - Specify the name of the VM that will host the SQL Server database.</span></span> <span data-ttu-id="459f2-210">若要建立新的 Azure VM，請指定新 VM 的名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-210">To create a new Azure VM, specify a name for the new VM.</span></span>  
  
-   <span data-ttu-id="459f2-211">**設定**-使用 [設定] 按鈕來建立新的 VM，以裝載 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="459f2-211">**Settings** - Use the Settings button to create a new VM to host the SQL Server database.</span></span> <span data-ttu-id="459f2-212">如果您要使用現有的 VM，您提供的資訊將會用來驗證您的認證。</span><span class="sxs-lookup"><span data-stu-id="459f2-212">If you are using an existing VM, the information you provide will be used to authenticate your credentials.</span></span>  
  
-   <span data-ttu-id="459f2-213">**儲存體帳戶**-從下拉式清單中選取儲存體帳戶。</span><span class="sxs-lookup"><span data-stu-id="459f2-213">**Storage account** - Select the storage account from the drop-down list.</span></span> <span data-ttu-id="459f2-214">若要建立新的儲存體帳戶，請為新帳戶指定名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-214">To create a new storage account, specify a name for the new account.</span></span> <span data-ttu-id="459f2-215">請注意，與相似性群組相關聯的儲存體帳戶將不會在下拉式清單中提供。</span><span class="sxs-lookup"><span data-stu-id="459f2-215">Note that storage accounts associated with an Affinity Group will not be available in the drop-down list.</span></span>  
  
-   <span data-ttu-id="459f2-216">**目標資料庫**-指定目標資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-216">**Target Database** - Specify details for the target database.</span></span>  
  
-   <span data-ttu-id="459f2-217">**伺服器連接**-伺服器的連接詳細資料。</span><span class="sxs-lookup"><span data-stu-id="459f2-217">**Server Connection** - Connection details for the server.</span></span>  
  
-   <span data-ttu-id="459f2-218">**資料庫**-指定或確認新資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-218">**Database** - Specify or confirm the name of a new database.</span></span> <span data-ttu-id="459f2-219">如果目的地 SQL Server 執行個體上已經有該資料庫名稱存在，建議您指定另一個修改的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="459f2-219">If the database name already exists on the destination SQL Server instance, we suggest that you specify a modified database name.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="459f2-220">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="459f2-220">Summary Page</span></span>  
 <span data-ttu-id="459f2-221">使用此頁面可檢閱此作業的指定設定。</span><span class="sxs-lookup"><span data-stu-id="459f2-221">Use this page to review the specified settings for the operation.</span></span> <span data-ttu-id="459f2-222">若要使用指定的設定來完成部署作業，請按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="459f2-222">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="459f2-223">若要取消部署作業並結束嚮導，請按一下 [**取消**]。</span><span class="sxs-lookup"><span data-stu-id="459f2-223">To cancel the deploy operation and exit the wizard, click **Cancel**.</span></span>  
  
 <span data-ttu-id="459f2-224">將資料庫詳細資料部署至 Azure VM 上的 SQL Server 資料庫時，可能需要進行手動步驟。</span><span class="sxs-lookup"><span data-stu-id="459f2-224">There may be manual steps required to deploy database details to the SQL Server database on the Azure VM.</span></span> <span data-ttu-id="459f2-225">我們將會詳細說明這些步驟。</span><span class="sxs-lookup"><span data-stu-id="459f2-225">These steps will be outlined in detail for you.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="459f2-226">結果頁面</span><span class="sxs-lookup"><span data-stu-id="459f2-226">Results Page</span></span>  
 <span data-ttu-id="459f2-227">此頁面會報告部署作業成功或失敗，並顯示每個動作的結果。</span><span class="sxs-lookup"><span data-stu-id="459f2-227">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="459f2-228">發生錯誤的所有動作都會在 **[結果]** 資料行中指出。</span><span class="sxs-lookup"><span data-stu-id="459f2-228">Any action that encountered an error will have an indication in the **Result** column.</span></span> <span data-ttu-id="459f2-229">按一下連結，即可檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="459f2-229">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="459f2-230">按一下 **[完成]** 關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="459f2-230">Click **Finish** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459f2-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="459f2-231">See Also</span></span>  
 <span data-ttu-id="459f2-232">[SQL Server 的雲端配接器](../../database-engine/cloud-adapter-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="459f2-232">[Cloud Adapter for SQL Server](../../database-engine/cloud-adapter-for-sql-server.md) </span></span>  
 <span data-ttu-id="459f2-233">[資料庫生命週期管理](../database-lifecycle-management.md) </span><span class="sxs-lookup"><span data-stu-id="459f2-233">[Database Lifecycle Management](../database-lifecycle-management.md) </span></span>  
 <span data-ttu-id="459f2-234">[匯出資料層應用程式](../data-tier-applications/export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="459f2-234">[Export a Data-tier Application](../data-tier-applications/export-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="459f2-235">[匯入 BACPAC 檔案以建立新的使用者資料庫](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span><span class="sxs-lookup"><span data-stu-id="459f2-235">[Import a BACPAC File to Create a New User Database](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span></span>  
 <span data-ttu-id="459f2-236">[Azure SQL Database 備份和還原](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span><span class="sxs-lookup"><span data-stu-id="459f2-236">[Azure SQL Database Backup and Restore](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span></span>  
 <span data-ttu-id="459f2-237">[Azure 虛擬機器中的 SQL Server 部署](https://msdn.microsoft.com/library/dn133141.aspx) </span><span class="sxs-lookup"><span data-stu-id="459f2-237">[SQL Server Deployment in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx) </span></span>  
 [<span data-ttu-id="459f2-238">準備移轉到 Azure 虛擬機器中的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="459f2-238">Getting Ready to Migrate to SQL Server in Azure Virtual Machines</span></span>](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
