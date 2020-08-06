---
title: 使用 DAC 部署資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbdeployment.settings.f1
- sql12.swb.dbdeployment.progress.f1
- sql12.swb.dbdeployment.summary.f1
- sql12.swb.dbdeployment.results.f1
- sql12.swb.dbdeployment.welcome.f1
helpviewer_keywords:
- deploy database wizard
- database deploy [SQL Server]
ms.assetid: 08c506e8-4ba0-4a19-a066-6e6a5c420539
author: stevestein
ms.author: sstein
ms.openlocfilehash: f753cfaf44e51b5bd3ffb939e38e2a300acb9703
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707597"
---
# <a name="deploy-a-database-by-using-a-dac"></a><span data-ttu-id="6600e-102">使用 DAC 來部署資料庫</span><span class="sxs-lookup"><span data-stu-id="6600e-102">Deploy a Database By Using a DAC</span></span>
  <span data-ttu-id="6600e-103">使用 [將資料庫部署到 SQL Azure]  精靈，在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體與 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 伺服器之間部署資料庫，或在兩個 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]伺服器之間部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="6600e-103">Use the **Deploy a Database to SQL Azure** Wizard to deploy a database between an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server, or between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]servers.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="6600e-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="6600e-104">Before You Begin</span></span>  
 <span data-ttu-id="6600e-105">精靈會使用資料層應用程式 (DAC) BACPAC 封存檔案，來部署資料和資料庫物件的定義。</span><span class="sxs-lookup"><span data-stu-id="6600e-105">The wizard uses a Data-tier Application (DAC) BACPAC archive file to deploy both the data and the definitions of database objects.</span></span> <span data-ttu-id="6600e-106">它會從來源資料庫執行 DAC 匯出作業並對目的地資料庫執行 DAC 匯入。</span><span class="sxs-lookup"><span data-stu-id="6600e-106">It performs a DAC export operation from the source database, and a DAC import to the destination.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a> <span data-ttu-id="6600e-107">資料庫選項和設定</span><span class="sxs-lookup"><span data-stu-id="6600e-107">Database Options and Settings</span></span>  
 <span data-ttu-id="6600e-108">根據預設，部署期間建立的資料庫將會擁有 CREATE DATABASE 陳述式中的預設值。</span><span class="sxs-lookup"><span data-stu-id="6600e-108">By default, the database created during the deployment will have the default settings from the CREATE DATABASE statement.</span></span> <span data-ttu-id="6600e-109">例外是資料庫定序和相容性層級會設定為來源資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="6600e-109">The exception is that the database collation and compatibility level are set to the values from the source database.</span></span>  
  
 <span data-ttu-id="6600e-110">資料庫選項 (例如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY) 無法在部署過程中調整。</span><span class="sxs-lookup"><span data-stu-id="6600e-110">Database options, such as TRUSTWORTHY, DB_CHAINING and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="6600e-111">實體屬性 (如檔案群組數目或檔案數目和大小) 無法在部署過程中更改。</span><span class="sxs-lookup"><span data-stu-id="6600e-111">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="6600e-112">部署完成之後，您可以使用 ALTER DATABASE 陳述式、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 來修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="6600e-112">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="6600e-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="6600e-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6600e-114">**[部署資料庫]** 精靈支援在下列項目上部署資料庫：</span><span class="sxs-lookup"><span data-stu-id="6600e-114">The **Deploy Database** wizard supports deploying a database:</span></span>  
  
-   <span data-ttu-id="6600e-115">從 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體至 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6600e-115">From an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span>  
  
-   <span data-ttu-id="6600e-116">從 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="6600e-116">From [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="6600e-117">兩個 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 伺服器之間。</span><span class="sxs-lookup"><span data-stu-id="6600e-117">Between two [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] servers.</span></span>  
  
 <span data-ttu-id="6600e-118">精靈不支援在兩個 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體之間部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="6600e-118">The wizard does not support deploying databases between two instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="6600e-119">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體必須執行 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更新版本，才能使用精靈。</span><span class="sxs-lookup"><span data-stu-id="6600e-119">An instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later to work with the wizard.</span></span> <span data-ttu-id="6600e-120">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體上的資料庫物件不受 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]支援，則無法使用此精靈將資料庫部署到 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6600e-120">If a database on an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] contains objects not supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], you cannot use the wizard to deploy the database to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="6600e-121">如果 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 上的資料庫物件不受 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]支援，則無法使用此精靈將資料庫部署到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="6600e-121">If a database on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] contains objects not supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you cannot use the wizard to deploy the database to instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6600e-122">Security</span><span class="sxs-lookup"><span data-stu-id="6600e-122">Security</span></span>  
 <span data-ttu-id="6600e-123">為了提高安全性，SQL Server 驗證登入會儲存在 DAC BACPAC 檔案中，而且沒有密碼。</span><span class="sxs-lookup"><span data-stu-id="6600e-123">To improve security, SQL Server Authentication logins are stored in a DAC BACPAC file without a password.</span></span> <span data-ttu-id="6600e-124">當您匯入 BACPAC 之後，此登入會建立為停用的登入，而且會產生密碼。</span><span class="sxs-lookup"><span data-stu-id="6600e-124">When the BACPAC is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="6600e-125">若要啟用登入，請使用具有 ALTER ANY LOGIN 權限的登入進行登入，並使用 ALTER LOGIN 來啟用登入，然後指派可以傳達給使用者的新密碼。</span><span class="sxs-lookup"><span data-stu-id="6600e-125">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="6600e-126">Windows 驗證登入不需要這項處理，因為這類登入的密碼不是由 SQL Server 所管理。</span><span class="sxs-lookup"><span data-stu-id="6600e-126">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
#### <a name="permissions"></a><span data-ttu-id="6600e-127">權限</span><span class="sxs-lookup"><span data-stu-id="6600e-127">Permissions</span></span>  
 <span data-ttu-id="6600e-128">精靈需要來源資料庫的 DAC 匯出權限。</span><span class="sxs-lookup"><span data-stu-id="6600e-128">The wizard requires DAC export permissions on the source database.</span></span> <span data-ttu-id="6600e-129">登入至少需要 ALTER ANY LOGIN 和資料庫範圍 VIEW DEFINITION 權限，以及 **sys.sql_expression_dependencies**的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="6600e-129">The login requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="6600e-130">匯出 DAC 可以透過 securityadmin 固定伺服器角色的成員來完成，這個角色的成員也是匯出 DAC 之來源資料庫中 database_owner 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6600e-130">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="6600e-131">系統管理員固定伺服器角色的成員或內建 SQL Server 系統管理員帳戶 **sa** 也可以匯出 DAC。</span><span class="sxs-lookup"><span data-stu-id="6600e-131">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
 <span data-ttu-id="6600e-132">精靈需要目的地執行個體或伺服器的 DAC 匯入權限。</span><span class="sxs-lookup"><span data-stu-id="6600e-132">The wizard requires DAC import permissions on the destination instance or server.</span></span> <span data-ttu-id="6600e-133">登入必須是 **系統管理員 (sysadmin)** 或 **伺服器管理員 (serveradmin)** 固定伺服器角色的成員，或是具有 **dbcreator** 固定伺服器角色及擁有 ALTER ANY LOGIN 權限。</span><span class="sxs-lookup"><span data-stu-id="6600e-133">The login must be a member of the **sysadmin** or **serveradmin** fixed server roles, or in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="6600e-134">內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶 (名稱為 **sa** ) 也可以匯入 DAC。</span><span class="sxs-lookup"><span data-stu-id="6600e-134">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="6600e-135">將具有登入的 DAC 匯入至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 loginmanager 或 serveradmin 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6600e-135">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="6600e-136">將不具有登入的 DAC 匯入至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 dbmanager 或 serveradmin 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="6600e-136">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-database-wizard"></a><a name="UsingDeployDACWizard"></a> <span data-ttu-id="6600e-137">使用部署資料庫精靈</span><span class="sxs-lookup"><span data-stu-id="6600e-137">Using the Deploy Database Wizard</span></span>  
 <span data-ttu-id="6600e-138">**若要使用部署資料庫精靈移轉資料庫**</span><span class="sxs-lookup"><span data-stu-id="6600e-138">**To migrate a database using the Deploy Database Wizard**</span></span>  
  
1.  <span data-ttu-id="6600e-139">連接至您要部署的資料庫位置。</span><span class="sxs-lookup"><span data-stu-id="6600e-139">Connect to the location of the database you want to deploy.</span></span> <span data-ttu-id="6600e-140">您可以指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體或 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6600e-140">You can specify either an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] or a [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] server.</span></span>  
  
2.  <span data-ttu-id="6600e-141">在 **[物件總管]** 中，展開含有資料庫的執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="6600e-141">In **Object Explorer**, expand the node for the instance that has the database.</span></span>  
  
3.  <span data-ttu-id="6600e-142">展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="6600e-142">Expand the **Databases** node.</span></span>  
  
4.  <span data-ttu-id="6600e-143">以滑鼠右鍵按一下您要部署的資料庫，選取 [工作]  ，然後選取 [將資料庫部署到 SQL Azure...] </span><span class="sxs-lookup"><span data-stu-id="6600e-143">Right click the database you want to deploy, select **Tasks**, and then select **Deploy Database to SQL Azure...**</span></span>  
  
5.  <span data-ttu-id="6600e-144">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="6600e-144">Complete the Wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="6600e-145">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-145">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="6600e-146">部署設定</span><span class="sxs-lookup"><span data-stu-id="6600e-146">Deployment Settings</span></span>](#Deployment_settings)  
  
    -   [<span data-ttu-id="6600e-147">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-147">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="6600e-148">結果</span><span class="sxs-lookup"><span data-stu-id="6600e-148">Results</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="6600e-149">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-149">Introduction Page</span></span>  
 <span data-ttu-id="6600e-150">此頁面描述 **[部署資料庫]** 精靈的步驟。</span><span class="sxs-lookup"><span data-stu-id="6600e-150">This page describes the steps for the **Deploy Database** Wizard.</span></span>  
  
 <span data-ttu-id="6600e-151">**選項**</span><span class="sxs-lookup"><span data-stu-id="6600e-151">**Options**</span></span>  
  
-   <span data-ttu-id="6600e-152">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="6600e-152">**Do not show this page again.**</span></span> <span data-ttu-id="6600e-153">- 按一下此核取方塊，之後就不會再顯示 [簡介] 頁面。</span><span class="sxs-lookup"><span data-stu-id="6600e-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="6600e-154">**下一步** - 繼續進行 **[部署設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="6600e-154">**Next** - Proceeds to the **Deployment Settings** page.</span></span>  
  
-   <span data-ttu-id="6600e-155">**取消**-取消作業並關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="6600e-155">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="6600e-156">[部署設定] 頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-156">Deployment Settings Page</span></span>  
 <span data-ttu-id="6600e-157">使用此頁面來指定目的地伺服器以及提供新資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6600e-157">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="6600e-158">**本機主機：**</span><span class="sxs-lookup"><span data-stu-id="6600e-158">**Local host:**</span></span>  
  
-   <span data-ttu-id="6600e-159">**伺服器連接** - 指定伺服器連接的詳細資料，然後按一下 [連接]\*\*\*\* 來驗證連接。</span><span class="sxs-lookup"><span data-stu-id="6600e-159">**Server connection** - Specify server connection details and then click **Connect** to verify the connection.</span></span>  
  
-   <span data-ttu-id="6600e-160">**新資料庫名稱** - 指定新資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="6600e-160">**New database name** - Specify a name for the new database.</span></span>  
  
 <span data-ttu-id="6600e-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)]資料庫設定：**</span><span class="sxs-lookup"><span data-stu-id="6600e-161">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] database settings:**</span></span>  
  
-   <span data-ttu-id="6600e-162">\*\* [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 版本\*\*- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 從下拉式功能表中選取的版本。</span><span class="sxs-lookup"><span data-stu-id="6600e-162">**[!INCLUDE[ssSDS](../../includes/sssds-md.md)] edition** - Select the edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)] from the drop-down menu.</span></span>  
  
-   <span data-ttu-id="6600e-163">**資料庫大小上限** - 從下拉式功能表中選取資料庫大小上限。</span><span class="sxs-lookup"><span data-stu-id="6600e-163">**Maximum database size** - Select the maximum database size from the drop-down menu.</span></span>  
  
 <span data-ttu-id="6600e-164">**其他設定：**</span><span class="sxs-lookup"><span data-stu-id="6600e-164">**Other settings:**</span></span>  
  
-   <span data-ttu-id="6600e-165">指定暫存檔 (即 BACPAC 封存檔案) 的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="6600e-165">Specify a local directory for the temporary file, which is the BACPAC archive file.</span></span> <span data-ttu-id="6600e-166">請注意，檔案將在指定的位置上建立，而且作業完成之後，將保留在該位置。</span><span class="sxs-lookup"><span data-stu-id="6600e-166">Note that the file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="6600e-167">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-167">Summary Page</span></span>  
 <span data-ttu-id="6600e-168">您可以使用此頁面來檢閱作業的指定來源和目標設定。</span><span class="sxs-lookup"><span data-stu-id="6600e-168">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="6600e-169">若要使用指定的設定來完成部署作業，請按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="6600e-169">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="6600e-170">若要取消部署作業並結束精靈，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="6600e-170">To cancel the deploy operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="6600e-171">進度頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-171">Progress Page</span></span>  
 <span data-ttu-id="6600e-172">此頁面會顯示進度列，指出作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="6600e-172">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="6600e-173">若要檢視詳細狀態，請按一下 **[檢視詳細資料]** 選項。</span><span class="sxs-lookup"><span data-stu-id="6600e-173">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="6600e-174">結果頁面</span><span class="sxs-lookup"><span data-stu-id="6600e-174">Results Page</span></span>  
 <span data-ttu-id="6600e-175">此頁面會報告部署作業成功或失敗，並顯示每個動作的結果。</span><span class="sxs-lookup"><span data-stu-id="6600e-175">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="6600e-176">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="6600e-176">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="6600e-177">按一下連結，即可檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="6600e-177">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="6600e-178">按一下 **[完成**] 以關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="6600e-178">Click **Finish** to close the Wizard.</span></span>  
  
## <a name="using-a-net-framework-application"></a><span data-ttu-id="6600e-179">使用 .Net Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="6600e-179">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="6600e-180">**在 .Net Framework 應用程式中使用 DacStoreExport() 與 Import() 方法，以部署資料庫。**</span><span class="sxs-lookup"><span data-stu-id="6600e-180">**To deploy a database using the DacStoreExport() and Import() methods in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="6600e-181">若要檢視程式碼範例，請下載 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)上的 DAC 範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="6600e-181">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="6600e-182">建立 SMO Server 物件，並將它設定為包含要部署之資料庫的執行個體或伺服器。</span><span class="sxs-lookup"><span data-stu-id="6600e-182">Create a SMO Server object and set it to the instance or server that contains the database to be deployed.</span></span>  
  
2.  <span data-ttu-id="6600e-183">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6600e-183">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="6600e-184">使用 `Export` 類型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法，將資料庫匯出至 BACPAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="6600e-184">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the database to a BACPAC file.</span></span> <span data-ttu-id="6600e-185">指定要匯出之資料庫的名稱，以及要放置 BACPAC 檔案之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="6600e-185">Specify the name of the database to be exported, and the path to the folder where the BACPAC file is to be placed.</span></span>  
  
4.  <span data-ttu-id="6600e-186">建立 SMO Server 物件，並將它設定為目的地執行個體或伺服器。</span><span class="sxs-lookup"><span data-stu-id="6600e-186">Create a SMO Server object and set it to the destination instance or server.</span></span>  
  
5.  <span data-ttu-id="6600e-187">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6600e-187">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
6.  <span data-ttu-id="6600e-188">使用 `Import` 類型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法，匯入 BACPAC。</span><span class="sxs-lookup"><span data-stu-id="6600e-188">Use the `Import` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to import the BACPAC.</span></span> <span data-ttu-id="6600e-189">指定匯出所建立的 BACPAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="6600e-189">Specify the BACPAC file created by the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6600e-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6600e-190">See Also</span></span>  
 <span data-ttu-id="6600e-191">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="6600e-191">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="6600e-192">[匯出資料層應用程式](export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="6600e-192">[Export a Data-tier Application](export-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="6600e-193">匯入 BACPAC 檔案以建立新的使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="6600e-193">Import a BACPAC File to Create a New User Database</span></span>](import-a-bacpac-file-to-create-a-new-user-database.md)  
  
  
