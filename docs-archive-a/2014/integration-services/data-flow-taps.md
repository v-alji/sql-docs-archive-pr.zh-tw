---
title: 資料流程分流 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 053b34add45354d0df71fa73a72f8786cc706d15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688078"
---
# <a name="data-flow-taps"></a><span data-ttu-id="e9411-102">資料流程點選</span><span class="sxs-lookup"><span data-stu-id="e9411-102">Data Flow Taps</span></span>
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] <span data-ttu-id="e9411-103">導入了一項新功能，可讓您在執行階段於封裝的資料流程路徑上加入資料點選，然後從資料點選將輸出導向至外部檔案。</span><span class="sxs-lookup"><span data-stu-id="e9411-103">introduces a new feature that allows you to add a data tap on a data flow path of a package at runtime and direct the output from the data tap to an external file.</span></span> <span data-ttu-id="e9411-104">若要使用此功能，您必須使用專案部署模型將 SSIS 專案部署至 SSIS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e9411-104">To use this feature, you must deploy your SSIS project using the project deployment model to an SSIS Server.</span></span> <span data-ttu-id="e9411-105">將封裝部署至伺服器之後，您需要對 SSISDB 資料庫執行 T-SQL 指令碼先加入資料點選，然後再執行該封裝。</span><span class="sxs-lookup"><span data-stu-id="e9411-105">After you deploy the package to the server, you need to execute T-SQL scripts against the SSISDB database to add data taps before executing the package.</span></span> <span data-ttu-id="e9411-106">範例狀況如下：</span><span class="sxs-lookup"><span data-stu-id="e9411-106">Here is a sample scenario:</span></span>  
  
1.  <span data-ttu-id="e9411-107">使用 [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) 預存程序建立封裝的執行執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9411-107">Create an execution instance of a package by using the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) stored procedure.</span></span>  
  
2.  <span data-ttu-id="e9411-108">使用 [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) 或 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) 預存程序加入資料點選。</span><span class="sxs-lookup"><span data-stu-id="e9411-108">Add a data tap by using either [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) or [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid) stored procedure.</span></span>  
  
3.  <span data-ttu-id="e9411-109">使用 [catalog.start_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) 啟動封裝的執行執行個體。</span><span class="sxs-lookup"><span data-stu-id="e9411-109">Start the execution instance of the package by using the [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).</span></span>  
  
 <span data-ttu-id="e9411-110">以下是執行上述狀況各個步驟的範例 SQL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="e9411-110">Here is a sample SQL script that performs the steps described in the above scenario:</span></span>  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 <span data-ttu-id="e9411-111">create_execution 預存程序的資料夾名稱、專案名稱和封裝名稱參數對應到 Integration Services 目錄中的資料夾、專案和封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="e9411-111">The folder name, project name, and package name parameters of the create_execution stored procedure correspond to the folder, project, and package names in the Integration Services catalog.</span></span> <span data-ttu-id="e9411-112">您可以從 SQL Server Management Studio 取得 create_execution 呼叫所要使用的資料夾、專案和封裝名稱，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="e9411-112">You can get the folder, project, and package names to use in the create_execution call from the SQL Server Management Studio as shown in the following image.</span></span> <span data-ttu-id="e9411-113">如果您的 SSIS 專案沒有出現在此，表示您可能尚未將該專案部署至 SSIS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e9411-113">If you do not see your SSIS project here, you may not have deployed the project to SSIS server yet.</span></span> <span data-ttu-id="e9411-114">請在 Visual Studio 中以滑鼠右鍵按一下 SSIS 專案，然後按一下 [部署] 將專案部署至所需的 SSIS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e9411-114">Right-click on SSIS project in Visual Studio and click Deploy to deploy the project to the expected SSIS server.</span></span>  
  
 <span data-ttu-id="e9411-115">除了輸入 SQL 陳述式之外，執行下列步驟也可以產生執行封裝指令碼：</span><span class="sxs-lookup"><span data-stu-id="e9411-115">Instead of typing the SQL statements, you can generate the execute package script by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="e9411-116">以滑鼠右鍵按一下 [Package.dtsx]  ，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="e9411-116">Right-click **Package.dtsx** and click **Execute**.</span></span>  
  
2.  <span data-ttu-id="e9411-117">按一下 **[指令碼]** 工具列按鈕以產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="e9411-117">Click **Script** toolbar button to generate the script.</span></span>  
  
3.  <span data-ttu-id="e9411-118">接著，在 start_execution 呼叫前面加入 add_data_tap 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9411-118">Now, add the add_data_tap statement before the start_execution call.</span></span>  
  
 <span data-ttu-id="e9411-119">add_data_tap 預存程序的 task_package_path 參數對應到 Visual Studio 中，資料流程工作的 PackagePath 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9411-119">The task_package_path parameter of add_data_tap stored procedure corresponds to the PackagePath property of the data flow task in Visual Studio.</span></span> <span data-ttu-id="e9411-120">在 Visual Studio 中，以滑鼠右鍵按一下 [資料流程工作]  ，然後按一下 [屬性]  啟動 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e9411-120">In Visual Studio, right-click the **Data Flow Task**, and click **Properties** to launch the Properties window.</span></span>  <span data-ttu-id="e9411-121">請記下 **PackagePath** 屬性的值，其將做為 add_data_tap 預存程序呼叫的 task_package_path 參數值使用。</span><span class="sxs-lookup"><span data-stu-id="e9411-121">Note the value of the **PackagePath** property to use it as a value for the task_package_path parameter for add_data_tap stored procedure call.</span></span>  
  
 <span data-ttu-id="e9411-122">add_data_tap 預存程序的 dataflow_path_id_string 參數對應到您要在其上加入資料點選之資料流程路徑的 IdentificationString 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9411-122">The dataflow_path_id_string  parameter of add_data_tap stored procedure corresponds to the IdentificationString property of the data flow path to which you want to add a data tap.</span></span> <span data-ttu-id="e9411-123">若要取得 dataflow_path_id_string，請按一下資料流程路徑 (資料流程中位於工作之間的箭號)，並記下 [屬性] 視窗所示 **IdentificationString** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e9411-123">To get the dataflow_path_id_string, click the data flow path (arrow between tasks in the data flow), and note the value of the **IdentificationString** property in the Properties window.</span></span>  
  
 <span data-ttu-id="e9411-124">當執行指令碼時，輸出檔會儲存於 \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps 中。</span><span class="sxs-lookup"><span data-stu-id="e9411-124">When you execute the script, the output file is stored in \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps.</span></span> <span data-ttu-id="e9411-125">如果已有同名的檔案存在，則將建立附帶尾碼的新檔案 (例如：output[1].txt)。</span><span class="sxs-lookup"><span data-stu-id="e9411-125">If a file with the name already exists, a new file with a suffix (for example: output[1].txt)  is created.</span></span>  
  
 <span data-ttu-id="e9411-126">如先前所述，您也可以使用 [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)預存程序，而不是使用 add_data_tap 預存程序。</span><span class="sxs-lookup"><span data-stu-id="e9411-126">As mentioned earlier, you can also use [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)stored procedure instead of using add_data_tap stored procedure.</span></span> <span data-ttu-id="e9411-127">此預存程序接受資料流程工作的識別碼當做參數，而非 task_package_path。</span><span class="sxs-lookup"><span data-stu-id="e9411-127">This stored procedure takes the ID of data flow task as a parameter instead of task_package_path.</span></span> <span data-ttu-id="e9411-128">您可以從 Visual Studio 屬性視窗取得資料流程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e9411-128">You can get the ID of data flow task from the properties window in Visual Studio.</span></span>  
  
## <a name="removing-a-data-tap"></a><span data-ttu-id="e9411-129">移除資料點選</span><span class="sxs-lookup"><span data-stu-id="e9411-129">Removing a data tap</span></span>  
 <span data-ttu-id="e9411-130">您可以使用 [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) 預存程序，在啟動執行之前移除資料點選。</span><span class="sxs-lookup"><span data-stu-id="e9411-130">You can remove a data tap before starting the execution by using the [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) stored procedure.</span></span> <span data-ttu-id="e9411-131">此預存程序接受資料點選的識別碼當做參數，而識別碼可透過 add_data_tap 預存程序的輸出取得。</span><span class="sxs-lookup"><span data-stu-id="e9411-131">This stored procedure takes the ID of data tap as a parameter, which you can get as an output of the add_data_tap stored procedure.</span></span>  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a><span data-ttu-id="e9411-132">列出所有資料點選</span><span class="sxs-lookup"><span data-stu-id="e9411-132">Listing all data taps</span></span>  
 <span data-ttu-id="e9411-133">您也可以使用 catalog.execution_data_taps 檢視表，列出所有資料點選。</span><span class="sxs-lookup"><span data-stu-id="e9411-133">You can also list all the data taps by using the catalog.execution_data_taps view.</span></span> <span data-ttu-id="e9411-134">下列範例會擷取規格執行之執行個體 (識別碼：54) 的資料點選。</span><span class="sxs-lookup"><span data-stu-id="e9411-134">The following example extracts data taps for a specification execution instance (ID: 54).</span></span>  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a><span data-ttu-id="e9411-135">效能考量</span><span class="sxs-lookup"><span data-stu-id="e9411-135">Performance consideration</span></span>  
 <span data-ttu-id="e9411-136">啟用詳細資訊記錄層次和加入資料點選會致使資料整合方案執行更多 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="e9411-136">Enabling verbose logging level and adding data taps increase the I/O operations performed by your data integration solution.</span></span> <span data-ttu-id="e9411-137">因此，建議您只有在進行疑難排解時才加入資料點選。</span><span class="sxs-lookup"><span data-stu-id="e9411-137">Hence, we recommend that you add data taps only for troubleshooting purposes</span></span>  
  
## <a name="video"></a><span data-ttu-id="e9411-138">影片</span><span class="sxs-lookup"><span data-stu-id="e9411-138">Video</span></span>  
 <span data-ttu-id="e9411-139">這部 [TechNet 上的影片](https://technet.microsoft.com/sqlserver/dn600163) 示範了如何在 SQL Server 2012 SSISDB 目錄中加入/使用資料點選，協助您以程式設計方式對封裝進行偵錯及在執行階段擷取部分結果。</span><span class="sxs-lookup"><span data-stu-id="e9411-139">This [video on TechNet](https://technet.microsoft.com/sqlserver/dn600163) demonstrates how to add/use data taps in SQL Server 2012 SSISDB catalog that help with debugging packages programmatically and capturing the partial results at the runtime.</span></span> <span data-ttu-id="e9411-140">該影片也將討論如何列出/移除這些資料點選，以及在 SSIS 封裝中使用資料點選的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="e9411-140">It also discusses how to list/ remove these data taps and best practices for using data taps in SSIS packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e9411-141">相關工作</span><span class="sxs-lookup"><span data-stu-id="e9411-141">Related Tasks</span></span>  
 [<span data-ttu-id="e9411-142">偵錯資料流程</span><span class="sxs-lookup"><span data-stu-id="e9411-142">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="e9411-143">套件執行的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="e9411-143">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
