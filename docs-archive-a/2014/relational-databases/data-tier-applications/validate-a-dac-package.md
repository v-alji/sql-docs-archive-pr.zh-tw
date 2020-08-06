---
title: 驗證 DAC 封裝 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], validate
- data-tier application [SQL Server], compare
- validate DAC
- compare DACs
- data-tier application [SQL Server], view
- view DAC
ms.assetid: 726ffcc2-9221-424a-8477-99e3f85f03bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 078c7bfeef2ff8636243f4853c03de252c7b9289
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606368"
---
# <a name="validate-a-dac-package"></a><span data-ttu-id="d527b-102">驗證 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="d527b-102">Validate a DAC Package</span></span>
  <span data-ttu-id="d527b-103">最好先檢閱 DAC 封裝的內容，再將它部署至實際執行環境，以及先驗證升級動作，再升級現有 DAC。</span><span class="sxs-lookup"><span data-stu-id="d527b-103">It is a good practice to review the contents of a DAC package before deploying it in production, and to validate the upgrade actions before upgrading an existing DAC.</span></span> <span data-ttu-id="d527b-104">當您部署的封裝之前不是在組織內開發時，特別會是這個情況。</span><span class="sxs-lookup"><span data-stu-id="d527b-104">This is especially true when deploying packages that were not developed in your organization.</span></span>  
  
1.  <span data-ttu-id="d527b-105">**開始之前：** [必要條件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="d527b-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
2.  <span data-ttu-id="d527b-106">**若要升級 DAC，請使用下列方式：** [檢視 DAC 內容](#ViewDACContents)、[檢視資料庫變更](#ViewDBChanges)、[檢視升級動作](#ViewUpgradeActions)、[比較 DAC](#CompareDACs)</span><span class="sxs-lookup"><span data-stu-id="d527b-106">**To upgrade a DAC, using:**  [View the Contents of a DAC](#ViewDACContents), [View Database Changes](#ViewDBChanges), [View Upgrade Actions](#ViewUpgradeActions), [Compare DACs](#CompareDACs)</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d527b-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="d527b-107">Prerequisites</span></span>  
 <span data-ttu-id="d527b-108">建議您不要部署來源不明或來源不受信任的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="d527b-108">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="d527b-109">這類 DAC 可能包含惡意程式碼，因此可能會執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="d527b-109">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="d527b-110">使用來源不明或來源不受信任的 DAC 之前，請先將它部署到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的隔離測試執行個體，並在資料庫上執行 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)，然後檢查資料庫中的程式碼，例如預存程序或其他使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d527b-110">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], run [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database, and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="view-the-contents-of-a-dac"></a><a name="ViewDACContents"></a> <span data-ttu-id="d527b-111">檢視 DAC 內容</span><span class="sxs-lookup"><span data-stu-id="d527b-111">View the Contents of a DAC</span></span>  
 <span data-ttu-id="d527b-112">有兩個機制可檢視資料層應用程式 (DAC) 封裝的內容。</span><span class="sxs-lookup"><span data-stu-id="d527b-112">There are two mechanisms for viewing the contents of a data-tier application (DAC) package.</span></span> <span data-ttu-id="d527b-113">您可以在 SQL Server Developer Tools 中將 DAC 封裝匯入 DAC 專案。</span><span class="sxs-lookup"><span data-stu-id="d527b-113">You can import the DAC package to a DAC project in SQL Server Developer Tools.</span></span> <span data-ttu-id="d527b-114">您可以將封裝的內容解除封裝到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d527b-114">You can unpack the contents of the package to a folder.</span></span>  
  
 <span data-ttu-id="d527b-115">**在 SQL Server Developer Tools 中檢視 DAC**</span><span class="sxs-lookup"><span data-stu-id="d527b-115">**View a DAC in SQL Server Developer Tools**</span></span>  
  
1.  <span data-ttu-id="d527b-116">開啟 [檔案]  功能表，選取 [開新檔案]  ，然後選取 [專案...]  。</span><span class="sxs-lookup"><span data-stu-id="d527b-116">Open the **File** menu, select **New**, and then select **Project...**.</span></span>  
  
2.  <span data-ttu-id="d527b-117">選取 **[SQL Server]** 專案範本，並指定 **[名稱]** 、 **[位置]** 及 **[方案名稱]** 。</span><span class="sxs-lookup"><span data-stu-id="d527b-117">Select the **SQL Server** project template, and specify a **Name**, **Location**, and **Solution name**.</span></span>  
  
3.  <span data-ttu-id="d527b-118">在 [方案總管]  中，以滑鼠右鍵按一下專案節點，然後選取 [屬性...]  。</span><span class="sxs-lookup"><span data-stu-id="d527b-118">In **Solution Explorer**, right click the project node and select **Properties...**.</span></span>  
  
4.  <span data-ttu-id="d527b-119">在 [專案設定]  索引標籤的 [輸出類型]  區段中，選取 [資料層應用程式 (.dacpac 檔案)]  核取方塊，然後關閉屬性對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d527b-119">On the **Project Settings** tab, in the **Output Types** section, select the **Data-tier Application (.dacpac File)** check box, and then close the properties dialog.</span></span>  
  
5.  <span data-ttu-id="d527b-120">在 [方案總管]  中，以滑鼠右鍵按一下專案節點，然後選取 [匯入資料層應用程式...]  。</span><span class="sxs-lookup"><span data-stu-id="d527b-120">In **Solution Explorer**, right click the project node and select **Import Data-tier Application...**.</span></span>  
  
6.  <span data-ttu-id="d527b-121">使用方案總管  開啟 DAC 中的所有檔案，例如伺服器選取原則和部署前後指令碼。</span><span class="sxs-lookup"><span data-stu-id="d527b-121">Use **Solution Explorer** to open all of the files in the DAC, such as the server selection policy and the pre- and post-deployment scripts.</span></span>  
  
7.  <span data-ttu-id="d527b-122">使用 **[結構描述檢視]** 檢閱結構描述中的所有物件，特別是檢閱函數或預存程序這類物件中的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="d527b-122">Use the **Schema View** to review all of the objects in the schema, particularly reviewing the code in objects such as functions or stored procedures.</span></span>  
  
 <span data-ttu-id="d527b-123">**檢視資料夾中的 DAC**</span><span class="sxs-lookup"><span data-stu-id="d527b-123">**View a DAC in a Folder**</span></span>  
  
-   <span data-ttu-id="d527b-124">遵循 [Unpack a DAC Package](unpack-a-dac-package.md)中的指示，將 DAC 封裝解壓縮至資料夾。</span><span class="sxs-lookup"><span data-stu-id="d527b-124">Unpack the DAC package into a folder by following the instructions in [Unpack a DAC Package](unpack-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="d527b-125">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的 [ [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器] 中開啟 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]指令碼以檢視其內容。</span><span class="sxs-lookup"><span data-stu-id="d527b-125">View the contents of the [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts by opening them in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="d527b-126">使用記事本這類工具檢視文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="d527b-126">View the contents of the text files in tools such as notepad.</span></span>  
  
##  <a name="view-database-changes"></a><a name="ViewDBChanges"></a> <span data-ttu-id="d527b-127">檢視資料庫變更</span><span class="sxs-lookup"><span data-stu-id="d527b-127">View Database Changes</span></span>  
 <span data-ttu-id="d527b-128">將 DAC 的目前版本部署至實際執行環境之後，直接對相關聯資料庫進行的變更可能會與新版 DAC 中所定義的結構描述衝突。</span><span class="sxs-lookup"><span data-stu-id="d527b-128">After the current version of a DAC was deployed to production, changes may have been made directly to the associated database that might conflict with the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="d527b-129">升級至新版 DAC 之前，請確認是否已經對資料庫進行這類變更。</span><span class="sxs-lookup"><span data-stu-id="d527b-129">Before upgrading to a new version of the DAC, check to see if such changes have been made to the database.</span></span>  
  
 <span data-ttu-id="d527b-130">**使用精靈檢視資料庫變更**</span><span class="sxs-lookup"><span data-stu-id="d527b-130">**View Database Changes by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="d527b-131">執行 [升級資料層應用程式精靈]  ，同時指定目前部署的 DAC 以及含有新版 DAC 的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="d527b-131">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="d527b-132">在 **[偵測變更]** 頁面上，檢閱已對資料庫進行之變更的報表。</span><span class="sxs-lookup"><span data-stu-id="d527b-132">On the **Detect Change** page, review the report of the changes that have been made to the database.</span></span>  
  
3.  <span data-ttu-id="d527b-133">如果您不想要繼續升級，請選取 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="d527b-133">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="d527b-134">如需使用精靈的詳細資訊，請參閱 [升級資料層應用程式](upgrade-a-data-tier-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d527b-134">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
### <a name="view-database-changes-by-using-powershell"></a><span data-ttu-id="d527b-135">使用 PowerShell 檢視資料庫變更</span><span class="sxs-lookup"><span data-stu-id="d527b-135">View Database Changes by Using PowerShell</span></span>
  
1.  <span data-ttu-id="d527b-136">建立 SMO Server 物件，並將它設定為包含要檢視之 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d527b-136">Create a SMO Server object and set it to the instance that contains the DAC to be viewed.</span></span>  
  
2.  <span data-ttu-id="d527b-137">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d527b-137">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="d527b-138">指定變數中的 DAC 名稱。</span><span class="sxs-lookup"><span data-stu-id="d527b-138">Specify the DAC name in a variable.</span></span>  
  
4.  <span data-ttu-id="d527b-139">使用 `GetDatabaseChanges()` 方法擷取 `ChangeResults` 物件，並將該物件以管道傳送至文字檔以產生新的、已刪除和已變更之物件的簡單報表。</span><span class="sxs-lookup"><span data-stu-id="d527b-139">Use the `GetDatabaseChanges()` method to retrieve a `ChangeResults` object, and pipe the object to a text file to generate a simple report of new, deleted, and changed objects.</span></span>  
  
### <a name="view-database-changes-example-powershell"></a><span data-ttu-id="d527b-140">檢視資料庫變更範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d527b-140">View Database Changes Example (PowerShell)</span></span>
  
 <span data-ttu-id="d527b-141">下列範例報告在已部署的 DAC (名稱為 MyApplicaiton) 中所做的任何資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="d527b-141">The following example reports any database changes that have been made in a deployed DAC named MyApplicaiton.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the change list and save to file.  
$dacChanges = $dacstore.GetDatabaseChanges($dacName) | Out-File -Filepath C:\DACScripts\MyApplicationChanges.txt  
```  
  
##  <a name="view-upgrade-actions"></a><a name="ViewUpgradeActions"></a> <span data-ttu-id="d527b-142">檢視升級動作</span><span class="sxs-lookup"><span data-stu-id="d527b-142">View Upgrade Actions</span></span>  
 <span data-ttu-id="d527b-143">使用新版 DAC 封裝升級從舊版 DAC 封裝部署的 DAC 之前，可以產生一份報表，其中包含會在升級期間執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，然後檢閱這些陳述式。</span><span class="sxs-lookup"><span data-stu-id="d527b-143">Before using a new version of a DAC package to upgrade a DAC that was deployed from an earlier DAC package, you can generate a report that contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that will be run during the upgrade, and then review the statements.</span></span>  
  
 <span data-ttu-id="d527b-144">**使用精靈來報告升級動作**</span><span class="sxs-lookup"><span data-stu-id="d527b-144">**Report Upgrade Actions by Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="d527b-145">執行 [升級資料層應用程式精靈]\*\*\*\*，同時指定目前部署的 DAC 以及含有新版 DAC 的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="d527b-145">Run the **Upgrade Data-tier Application** wizard, specifying the currently deployed DAC and the DAC package containing the new version of the DAC.</span></span>  
  
2.  <span data-ttu-id="d527b-146">在 **[摘要]** 頁面上，檢閱升級動作的報表。</span><span class="sxs-lookup"><span data-stu-id="d527b-146">On the **Summary** page, review the report of the upgrade actions.</span></span>  
  
3.  <span data-ttu-id="d527b-147">如果您不想要繼續升級，請選取 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="d527b-147">Select **Cancel** if you do not want to continue with the upgrade.</span></span>  
  
4.  <span data-ttu-id="d527b-148">如需使用精靈的詳細資訊，請參閱 [升級資料層應用程式](upgrade-a-data-tier-application.md)。</span><span class="sxs-lookup"><span data-stu-id="d527b-148">For more information on using the wizard, see [Upgrade a Data-tier Application](upgrade-a-data-tier-application.md).</span></span>  
  
 <span data-ttu-id="d527b-149">**使用 PowerShell 來報告升級動作**</span><span class="sxs-lookup"><span data-stu-id="d527b-149">**Report Upgrade Actions by Using PowerShell**</span></span>  
  
1.  <span data-ttu-id="d527b-150">建立 SMO Server 物件，並將它設定為包含已部署之 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d527b-150">Create a SMO Server object and set it to the instance that contains the deployed DAC.</span></span>  
  
2.  <span data-ttu-id="d527b-151">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d527b-151">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="d527b-152">使用 `System.IO.File` 以載入 DAC 封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="d527b-152">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="d527b-153">指定變數中的 DAC 名稱。</span><span class="sxs-lookup"><span data-stu-id="d527b-153">Specify the DAC name in a variable.</span></span>  
  
5.  <span data-ttu-id="d527b-154">使用 `GetIncrementalUpgradeScript()` 方法以取得升級要執行的 Transact-SQL 陳述式清單，並將該清單以管道傳送至文字檔。</span><span class="sxs-lookup"><span data-stu-id="d527b-154">Use the `GetIncrementalUpgradeScript()` method to get a list of the Transact-SQL statements an upgrade would run, and pipe the list to a text file.</span></span>  
  
6.  <span data-ttu-id="d527b-155">關閉用來讀取 DAC 封裝檔案的檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="d527b-155">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="view-upgrade-actions-example-powershell"></a><span data-ttu-id="d527b-156">檢視升級動作範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="d527b-156">View Upgrade Actions Example (PowerShell)</span></span>
  
 <span data-ttu-id="d527b-157">下列範例報告 Transact-SQL 陳述式，可執行以將 DAC (名稱為 MyApplicaiton) 升級至 MyApplicationVNext.dacpac 檔案中所定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d527b-157">The following example reports the Transact-SQL statements that would be run to upgrading a DAC named MyApplicaiton to the schema defined in a MyApplicationVNext.dacpac file.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Specify the DAC instance name.  
$dacName  = "MyApplication"  
  
## Generate the upgrade script and save to file.  
$dacstore.GetIncrementalUpgradeScript($dacName, $dacType) | Out-File -Filepath C:\DACScripts\MyApplicationUpgrade.sql  
  
## Close the filestream to the new DAC package.  
$fileStream.Close()  
```  
  
##  <a name="compare-dacs"></a><a name="CompareDACs"></a><span data-ttu-id="d527b-158">比較 Dac</span><span class="sxs-lookup"><span data-stu-id="d527b-158">Compare DACs</span></span>  
 <span data-ttu-id="d527b-159">在升級 DAC 之前，最好先檢閱目前 DAC 與新 DAC 之間的資料庫和執行個體層級物件的差異。</span><span class="sxs-lookup"><span data-stu-id="d527b-159">Before upgrading a DAC, it is a good practice to review the differences in the database and instance-level objects between the current and new DACs.</span></span> <span data-ttu-id="d527b-160">如果您沒有目前 DAC 封裝的複本，您可以從目前的資料庫擷取封裝。</span><span class="sxs-lookup"><span data-stu-id="d527b-160">If you do not have a copy of the package for the current DAC, you can extract a package from the current database.</span></span>  
  
 <span data-ttu-id="d527b-161">如果您在 SQL Server Developer Tools 中將這兩個 DAC 封裝匯入至 DAC 專案，則可以使用結構描述比較工具來分析這兩個 DAC 的差異。</span><span class="sxs-lookup"><span data-stu-id="d527b-161">If you import both DAC packages into DAC projects in SQL Server Developer Tools, you can use the Schema Compare tool to analyze the differences between the two DACs.</span></span>  
  
 <span data-ttu-id="d527b-162">您也可以將 DAC 解除封裝至不同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d527b-162">Alternatively, unpack the DACs into separate folders.</span></span> <span data-ttu-id="d527b-163">然後您可以使用差異工具 (如 WinDiff 公用程式) 來分析差異。</span><span class="sxs-lookup"><span data-stu-id="d527b-163">You can then use a difference tool, such as the WinDiff utility, to analyze the differences.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d527b-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d527b-164">See Also</span></span>  
 <span data-ttu-id="d527b-165">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d527b-165">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="d527b-166">[部署資料層應用程式](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="d527b-166">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="d527b-167">升級資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="d527b-167">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
