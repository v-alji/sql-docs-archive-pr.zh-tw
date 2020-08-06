---
title: 匯出資料層應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.exportdac.settings.f1
- sql12.swb. exportdac.settings.f1
- sql12.swb.exportdac.welcome.f1
- sql12.swb. exportdac.summary.f1
- sql12.swb.exportdac.progress.f1
- sql12.swb.exportdac.summary.f1
- sql12.swb.exportdac.results.f1
- sql12.swb. exportdac.results.f1
helpviewer_keywords:
- How to [DAC], export
- wizard [DAC], export
- export DAC
- data-tier application [SQL Server], export
ms.assetid: 61915bc5-0f5f-45ac-8cfe-3452bc185558
author: stevestein
ms.author: sstein
ms.openlocfilehash: d5e1bbfc5c38dee5e7f29598086d87b680880641
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598989"
---
# <a name="export-a-data-tier-application"></a><span data-ttu-id="ff8d7-102">匯出資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="ff8d7-102">Export a Data-tier Application</span></span>
  <span data-ttu-id="ff8d7-103">匯出已部署的資料層應用程式 (DAC) 或資料庫，會建立匯出檔，而此檔案包含資料庫中物件的定義以及資料表中所含的所有資料。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-103">Exporting a deployed data-tier application (DAC) or database creates an export file that includes both the definitions of the objects in the database and all of the data contained in the tables.</span></span> <span data-ttu-id="ff8d7-104">接著，匯出檔可以匯入 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的另一個執行個體或 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-104">The export file can then be imported to another instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], or to [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="ff8d7-105">匯出-匯入作業可以進行合併以在執行個體之間移轉 DAC、建立邏輯備份或建立 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中所部署資料庫的內部部署複本。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-105">The export-import operations can be combined to migrate a DAC between instances, to create a logical backup, or to create an on-premise copy of a database deployed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ff8d7-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="ff8d7-106">Before You Begin</span></span>  
 <span data-ttu-id="ff8d7-107">匯出程序會使用兩個階段來建立 DAC 匯出檔。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-107">The export process builds a DAC export file in two stages.</span></span>  
  
1.  <span data-ttu-id="ff8d7-108">匯出會在匯出檔 (BACPAC 檔案) 中建置 DAC 定義，其方式相當於 DAC 擷取在 DAC 套件檔案中建置 DAC 定義。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-108">The export builds a DAC definition in the export file - BACPAC file - in the same way a DAC extract builds a DAC definition in a DAC package file.</span></span> <span data-ttu-id="ff8d7-109">匯出的 DAC 定義包含目前資料庫中的所有物件。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-109">The exported DAC definition includes all of the objects in the current database.</span></span> <span data-ttu-id="ff8d7-110">如果匯出程序是針對原本從 DAC 部署的資料庫來執行，並已在部署之後直接變更資料庫，則匯出的定義會符合資料庫中所設定的物件，而非原始 DAC 中所定義的物件。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-110">If the export process is run against a database that was originally deployed from a DAC, and changes were made directly to the database after deployment, the exported definition matches the object set in the database, not what was defined in the original DAC.</span></span>  
  
2.  <span data-ttu-id="ff8d7-111">匯出會大量複製資料庫中所有資料表的資料，並將資料合併至匯出檔。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-111">The export bulk copies out the data from all of the tables in the database and incorporates the data into the export file.</span></span>  
  
 <span data-ttu-id="ff8d7-112">匯出程序會將 DAC 版本設定為 1.0.0.0，而將匯出檔中的 DAC 描述設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-112">The export process sets the DAC version to 1.0.0.0 and the DAC description in the export file to an empty string.</span></span> <span data-ttu-id="ff8d7-113">如果已從 DAC 部署資料庫，則匯出檔中的 DAC 定義會包含指定給原始 DAC 的名稱，否則，DAC 名稱會設定為資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-113">If the database was deployed from a DAC, the DAC definition in the export file contains the name given to the original DAC, otherwise the DAC name is set to the database name.</span></span>  
  

###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ff8d7-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="ff8d7-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ff8d7-115">DAC 或資料庫只能從 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更新版本的資料庫中匯出。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-115">A DAC or database can only be exported from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
 <span data-ttu-id="ff8d7-116">如果 DAC 或包含的使用者中不支援資料庫的物件，則無法匯出資料庫。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-116">You cannot export a database that has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="ff8d7-117">如需有關 DAC 中支援之物件類型的詳細資訊，請參閱＜ [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ff8d7-118">權限</span><span class="sxs-lookup"><span data-stu-id="ff8d7-118">Permissions</span></span>  
 <span data-ttu-id="ff8d7-119">您至少需具備 ALTER ANY LOGIN 和資料庫範圍 VIEW DEFINITION 權限，以及 **sys.sql_expression_dependencies**的 SELECT 權限，才能匯出 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-119">Exporting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="ff8d7-120">匯出 DAC 可以透過 securityadmin 固定伺服器角色的成員來完成，這個角色的成員也是匯出 DAC 之來源資料庫中 database_owner 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-120">Exporting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is exported.</span></span> <span data-ttu-id="ff8d7-121">系統管理員固定伺服器角色的成員或內建 SQL Server 系統管理員帳戶 **sa** 也可以匯出 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also export a DAC.</span></span>  
  
##  <a name="using-the-export-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="ff8d7-122">使用匯出資料層應用程式嚮導</span><span class="sxs-lookup"><span data-stu-id="ff8d7-122">Using the Export Data-tier Application Wizard</span></span>  
 <span data-ttu-id="ff8d7-123">**若要使用精靈匯出 DAC**</span><span class="sxs-lookup"><span data-stu-id="ff8d7-123">**To Export a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="ff8d7-124">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體 (不論是內部部署或在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]中)。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-124">Connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], whether on-premise or in [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
2.  <span data-ttu-id="ff8d7-125">在物件總管\*\*\*\* 中，展開您要匯出 DAC 的執行個體來源節點。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-125">In **Object Explorer**, expand the node for the instance from which you want to export the DAC.</span></span>  
  
3.  <span data-ttu-id="ff8d7-126">以滑鼠右鍵按一下資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-126">Right-click the database name.</span></span>  
  
4.  <span data-ttu-id="ff8d7-127">按一下 [工作]\*\*\*\*，然後選取 [匯出資料層應用程式...]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ff8d7-127">Click **Tasks** and then select **Export Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="ff8d7-128">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="ff8d7-128">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="ff8d7-129">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-129">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="ff8d7-130">匯出設定頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-130">Export Settings Page</span></span>](#Export_settings)  
  
    -   [<span data-ttu-id="ff8d7-131">驗證頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-131">Validation Page</span></span>](#Validation)  
  
    -   [<span data-ttu-id="ff8d7-132">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-132">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="ff8d7-133">進度頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-133">Progress Page</span></span>](#Progress)  
  
    -   [<span data-ttu-id="ff8d7-134">結果頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-134">Results Page</span></span>](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="ff8d7-135">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-135">Introduction Page</span></span>  
 <span data-ttu-id="ff8d7-136">此頁面描述匯出資料層應用程式精靈的步驟。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-136">This page describes the steps for the Export Data-tier Application Wizard.</span></span>  
  
 <span data-ttu-id="ff8d7-137">**選項**</span><span class="sxs-lookup"><span data-stu-id="ff8d7-137">**Options**</span></span>  
  
 <span data-ttu-id="ff8d7-138">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="ff8d7-138">**Do not show this page again.**</span></span> <span data-ttu-id="ff8d7-139">- 按一下此核取方塊，之後就不會再顯示 [簡介] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-139">- Click the check box to stop the Introduction page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="ff8d7-140">**下一步** - 繼續進行 [Select DAC Package (選取 DAC 封裝)]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-140">**Next** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="ff8d7-141">**取消**-取消作業並關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-141">**Cancel** - Cancels the operation and closes the Wizard.</span></span>  
  
##  <a name="export-settings-page"></a><a name="Export_settings"></a><span data-ttu-id="ff8d7-142">[匯出設定] 頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-142">Export Settings Page</span></span>  
 <span data-ttu-id="ff8d7-143">請使用此頁面來指定要建立 BACPAC 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-143">Use this page to specify the location where you want the BACPAC file to be created.</span></span>  
  
-   <span data-ttu-id="ff8d7-144">**儲存至本機磁碟** - 在本機電腦的目錄中建立 BACPAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-144">**Save to local disk** - Creates a BACPAC file in a directory on the local computer.</span></span> <span data-ttu-id="ff8d7-145">按一下 [瀏覽...]\*\*\*\* 巡覽本機電腦，或在提供的空間中指定路徑。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-145">Click **Browse...** to navigate the local computer, or specify the path in the space provided.</span></span> <span data-ttu-id="ff8d7-146">路徑名稱必須包含檔案名稱和 .bacpac 副檔名。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-146">The path name must include a file name and the .bacpac extension.</span></span>  
  
-   <span data-ttu-id="ff8d7-147">**儲存至 Azure** - 在 Azure 容器中建立 BACPAC 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-147">**Save to Azure** - Creates a BACPAC file in an Azure container.</span></span> <span data-ttu-id="ff8d7-148">您必須連線到 Azure 容器，才能驗證此選項。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-148">You must connect to an Azure container in order to validate this option.</span></span> <span data-ttu-id="ff8d7-149">請注意，此選項也會要求您指定暫存檔的本機目錄。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-149">Note that this option also requires that you specify a local directory for the temporary file.</span></span> <span data-ttu-id="ff8d7-150">請注意，暫存檔將建立在指定的位置，而且作業完成之後，將保留在該位置。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-150">Note that the temporary file will be created at the specified location and will remain there after the operation completes.</span></span>  
  
 <span data-ttu-id="ff8d7-151">若要指定要匯出的資料表子集，請使用 [進階]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-151">To specify a subset of tables to export, use the **Advanced** option.</span></span>  
  
##  <a name="validation-page"></a><a name="Validation"></a><span data-ttu-id="ff8d7-152">驗證頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-152">Validation Page</span></span>  
 <span data-ttu-id="ff8d7-153">您可以使用 [驗證] 頁面來檢閱封鎖作業的任何問題。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-153">Use the validation page to review any issues that block the operation.</span></span> <span data-ttu-id="ff8d7-154">若要繼續進行，請解決封鎖問題，然後按一下 **[重新執行驗證]** 確定驗證成功。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-154">To continue, resolve blocking issues and then click **Re-run Validation** to ensure that validation is successful.</span></span>  
  
 <span data-ttu-id="ff8d7-155">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-155">To continue, click **Next**.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="ff8d7-156">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-156">Summary Page</span></span>  
 <span data-ttu-id="ff8d7-157">您可以使用此頁面來檢閱作業的指定來源和目標設定。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-157">Use this page to review the specified source and target settings for the operation.</span></span> <span data-ttu-id="ff8d7-158">若要使用指定的設定來完成匯出作業，請按一下 [完成]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-158">To complete the export operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="ff8d7-159">若要取消匯出作業並結束精靈，請按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-159">To cancel the export operation and exit the Wizard, click **Cancel**.</span></span>  
  
##  <a name="progress-page"></a><a name="Progress"></a> <span data-ttu-id="ff8d7-160">進度頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-160">Progress Page</span></span>  
 <span data-ttu-id="ff8d7-161">此頁面會顯示進度列，指出作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-161">This page displays a progress bar that indicates the status of the operation.</span></span> <span data-ttu-id="ff8d7-162">若要檢視詳細狀態，請按一下 **[檢視詳細資料]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-162">To view detailed status, click the **View details** option.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="ff8d7-163">結果頁面</span><span class="sxs-lookup"><span data-stu-id="ff8d7-163">Results Page</span></span>  
 <span data-ttu-id="ff8d7-164">此頁面會報告匯出作業成功或失敗，並顯示每個動作的結果。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-164">This page reports the success or failure of the export operation, showing the results of each action.</span></span> <span data-ttu-id="ff8d7-165">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-165">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="ff8d7-166">按一下連結，即可檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-166">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="ff8d7-167">按一下 **[完成**] 以關閉嚮導。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-167">Click **Finish** to close the Wizard.</span></span>  
  
##  <a name="using-a-net-framework-application"></a><a name="NetApp"></a><span data-ttu-id="ff8d7-168">使用 .Net Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="ff8d7-168">Using a .Net Framework Application</span></span>  
 <span data-ttu-id="ff8d7-169">**在 .Net Framework 應用程式中使用 Export() 方法，匯出 DAC。**</span><span class="sxs-lookup"><span data-stu-id="ff8d7-169">**To export a DAC using the Export() method in a .Net Framework application.**</span></span>  
  
 <span data-ttu-id="ff8d7-170">若要檢視程式碼範例，請下載 [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)上的 DAC 範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-170">To view a code example, download the DAC sample application on [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575)</span></span>  
  
1.  <span data-ttu-id="ff8d7-171">建立 SMO Server 物件，並將它設定為包含要匯出之 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-171">Create a SMO Server object and set it to the instance that contains the DAC to be exported.</span></span>  
  
2.  <span data-ttu-id="ff8d7-172">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-172">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="ff8d7-173">使用 `Export` 類型的 `Microsoft.SqlServer.Management.Dac.DacStore` 方法，匯出 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-173">Use the `Export` method of the `Microsoft.SqlServer.Management.Dac.DacStore` type to export the DAC.</span></span> <span data-ttu-id="ff8d7-174">指定要匯出之 DAC 的名稱，以及要放置匯出檔之資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="ff8d7-174">Specify the name of the DAC to be exported, and the path to the folder where the export file is to be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8d7-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff8d7-175">See Also</span></span>  
 <span data-ttu-id="ff8d7-176">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ff8d7-176">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="ff8d7-177">從資料庫中擷取 DAC</span><span class="sxs-lookup"><span data-stu-id="ff8d7-177">Extract a DAC From a Database</span></span>](extract-a-dac-from-a-database.md)  
  
  
