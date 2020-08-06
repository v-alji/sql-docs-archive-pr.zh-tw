---
title: 使用預存程式部署及執行 SSIS 套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1570207dca6e944b54c553a1d83256d8f4fa3244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707686"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a><span data-ttu-id="f4a85-102">使用預存程序部署及執行 SSIS 封裝</span><span class="sxs-lookup"><span data-stu-id="f4a85-102">Deploy and Execute SSIS Packages using Stored Procedures</span></span>
  <span data-ttu-id="f4a85-103">當您設定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案來使用專案部署模型時，您可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 目錄中的預存程序來部署專案及執行封裝。</span><span class="sxs-lookup"><span data-stu-id="f4a85-103">When you configure an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to use the project deployment model, you can use stored procedures in the [!INCLUDE[ssIS](../includes/ssis-md.md)] catalog to deploy the project and execute the packages.</span></span> <span data-ttu-id="f4a85-104">如需有關專案部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f4a85-104">For information about the project deployment model, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="f4a85-105">您也可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 部署專案及執行封裝。</span><span class="sxs-lookup"><span data-stu-id="f4a85-105">You can also use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to deploy the project and execute the packages.</span></span> <span data-ttu-id="f4a85-106">如需詳細資訊，請參閱＜ **另請參閱** ＞一節中的主題。</span><span class="sxs-lookup"><span data-stu-id="f4a85-106">For more information, see the topics in the **See Also** section.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f4a85-107">您可以執行以下動作，輕鬆地針對底下程序中所列的預存程序產生 Transact-SQL 陳述式 (除了 catalog.deploy_project 以外)：</span><span class="sxs-lookup"><span data-stu-id="f4a85-107">You can easily generate the Transact-SQL statements for the stored procedures listed in the procedure below, with the exception of catalog.deploy_project, by doing the following:</span></span>  
> 
>  1.  <span data-ttu-id="f4a85-108">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，展開 [物件總管] 中的 **Integration Services 目錄** 節點，並導覽到您要執行的封裝。</span><span class="sxs-lookup"><span data-stu-id="f4a85-108">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** node in Object Explorer and navigate to the package you want to execute.</span></span>  
> 2.  <span data-ttu-id="f4a85-109">以滑鼠右鍵按一下封裝，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="f4a85-109">Right-click the package, and then click **Execute**.</span></span>  
> 3.  <span data-ttu-id="f4a85-110">請視需要在 **[進階]** 索引標籤中設定參數值、連接管理員屬性和選項，例如記錄層次。</span><span class="sxs-lookup"><span data-stu-id="f4a85-110">As needed, set parameters values, connection manager properties, and options in the **Advanced** tab such as the logging level.</span></span>  
> 
>      <span data-ttu-id="f4a85-111">如需有關記錄層級的詳細資訊，請參閱＜ [在 SSIS 伺服器上啟用封裝執行的記錄功能](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f4a85-111">For more information about logging levels, see [Enable Logging for Package Execution on the SSIS Server](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).</span></span>  
> 4.  <span data-ttu-id="f4a85-112">在按一下 **[確定]** 執行封裝之前，請按一下 **[指令碼]**。</span><span class="sxs-lookup"><span data-stu-id="f4a85-112">Before clicking **OK** to execute the package, click **Script**.</span></span> <span data-ttu-id="f4a85-113">Transact-SQL 會出現在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的 [查詢編輯器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="f4a85-113">The Transact-SQL appears in a Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a><span data-ttu-id="f4a85-114">若要使用預存程序部署及執行封裝</span><span class="sxs-lookup"><span data-stu-id="f4a85-114">To deploy and execute a package using stored procedures</span></span>  
  
1.  <span data-ttu-id="f4a85-115">呼叫 [catalog.deploy_project &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) 將包含封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f4a85-115">Call [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) to deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="f4a85-116">若要取得專案部署檔案的二進位內容 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ，請針對\* \@ project_stream\*參數，搭配 OPENROWSET 函數和 BULK 資料列集提供者使用 SELECT 語句。</span><span class="sxs-lookup"><span data-stu-id="f4a85-116">To retrieve the binary contents of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project deployment file, for the *\@project_stream* parameter, use a SELECT statement with the OPENROWSET function and the BULK rowset provider.</span></span> <span data-ttu-id="f4a85-117">BULK 資料列集提供者可讓您從檔案讀取資料。</span><span class="sxs-lookup"><span data-stu-id="f4a85-117">The BULK rowset provider enables you to read data from a file.</span></span> <span data-ttu-id="f4a85-118">BULK 資料列集提供者的 SINGLE_BLOB 引數會傳回資料檔的內容當做類型為 varbinary(max) 的單一資料列、單一資料行資料列集。</span><span class="sxs-lookup"><span data-stu-id="f4a85-118">The SINGLE_BLOB argument for the BULK rowset provider returns the contents of the data file as a single-row, single-column rowset of type varbinary(max).</span></span> <span data-ttu-id="f4a85-119">如需詳細資訊，請參閱 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f4a85-119">For more information, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
     <span data-ttu-id="f4a85-120">在下列範例中，SSISPackages_ProjectDeployment 專案會部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器上的 [SSIS 封裝] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4a85-120">In the following example, the SSISPackages_ProjectDeployment project is deployed to the SSIS Packages folder on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="f4a85-121">二進位資料會從專案檔讀取 (SSISPackage_ProjectDeployment. .ispac) ，並儲存在 Varbinary (max) 類型的\* \@ ProjectBinary\*參數中。</span><span class="sxs-lookup"><span data-stu-id="f4a85-121">The binary data is read from the project file (SSISPackage_ProjectDeployment.ispac) and is stored in the *\@ProjectBinary* parameter of type varbinary(max).</span></span> <span data-ttu-id="f4a85-122">\* \@ ProjectBinary*參數值會指派給* \@ project_stream\*參數。</span><span class="sxs-lookup"><span data-stu-id="f4a85-122">The *\@ProjectBinary* parameter value is assigned to the *\@project_stream* parameter.</span></span>  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  <span data-ttu-id="f4a85-123">呼叫 [catalog.create_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) 來建立封裝執行的執行個體，並選擇性地呼叫 [catalog.set_execution_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) 來設定執行階段參數值。</span><span class="sxs-lookup"><span data-stu-id="f4a85-123">Call [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) to create an instance of the package execution, and optionally call [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) to set runtime parameter values.</span></span>  
  
     <span data-ttu-id="f4a85-124">在下列範例中，catalog.create_execution 會針對 SSISPackage_ProjectDeployment 專案中包含的 package.dtsx 建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="f4a85-124">In the following example, catalog.create_execution creates an instance of execution for package.dtsx that is contained in the SSISPackage_ProjectDeployment project.</span></span> <span data-ttu-id="f4a85-125">此專案位於 SSIS 封裝資料夾內。</span><span class="sxs-lookup"><span data-stu-id="f4a85-125">The project is located in the SSIS Packages folder.</span></span> <span data-ttu-id="f4a85-126">此預存程序傳回的 execution_id 是用在 catalog.set_execution_parameter_value 的呼叫中。</span><span class="sxs-lookup"><span data-stu-id="f4a85-126">The execution_id returned by the stored procedure is used in the call to catalog.set_execution_parameter_value.</span></span> <span data-ttu-id="f4a85-127">此第二個預存程序會將 LOGGING_LEVEL 參數設定為 3 (詳細資訊記錄)，並將名為 Parameter1 的封裝參數設定為 1 的值。</span><span class="sxs-lookup"><span data-stu-id="f4a85-127">This second stored procedure sets the LOGGING_LEVEL parameter to 3 (verbose logging) and sets a package parameter named Parameter1 to a value of 1.</span></span>  
  
     <span data-ttu-id="f4a85-128">對於參數 (例如 LOGGING_LEVEL)，object_type 的值為 50。</span><span class="sxs-lookup"><span data-stu-id="f4a85-128">For parameters such as LOGGING_LEVEL the object_type value is 50.</span></span> <span data-ttu-id="f4a85-129">若為封裝參數，object_type 的值為 30。</span><span class="sxs-lookup"><span data-stu-id="f4a85-129">For package parameters the object_type value is 30.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  <span data-ttu-id="f4a85-130">呼叫 [catalog.start_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) 來執行封裝。</span><span class="sxs-lookup"><span data-stu-id="f4a85-130">Call [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) to execute the package.</span></span>  
  
     <span data-ttu-id="f4a85-131">在下列範例中，catalog.start_execution 的呼叫會加入至 Transact-SQL 來開始執行封裝。</span><span class="sxs-lookup"><span data-stu-id="f4a85-131">In the following example, a call to catalog.start_execution is added to the Transact-SQL to start the package execution.</span></span> <span data-ttu-id="f4a85-132">使用 catalog.create_execution 預存程序所傳回的 execution_id。</span><span class="sxs-lookup"><span data-stu-id="f4a85-132">The execution_id returned by the catalog.create_execution stored procedure is used.</span></span>  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a><span data-ttu-id="f4a85-133">若要使用預存程序在不同伺服器之間部署專案</span><span class="sxs-lookup"><span data-stu-id="f4a85-133">To deploy a project from server to server using stored procedures</span></span>  
 <span data-ttu-id="f4a85-134">您可以使用 [catalog.get_project &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) 和 [catalog.deploy_project &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) 預存程序在不同伺服器之間部署專案。</span><span class="sxs-lookup"><span data-stu-id="f4a85-134">You can deploy a project from server to server by using the [catalog.get_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) and [catalog.deploy_project &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) stored procedures.</span></span>  
  
 <span data-ttu-id="f4a85-135">在執行預存程序之前，您必須執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="f4a85-135">You need to do the following before running the stored procedures.</span></span>  
  
-   <span data-ttu-id="f4a85-136">建立連結的伺服器物件。</span><span class="sxs-lookup"><span data-stu-id="f4a85-136">Create a linked server object.</span></span> <span data-ttu-id="f4a85-137">如需詳細資訊，請參閱[建立連結的伺服器 &#40;SQL Server Database Engine&#41;](../database-engine/sql-server-database-engine-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f4a85-137">For more information, see [Create Linked Servers &#40;SQL Server Database Engine&#41;](../database-engine/sql-server-database-engine-overview.md).</span></span>  
  
     <span data-ttu-id="f4a85-138">在 **[連結的伺服器屬性]** 對話方塊的 **[伺服器選項]** 頁面上，將 **[RPC]** 和 **[RPC 輸出]** 設定為 **[True]**。</span><span class="sxs-lookup"><span data-stu-id="f4a85-138">On the **Server Options** page of the **Linked Server Properties** dialog box, set **RPC** and **RPC Out** to **True**.</span></span> <span data-ttu-id="f4a85-139">此外，也將 **[啟用 RPC 的分散式交易促銷]** 設定為 **[False]**。</span><span class="sxs-lookup"><span data-stu-id="f4a85-139">Also, set **Enable Promotion of Distributed Transactions for RPC** to **False**.</span></span>  
  
-   <span data-ttu-id="f4a85-140">若要針對您為連結的伺服器選取的提供者啟用動態參數，請在物件總管中展開 [連結的伺服器]\*\*\*\* 下方的 [提供者]\*\*\*\* 節點，以滑鼠右鍵按一下此提供者，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4a85-140">Enable dynamic parameters for the provider you selected for the linked server, by expanding the **Providers** node under **Linked Servers** in Object Explorer, right-clicking the provider, and then clicking **Properties**.</span></span> <span data-ttu-id="f4a85-141">選取 **[動態參數]** 旁邊的 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="f4a85-141">Select **Enable** next to **Dynamic parameter.**</span></span>  
  
-   <span data-ttu-id="f4a85-142">確認兩部伺服器上都已啟動分散式交易協調器 (DTC)。</span><span class="sxs-lookup"><span data-stu-id="f4a85-142">Confirm that the Distributed Transaction Coordinator (DTC) is started on both servers.</span></span>  
  
 <span data-ttu-id="f4a85-143">呼叫 catalog.get_project 來傳回專案的二進位內容，然後呼叫 catalog.deploy_project。</span><span class="sxs-lookup"><span data-stu-id="f4a85-143">Call catalog.get_project to return the binary for the project, and then call catalog.deploy_project.</span></span> <span data-ttu-id="f4a85-144">catalog.get_project 傳回的值會插入 varbinary(max) 類型的資料表變數中。</span><span class="sxs-lookup"><span data-stu-id="f4a85-144">The value returned by catalog.get_project is inserted into a table variable of type varbinary(max).</span></span> <span data-ttu-id="f4a85-145">連結的伺服器無法傳回屬於 varbinary(max) 的結果。</span><span class="sxs-lookup"><span data-stu-id="f4a85-145">The linked server can't return results that are varbinary(max).</span></span>  
  
 <span data-ttu-id="f4a85-146">在下列範例中，catalog.get_project 會針對連結的伺服器上的 SSISPackages 專案傳回二進位內容。</span><span class="sxs-lookup"><span data-stu-id="f4a85-146">In the following example, catalog.get_project returns a binary for the SSISPackages project on the linked server.</span></span> <span data-ttu-id="f4a85-147">catalog.deploy_project 會將專案部署到本機伺服器的 DestFolder 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4a85-147">The catalog.deploy_project deploys the project to the local server, to the folder named DestFolder.</span></span>  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4a85-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4a85-148">See Also</span></span>  
 <span data-ttu-id="f4a85-149">[將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4a85-149">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 <span data-ttu-id="f4a85-150">[在 SQL Server Data Tools 中執行封裝](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span><span class="sxs-lookup"><span data-stu-id="f4a85-150">[Run a Package in SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md) </span></span>  
 [<span data-ttu-id="f4a85-151">使用 SQL Server Management Studio 在 SSIS 伺服器上執行套件</span><span class="sxs-lookup"><span data-stu-id="f4a85-151">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
