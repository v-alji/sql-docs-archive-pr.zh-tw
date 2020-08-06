---
title: 匯入 BACPAC 檔案以建立新的使用者資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.importdac.progress.f1
- sql12.swb. importdac.settings.f1
- sql12.swb.importdac.storagebrowser.f1
- sql12.swb. importdac.summary.f1
- sql12.swb.importdac.results.f1
- sql12.swb. importdac.progress.f1
- sql12.swb.importdac.welcome.f1
- sql12.swb.importdac.settings.f1
- sql12.swb. importdac.results.f1
- sql12.swb.importdac.summary.f1
helpviewer_keywords:
- Data-tier application
- SQL Server DAC
- Migrate database
- DAC
ms.assetid: 736d8d9a-39f1-4bf8-b81f-2e56c134d12e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66e71453f38fe15f295fceaf63b5edba5ab5ff43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598444"
---
# <a name="import-a-bacpac-file-to-create-a-new-user-database"></a><span data-ttu-id="e0cba-102">匯入 BACPAC 檔案以建立新的使用者資料庫</span><span class="sxs-lookup"><span data-stu-id="e0cba-102">Import a BACPAC File to Create a New User Database</span></span>
  <span data-ttu-id="e0cba-103">匯入資料層應用程式 (DAC) 檔案 (.bacpac 檔案)，可在新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體上，建立原始資料庫連同其資料的複本，或將該檔案匯入 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e0cba-103">Import a data-tier application (DAC) file - a .bacpac file - to create a copy of the original database, with the data, on a new instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="e0cba-104">匯出-匯入作業可以進行合併以在執行個體之間移轉 DAC 或資料庫，或建立邏輯備份 (例如建立 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中所部署資料庫的內部部署複本)。</span><span class="sxs-lookup"><span data-stu-id="e0cba-104">Export-import operations can be combined to migrate a DAC or database between instances, or to create a logical backup, such as creating an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e0cba-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="e0cba-105">Before You Begin</span></span>  
 <span data-ttu-id="e0cba-106">匯入程序會使用兩個階段來建立新的 DAC。</span><span class="sxs-lookup"><span data-stu-id="e0cba-106">The import process builds a new DAC in two stages.</span></span>  
  
1.  <span data-ttu-id="e0cba-107">匯入會使用儲存在匯出檔案中的 DAC 定義，建立新的 DAC 及相關聯的資料庫，其方式相當於 DAC 部署從 DAC 封裝檔案中的定義建立新的 DAC。</span><span class="sxs-lookup"><span data-stu-id="e0cba-107">The import creates a new DAC and associated database using the DAC definition stored in the export file, the same way a DAC deploy creates a new DAC from the definition in a DAC package file.</span></span>  
  
2.  <span data-ttu-id="e0cba-108">匯入會從匯出檔案大量複製資料。</span><span class="sxs-lookup"><span data-stu-id="e0cba-108">The import bulk copies in the data from the export file.</span></span>  
  
 
## <a name="sql-server-utility"></a><span data-ttu-id="e0cba-109">SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="e0cba-109">SQL Server Utility</span></span>  
 <span data-ttu-id="e0cba-110">如果您將 DAC 匯入至 Database Engine 的受管理執行個體，下次從執行個體將公用程式收集組傳送到公用程式控制點時，匯入的 DAC 就會合併至 SQL Server 公用程式。</span><span class="sxs-lookup"><span data-stu-id="e0cba-110">If you import a DAC to a managed instance of the Database Engine, the imported DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="e0cba-111">然後 DAC 會出現在  **[公用程式總管]** [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 的 [部署的資料層應用程式]  節點中，並在 [部署的資料層應用程式]  詳細資料頁面中報告。</span><span class="sxs-lookup"><span data-stu-id="e0cba-111">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
## <a name="database-options-and-settings"></a><span data-ttu-id="e0cba-112">資料庫選項和設定</span><span class="sxs-lookup"><span data-stu-id="e0cba-112">Database Options and Settings</span></span>  
 <span data-ttu-id="e0cba-113">根據預設，匯入期間建立的資料庫將會擁有 CREATE DATABASE 陳述式中的所有預設值，但是資料庫定序和相容性層級會設定為 DAC 匯出檔案中所定義的值。</span><span class="sxs-lookup"><span data-stu-id="e0cba-113">By default, the database created during the import will have all of the default settings from the CREATE DATABASE statement, except that the database collation and compatibility level are set to the values defined in the DAC export file.</span></span> <span data-ttu-id="e0cba-114">DAC 匯出檔案使用原始資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="e0cba-114">A DAC export file uses the values from the original database.</span></span>  
  
 <span data-ttu-id="e0cba-115">某些資料庫選項 (例如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY) 無法在匯入過程中調整。</span><span class="sxs-lookup"><span data-stu-id="e0cba-115">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the import process.</span></span> <span data-ttu-id="e0cba-116">實體屬性 (如檔案群組數目或檔案數目和大小) 無法在匯入過程中更改。</span><span class="sxs-lookup"><span data-stu-id="e0cba-116">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the import process.</span></span> <span data-ttu-id="e0cba-117">匯入完成之後，您可以使用 ALTER DATABASE 陳述式、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 來調整資料庫。</span><span class="sxs-lookup"><span data-stu-id="e0cba-117">After the import completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span> <span data-ttu-id="e0cba-118">如需詳細資訊，請參閱 [Databases](../databases/databases.md)。</span><span class="sxs-lookup"><span data-stu-id="e0cba-118">For more information, see [Databases](../databases/databases.md).</span></span>  
  
## <a name="limitations-and-restrictions"></a><span data-ttu-id="e0cba-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="e0cba-119">Limitations and Restrictions</span></span>  
 <span data-ttu-id="e0cba-120">DAC 可匯入至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 或更新版本的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0cba-120">A DAC can be imported to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="e0cba-121">如果您從更新版本匯出 DAC，則 DAC 可能會包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]不支援的物件。</span><span class="sxs-lookup"><span data-stu-id="e0cba-121">If you export a DAC from a higher version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="e0cba-122">您無法將這些 DAC 部署至 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0cba-122">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e0cba-123">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e0cba-123">Prerequisites</span></span>  
 <span data-ttu-id="e0cba-124">建議您不要匯入來源不明或來源不受信任的 DAC 匯出檔案。</span><span class="sxs-lookup"><span data-stu-id="e0cba-124">We recommend that you do not import a DAC export file from unknown or untrusted sources.</span></span> <span data-ttu-id="e0cba-125">這類檔案可能包含惡意程式碼，因此可能會執行非預期的 Transact-SQL 程式碼，或是修改結構描述而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0cba-125">Such files could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="e0cba-126">在您使用來源不明或來源不受信任的匯出檔案之前，請解除封裝 DAC 並檢查程式碼，例如預存程序和其他使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0cba-126">Before you use an export file from an unknown or untrusted source, unpack the DAC and examine the code, like stored procedures and other user-defined code.</span></span> <span data-ttu-id="e0cba-127">如需有關如何執行這些檢查的詳細資訊，請參閱＜ [Validate a DAC Package](validate-a-dac-package.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e0cba-127">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="e0cba-128">安全性</span><span class="sxs-lookup"><span data-stu-id="e0cba-128">Security</span></span>  
 <span data-ttu-id="e0cba-129">為了提高安全性，SQL Server 驗證登入會儲存在 DAC 匯出檔案中，而且沒有密碼。</span><span class="sxs-lookup"><span data-stu-id="e0cba-129">To improve security, SQL Server Authentication logins are stored in a DAC export file without a password.</span></span> <span data-ttu-id="e0cba-130">當您匯入檔案之後，此登入會建立為停用的登入，而且會產生密碼。</span><span class="sxs-lookup"><span data-stu-id="e0cba-130">When the file is imported, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="e0cba-131">若要啟用登入，請使用具有 ALTER ANY LOGIN 權限的登入進行登入，並使用 ALTER LOGIN 來啟用登入，然後指派可以傳達給使用者的新密碼。</span><span class="sxs-lookup"><span data-stu-id="e0cba-131">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="e0cba-132">Windows 驗證登入不需要這項處理，因為這類登入的密碼不是由 SQL Server 所管理。</span><span class="sxs-lookup"><span data-stu-id="e0cba-132">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="e0cba-133">權限</span><span class="sxs-lookup"><span data-stu-id="e0cba-133">Permissions</span></span>  
 <span data-ttu-id="e0cba-134">只有 **系統管理員 (sysadmin)** 或 **serveradmin** 固定伺服器角色的成員，或是具有 **dbcreator** 固定伺服器角色且擁有 ALTER ANY LOGIN 權限的登入，才能匯入 DAC。</span><span class="sxs-lookup"><span data-stu-id="e0cba-134">A DAC can only be imported by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="e0cba-135">內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶 (名稱為 **sa** ) 也可以匯入 DAC。</span><span class="sxs-lookup"><span data-stu-id="e0cba-135">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also import a DAC.</span></span> <span data-ttu-id="e0cba-136">將具有登入的 DAC 匯入至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 loginmanager 或 serveradmin 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="e0cba-136">Importing a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="e0cba-137">將不具有登入的 DAC 匯入至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 dbmanager 或 serveradmin 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="e0cba-137">Importing a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
## <a name="using-the-import-data-tier-application-wizard"></a><span data-ttu-id="e0cba-138">使用匯入資料層應用程式精靈</span><span class="sxs-lookup"><span data-stu-id="e0cba-138">Using the Import Data-tier Application Wizard</span></span>  
 <span data-ttu-id="e0cba-139">**若要啟動此精靈，請使用下列步驟：**</span><span class="sxs-lookup"><span data-stu-id="e0cba-139">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="e0cba-140">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體 (不論是內部部署或在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中)。</span><span class="sxs-lookup"><span data-stu-id="e0cba-140">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="e0cba-141">在 **[物件總管]** 的 **[資料庫]** 上按一下滑鼠右鍵，然後選取 **[匯入資料層應用程式]** 功能表項目啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="e0cba-141">In **Object Explorer**, right-click on **Databases**, and then select the **Import Data-tier Application** menu item to launch the wizard.</span></span>  
  
3.  <span data-ttu-id="e0cba-142">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="e0cba-142">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="e0cba-143">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-143">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="e0cba-144">匯入設定頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-144">Import Settings Page</span></span>](#Import_settings)  
  
    -   [<span data-ttu-id="e0cba-145">資料庫設定頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-145">Database Settings Page</span></span>](#Database_settings)  
  
    -   [<span data-ttu-id="e0cba-146">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-146">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="e0cba-147">進度頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-147">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="e0cba-148">結果頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-148">Results Page</span></span>](#Results)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="e0cba-149">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-149">Introduction Page</span></span>  
 <span data-ttu-id="e0cba-150">此頁面描述的是資料層應用程式匯入精靈的步驟。</span><span class="sxs-lookup"><span data-stu-id="e0cba-150">This page describes the steps for the Data-tier Application Import Wizard.</span></span>  
  
 <span data-ttu-id="e0cba-151">**選項**</span><span class="sxs-lookup"><span data-stu-id="e0cba-151">**Options**</span></span>  
  
-   <span data-ttu-id="e0cba-152">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="e0cba-152">**Do not show this page again.**</span></span> <span data-ttu-id="e0cba-153">- 按一下此核取方塊，之後就不會再顯示 [簡介] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e0cba-153">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="e0cba-154">**下一步** - 繼續進行 [匯入設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="e0cba-154">**Next** - Proceeds to the **Import Settings** page.</span></span>  
  
-   <span data-ttu-id="e0cba-155">**取消** - 取消作業並關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="e0cba-155">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
###  <a name="import-settings-page"></a><a name="Import_settings"></a> <span data-ttu-id="e0cba-156">匯入設定頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-156">Import Settings Page</span></span>  
 <span data-ttu-id="e0cba-157">您可以使用此頁面來指定要匯入之 .bacpac 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="e0cba-157">Use this page to specify the location of the .bacpac file to import.</span></span>  
  
-   <span data-ttu-id="e0cba-158">**從本機磁碟匯入** - 按一下 [瀏覽...]  巡覽本機電腦，或在提供的空間中指定路徑。</span><span class="sxs-lookup"><span data-stu-id="e0cba-158">**Import from local disk** - Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="e0cba-159">路徑名稱必須包含檔案名稱和 .bacpac 副檔名。</span><span class="sxs-lookup"><span data-stu-id="e0cba-159">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="e0cba-160">**從 azure 匯入**-從 azure 容器匯入 BACPAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0cba-160">**Import from Azure** - Imports a BACPAC file from an Azure container.</span></span> <span data-ttu-id="e0cba-161">您必須連線到 Azure 容器，才能驗證此選項。</span><span class="sxs-lookup"><span data-stu-id="e0cba-161">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="e0cba-162">請注意，此選項也會要求您指定暫存檔的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e0cba-162">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="e0cba-163">暫存檔將建立在指定的位置，而且作業完成之後，將保留在該位置。</span><span class="sxs-lookup"><span data-stu-id="e0cba-163">The temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
     <span data-ttu-id="e0cba-164">瀏覽 Azure 時，您可以在單一帳戶中的容器之間切換。</span><span class="sxs-lookup"><span data-stu-id="e0cba-164">When browsing Azure, you will be able to switch between containers within a single account.</span></span> <span data-ttu-id="e0cba-165">您必須指定單一 .bacpac 檔案，才能繼續進行匯入作業。</span><span class="sxs-lookup"><span data-stu-id="e0cba-165">You must specify a single .bacpac file to continue the import operation.</span></span> <span data-ttu-id="e0cba-166">請注意，您可以依照 **[名稱]**、 **[大小]** 或 **[修改日期]** 排序資料行。</span><span class="sxs-lookup"><span data-stu-id="e0cba-166">Note that you can sort columns by **Name**, **Size**, or **Date Modified**.</span></span>  
  
     <span data-ttu-id="e0cba-167">若要繼續進行，請指定要匯入的 .bacpac 檔案，然後按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-167">To continue, specify the .bacpac file to import, and then click **Open**.</span></span>  
  
###  <a name="database-settings-page"></a><a name="Database_settings"></a> <span data-ttu-id="e0cba-168">資料庫設定頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-168">Database Settings Page</span></span>  
 <span data-ttu-id="e0cba-169">您可以使用此頁面指定要建立之資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e0cba-169">Use this page to specify details for the database that will be created.</span></span>  
  
 <span data-ttu-id="e0cba-170">**若為 SQL Server 的本機執行個體：**</span><span class="sxs-lookup"><span data-stu-id="e0cba-170">**For a local instance of SQL Server:**</span></span>  
  
-   <span data-ttu-id="e0cba-171">**新資料庫名稱** - 針對匯入的資料庫提供名稱。</span><span class="sxs-lookup"><span data-stu-id="e0cba-171">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="e0cba-172">**資料檔案路徑** - 提供資料檔案的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e0cba-172">**Data file path** - Provide a local directory for data files.</span></span> <span data-ttu-id="e0cba-173">按一下 [瀏覽...]  巡覽本機電腦，或在提供的空間中指定路徑。</span><span class="sxs-lookup"><span data-stu-id="e0cba-173">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
-   <span data-ttu-id="e0cba-174">**記錄檔路徑** - 提供記錄檔的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e0cba-174">**Log file path** - Provide a local directory for log files.</span></span> <span data-ttu-id="e0cba-175">按一下 [瀏覽...]  巡覽本機電腦，或在提供的空間中指定路徑。</span><span class="sxs-lookup"><span data-stu-id="e0cba-175">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span>  
  
 <span data-ttu-id="e0cba-176">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-176">To continue, click **Next**.</span></span>  
  
 <span data-ttu-id="e0cba-177">**若為 SQL 資料庫：**</span><span class="sxs-lookup"><span data-stu-id="e0cba-177">**For a SQL Database:**</span></span>  
  
-   <span data-ttu-id="e0cba-178">**新資料庫名稱** - 針對匯入的資料庫提供名稱。</span><span class="sxs-lookup"><span data-stu-id="e0cba-178">**New database name** - Provide a name for the imported database.</span></span>  
  
-   <span data-ttu-id="e0cba-179">**的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 版本**-指定 [ [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business] 或 [Web] [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-179">**Edition of [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** - Specify [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Business or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Web.</span></span> <span data-ttu-id="e0cba-180">如需有關 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]版本的詳細資訊，請參閱這個 [SQL 資料庫](https://www.windowsazure.com/home/tour/database/) 網站。</span><span class="sxs-lookup"><span data-stu-id="e0cba-180">For more information about editions of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], see this [SQL Database](https://www.windowsazure.com/home/tour/database/) web site.</span></span>  
  
-   <span data-ttu-id="e0cba-181">\*\*資料庫大小上限 (GB) \*\* -使用下拉式功能表來指定資料庫的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e0cba-181">**Maximum database size (GB)** - Use the drop-down menu to specify the maximum size for your database.</span></span>  
  
 <span data-ttu-id="e0cba-182">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-182">To continue, click **Next**.</span></span>  
  
### <a name="validation-page"></a><span data-ttu-id="e0cba-183">驗證頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-183">Validation Page</span></span>  
 <span data-ttu-id="e0cba-184">您可以使用此頁面檢閱造成此作業無法執行的任何問題。</span><span class="sxs-lookup"><span data-stu-id="e0cba-184">Use this page to review any issues that block the operation.</span></span> <span data-ttu-id="e0cba-185">若要繼續進行，請解決封鎖問題，然後按一下 **[重新執行驗證]** 確定驗證成功。</span><span class="sxs-lookup"><span data-stu-id="e0cba-185">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="e0cba-186">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-186">To continue, click **Next**.</span></span>  
  
###  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="e0cba-187">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-187">Summary Page</span></span>  
 <span data-ttu-id="e0cba-188">您可以使用此頁面來檢閱作業的指定來源和目標設定。</span><span class="sxs-lookup"><span data-stu-id="e0cba-188">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="e0cba-189">若要使用指定的設定來完成匯入作業，請按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="e0cba-189">To complete the import operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="e0cba-190">若要取消匯入作業並結束精靈，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="e0cba-190">To cancel the import operation and exit the wizard, click **Cancel**.</span></span>  
  
###  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="e0cba-191">進度頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-191">Progress Page</span></span>  
 <span data-ttu-id="e0cba-192">此頁面會顯示進度列，指出作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="e0cba-192">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="e0cba-193">若要檢視詳細狀態，請按一下 **[檢視詳細資料]** 選項。</span><span class="sxs-lookup"><span data-stu-id="e0cba-193">To view detailed status, click the **View details** option.</span></span>  
  
 <span data-ttu-id="e0cba-194">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="e0cba-194">To continue, click **Next**.</span></span>  
  
###  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="e0cba-195">結果頁面</span><span class="sxs-lookup"><span data-stu-id="e0cba-195">Results Page</span></span>  
 <span data-ttu-id="e0cba-196">此頁面會報告匯入和建立資料庫作業成功或失敗，並顯示每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="e0cba-196">This page reports the success or failure of the import and create database operations, showing the success or failure of each action.</span></span> <span data-ttu-id="e0cba-197">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="e0cba-197">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="e0cba-198">按一下連結，即可檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="e0cba-198">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="e0cba-199">按一下 [關閉]\*\*\*\* 以關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="e0cba-199">Click **Close** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0cba-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0cba-200">See Also</span></span>  
 <span data-ttu-id="e0cba-201">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e0cba-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="e0cba-202">匯出資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="e0cba-202">Export a Data-tier Application</span></span>](export-a-data-tier-application.md)  
  
