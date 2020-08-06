---
title: dtexec 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7b6867fa-1039-49b3-90fb-85b84678a612
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45820aa673f31ae9cea7d1f2f4e8b61d63b8670c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703165"
---
# <a name="dtexec-utility"></a><span data-ttu-id="05039-102">dtexec 公用程式</span><span class="sxs-lookup"><span data-stu-id="05039-102">dtexec Utility</span></span>
  <span data-ttu-id="05039-103">`dtexec`命令提示字元公用程式可用來設定及執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-103">The `dtexec` command prompt utility is used to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="05039-104">`dtexec` 公用程式可存取所有封裝組態及執行功能，例如參數、連接、屬性、變數、記錄與進度指標。</span><span class="sxs-lookup"><span data-stu-id="05039-104">The `dtexec` utility provides access to all the package configuration and execution features, such as parameters, connections, properties, variables, logging, and progress indicators.</span></span> <span data-ttu-id="05039-105">`dtexec`公用程式可讓您從下列來源載入封裝： [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器、.ispac 專案檔案、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區和檔案系統。</span><span class="sxs-lookup"><span data-stu-id="05039-105">The `dtexec` utility lets you load packages from these sources: the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, an .ispac project file, a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05039-106">當您使用 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] 隨附的 `dtexec` 公用程式版本執行 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 或 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 封裝時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會暫時將封裝升級為 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05039-106">When you use the version of the `dtexec` utility that comes with [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] to run a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or a [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] temporarily upgrades the package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].</span></span> <span data-ttu-id="05039-107">但您無法使用 `dtexec` 公用程式儲存這些升級的變更。</span><span class="sxs-lookup"><span data-stu-id="05039-107">However, you cannot use the `dtexec` utility to save these upgraded changes.</span></span> <span data-ttu-id="05039-108">如需如何將封裝永久升級至的詳細資訊 [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] ，請參閱[升級 Integration Services 套件](../install-windows/upgrade-integration-services-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-108">For more information about how to permanently upgrade a package to [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)], see [Upgrade Integration Services Packages](../install-windows/upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="05039-109">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="05039-109">This topic includes the following sections:</span></span>  
  
-   [<span data-ttu-id="05039-110">Integration Services 伺服器及專案檔案</span><span class="sxs-lookup"><span data-stu-id="05039-110">Integration Services Server and Project File</span></span>](#server)  
  
-   [<span data-ttu-id="05039-111">64 位元電腦上的安裝考量</span><span class="sxs-lookup"><span data-stu-id="05039-111">Installation Considerations on 64-bit Computers</span></span>](#bit)  
  
-   [<span data-ttu-id="05039-112">擁有並存安裝之電腦的考量</span><span class="sxs-lookup"><span data-stu-id="05039-112">Considerations on Computers with Side-by-Side Installations</span></span>](#side)  
  
-   [<span data-ttu-id="05039-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="05039-113">Phases of Execution</span></span>](#phases)  
  
-   [<span data-ttu-id="05039-114">傳回的結束碼</span><span class="sxs-lookup"><span data-stu-id="05039-114">Exit Codes Returned</span></span>](#exit)  
  
-   [<span data-ttu-id="05039-115">語法與規則</span><span class="sxs-lookup"><span data-stu-id="05039-115">Syntax Rules</span></span>](#syntaxRules)  
  
-   [<span data-ttu-id="05039-116">使用 xp_cmdshell 的 dtexec</span><span class="sxs-lookup"><span data-stu-id="05039-116">Using dtexec from the xp_cmdshell</span></span>](#cmdshell)  
  
-   [<span data-ttu-id="05039-117">語法</span><span class="sxs-lookup"><span data-stu-id="05039-117">Syntax</span></span>](#syntax)  
  
-   [<span data-ttu-id="05039-118">參數</span><span class="sxs-lookup"><span data-stu-id="05039-118">Parameters</span></span>](#parameter)  
  
-   [<span data-ttu-id="05039-119">備註</span><span class="sxs-lookup"><span data-stu-id="05039-119">Remarks</span></span>](#remark)  
  
-   [<span data-ttu-id="05039-120">範例</span><span class="sxs-lookup"><span data-stu-id="05039-120">Examples</span></span>](#example)  
  
##  <a name="integration-services-server-and-project-file"></a><a name="server"></a> <span data-ttu-id="05039-121">Integration Services 伺服器及專案檔案</span><span class="sxs-lookup"><span data-stu-id="05039-121">Integration Services Server and Project File</span></span>  
 <span data-ttu-id="05039-122">當您使用在 `dtexec` 伺服器上執行封裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 時，會 `dtexec` 呼叫[目錄。 create_execution &#40;ssisdb 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database)，[目錄。 set_execution_parameter_value &#40;ssisdb](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)資料庫&#41;和[目錄。 start_execution &#40;ssisdb 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)預存程式來建立執行、設定參數值，以及開始執行。</span><span class="sxs-lookup"><span data-stu-id="05039-122">When you use `dtexec` to run packages on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, `dtexec` calls the [catalog.create_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) and [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) stored procedures to create an execution, set parameter values and start the execution.</span></span> <span data-ttu-id="05039-123">所有執行記錄都可以從伺服器的相關檢視中查看，或透過 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中提供的標準報表查看。</span><span class="sxs-lookup"><span data-stu-id="05039-123">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="05039-124">如需報表的詳細資訊，請參閱 [Integration Services 伺服器的報表](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-124">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="05039-125">以下是執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上的封裝範例。</span><span class="sxs-lookup"><span data-stu-id="05039-125">The following is an example of executing a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
DTExec /ISSERVER "\SSISDB\folderB\Integration Services Project17\Package.dtsx" /SERVER "." /Envreference 2 /Par "$Project::ProjectParameter(Int32)";1 /Par "Parameter(Int32)";21 /Par "CM.sqlcldb2.SSIS_repro.InitialCatalog";ssisdb /Par "$ServerOption::SYNCHRONIZED(Boolean)";True  
```  
  
 <span data-ttu-id="05039-126">當您使用 `dtexec` 從 .ispac 專案檔案行封裝時，相關的選項為：/Proj[ect] 和 /Pack[age]，這些選項用來指定專案路徑及封裝資料流名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-126">When you use `dtexec` to run a package from the .ispac project file, the related options are: /Proj[ect] and /Pack[age] that are used to specify the project path and package stream name.</span></span> <span data-ttu-id="05039-127">當您從 **執行** [Integration Services 專案轉換精靈] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]，以便將專案轉換至專案部署模型時，此精靈會產生一個 .ispac 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-127">When you convert a project to the project deployment model by running the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], the wizard generates an .ispac projec file.</span></span> <span data-ttu-id="05039-128">如需詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-128">For more information, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="05039-129">您可以使用 `dtexec` 與協力廠商排程工具來排程部署到伺服器的封裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="05039-129">You can use `dtexec` with third-party scheduling tools to schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
##  <a name="installation-considerations-on-64-bit-computers"></a><a name="bit"></a> <span data-ttu-id="05039-130">64 位元電腦上的安裝考量</span><span class="sxs-lookup"><span data-stu-id="05039-130">Installation Considerations on 64-bit Computers</span></span>  
 <span data-ttu-id="05039-131">在 64 位元電腦上，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會安裝 64 位元版本的 `dtexec` 公用程式 (dtexec.exe)。</span><span class="sxs-lookup"><span data-stu-id="05039-131">On a 64-bit computer, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installs a 64-bit version of the `dtexec` utility (dtexec.exe).</span></span> <span data-ttu-id="05039-132">如果您必須用 32 位元模式執行特定封裝，必須安裝 32 位元版本的 `dtexec` 公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-132">If you have to run certain packages in 32-bit mode, you will have to install the 32-bit version of the `dtexec` utility.</span></span> <span data-ttu-id="05039-133">如果要安裝 32 位元版本的 `dtexec` 公用程式，必須在安裝期間選取用戶端工具或 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="05039-133">To install the 32-bit version of the `dtexec` utility, you must select either Client Tools or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] during setup.</span></span>  
  
 <span data-ttu-id="05039-134">根據預設，同時安裝了 64 位元和 32 位元版之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 命令提示字元公用程式的 64 位元電腦將會在命令提示字元上執行 32 位元版本。</span><span class="sxs-lookup"><span data-stu-id="05039-134">By default, a 64-bit computer that has both the 64-bit and 32-bit versions of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] command prompt utility installed will run the 32-bit version at the command prompt.</span></span> <span data-ttu-id="05039-135">執行 32 位元版本是因為 32 位元版本的目錄路徑在 PATH 環境變數中會出現在 64 位元版本的目錄路徑前面</span><span class="sxs-lookup"><span data-stu-id="05039-135">The 32-bit version runs because the directory path for the 32-bit version appears in the PATH environment variable before the directory path for the 64-bit version.</span></span> <span data-ttu-id="05039-136">(一般而言，32 位元的目錄路徑是 *\<drive>* :\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn，而 64 位元的目錄路徑是 *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn。)</span><span class="sxs-lookup"><span data-stu-id="05039-136">(Typically, the 32-bit directory path is *\<drive>*:\Program Files(x86)\Microsoft SQL Server\110\DTS\Binn, while the 64-bit directory path is *\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05039-137">如果您使用 SQL Server Agent 執行此公用程式，SQL Server Agent 會自動使用 64 位元版的公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-137">If you use SQL Server Agent to run the utility, SQL Server Agent automatically uses the 64-bit version of the utility.</span></span> <span data-ttu-id="05039-138">SQL Server Agent 會使用此登錄 (而不是 PATH 環境變數) 來尋找此公用程式的正確可執行檔。</span><span class="sxs-lookup"><span data-stu-id="05039-138">SQL Server Agent uses the registry, not the PATH environment variable, to locate the correct executable for the utility.</span></span>  
  
 <span data-ttu-id="05039-139">若要確保您可在命令提示字元上執行 64 位元版的公用程式，您可以採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="05039-139">To ensure that you run the 64-bit version of the utility at the command prompt, you can take one of the following actions:</span></span>  
  
-   <span data-ttu-id="05039-140">開啟 [命令提示字元] 視窗，然後將目錄切換到包含 64 位元版公用程式的目錄 ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn)，再從該位置執行公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-140">Open a Command Prompt window, change to the directory that contains the 64-bit version of the utility (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn), and then run the utility from that location.</span></span>  
  
-   <span data-ttu-id="05039-141">在命令提示字元上，輸入 64 位元版公用程式的完整路徑 ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn)，以執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-141">At the command prompt, run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) to the 64-bit version of the utility.</span></span>  
  
-   <span data-ttu-id="05039-142">在 PATH 環境變數中將 64 位元路徑 ( *\<drive>* :\Program Files\Microsoft SQL Server\110\DTS\Binn) 置於 32 位元路徑 ( *\<drive>* :\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) 之前，可久變更 PATH 環境變數中的路徑順序。</span><span class="sxs-lookup"><span data-stu-id="05039-142">Permanently change the order of the paths in the PATH environment variable by placing the 64-bit path (*\<drive>*:\Program Files\Microsoft SQL Server\110\DTS\Binn) before the 32-bit path (*\<drive>*:\ Program Files(x86)\Microsoft SQL Server\110\DTS\Binn) in the variable.</span></span>  
  
##  <a name="considerations-on-computers-with-side-by-side-installations"></a><a name="side"></a> <span data-ttu-id="05039-143">擁有並存安裝之電腦的考量</span><span class="sxs-lookup"><span data-stu-id="05039-143">Considerations on Computers with Side-by-Side Installations</span></span>  
 <span data-ttu-id="05039-144">如果 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 安裝在已安裝 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 或 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 的電腦上，則會安裝多個版本的 `dtexec` 公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-144">When [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] is installed on a machine that has [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] installed, multiple versions of the `dtexec` utility are installed.</span></span>  
  
 <span data-ttu-id="05039-145">為確保執行正確的公用程式版本，請在命令提示字元中輸入完整路徑 ( *\<drive>* :\Program Files\Microsoft SQL Server\\<版本\>\DTS\Binn) 來執行公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-145">To ensure that you run the correct version of the utility, at the command prompt run the utility by entering the full path (*\<drive>*:\Program Files\Microsoft SQL Server\\<version\>\DTS\Binn).</span></span>  
  
##  <a name="phases-of-execution"></a><a name="phases"></a> <span data-ttu-id="05039-146">執行階段</span><span class="sxs-lookup"><span data-stu-id="05039-146">Phases of Execution</span></span>  
 <span data-ttu-id="05039-147">這個公用程式有四個執行階段。</span><span class="sxs-lookup"><span data-stu-id="05039-147">The utility has four phases that it proceeds through as it executes.</span></span> <span data-ttu-id="05039-148">執行階段如下所示：</span><span class="sxs-lookup"><span data-stu-id="05039-148">The phases are as follows:</span></span>  
  
1.  <span data-ttu-id="05039-149">命令來源階段：命令提示字元讀取已指定的選項及引數清單。</span><span class="sxs-lookup"><span data-stu-id="05039-149">Command sourcing phase: The command prompt reads the list of options and arguments that have been specified.</span></span> <span data-ttu-id="05039-150">如果遇到了 **/?**</span><span class="sxs-lookup"><span data-stu-id="05039-150">All subsequent phases are skipped if a **/?**</span></span> <span data-ttu-id="05039-151">或 **/HELP** 選項，則會略過所有後續的階段。</span><span class="sxs-lookup"><span data-stu-id="05039-151">or **/HELP** option is encountered.</span></span>  
  
2.  <span data-ttu-id="05039-152">封裝載入階段： `/SQL` 已載入、 **/FILE**或選項所指定的封裝 `/DTS` 。</span><span class="sxs-lookup"><span data-stu-id="05039-152">Package load phase: The package specified by the `/SQL`, **/FILE**, or `/DTS` option is loaded.</span></span>  
  
3.  <span data-ttu-id="05039-153">設定階段：選項會依下列順序處理：</span><span class="sxs-lookup"><span data-stu-id="05039-153">Configuration phase: Options are processed in this order:</span></span>  
  
    -   <span data-ttu-id="05039-154">設定封裝旗標、變數和屬性的選項。</span><span class="sxs-lookup"><span data-stu-id="05039-154">Options that set package flags, variables, and properties.</span></span>  
  
    -   <span data-ttu-id="05039-155">確認封裝的版本和建置的選項。</span><span class="sxs-lookup"><span data-stu-id="05039-155">Options that verify the package version and build.</span></span>  
  
    -   <span data-ttu-id="05039-156">設定公用程式之執行階段行為的選項，例如報告。</span><span class="sxs-lookup"><span data-stu-id="05039-156">Options that configure the run-time behavior of the utility, such as reporting.</span></span>  
  
4.  <span data-ttu-id="05039-157">驗證及執行階段：執行套件，如有指定 **/VALIDATE** 選項，則只會驗證套件而不會執行套件。</span><span class="sxs-lookup"><span data-stu-id="05039-157">Validation and execution phase: The package is run, or validated without running if the **/VALIDATE** option was specified.</span></span>  
  
##  <a name="exit-codes-returned"></a><a name="exit"></a> <span data-ttu-id="05039-158">傳回的結束碼</span><span class="sxs-lookup"><span data-stu-id="05039-158">Exit Codes Returned</span></span>  
 <span data-ttu-id="05039-159">**從 dtexec 公用程式傳回的結束碼**</span><span class="sxs-lookup"><span data-stu-id="05039-159">**Exit codes returned from dtexec utility**</span></span>  
  
 <span data-ttu-id="05039-160">封裝執行期間，`dtexec` 可能會傳回結束碼。</span><span class="sxs-lookup"><span data-stu-id="05039-160">When a package runs, `dtexec` can return an exit code.</span></span> <span data-ttu-id="05039-161">結束碼可用來擴展 ERRORLEVEL 變數，讓您可以在批次檔內的條件陳述式或分支邏輯中測試此變數的值。</span><span class="sxs-lookup"><span data-stu-id="05039-161">The exit code is used to populate the ERRORLEVEL variable, the value of which can then be tested in conditional statements or branching logic within a batch file.</span></span> <span data-ttu-id="05039-162">下表列出 `dtexec` 公用程式結束時所能設定的值。</span><span class="sxs-lookup"><span data-stu-id="05039-162">The following table lists the values that the `dtexec` utility can set when exiting.</span></span>  
  
|<span data-ttu-id="05039-163">值</span><span class="sxs-lookup"><span data-stu-id="05039-163">Value</span></span>|<span data-ttu-id="05039-164">描述</span><span class="sxs-lookup"><span data-stu-id="05039-164">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05039-165">0</span><span class="sxs-lookup"><span data-stu-id="05039-165">0</span></span>|<span data-ttu-id="05039-166">順利執行封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-166">The package executed successfully.</span></span>|  
|<span data-ttu-id="05039-167">1</span><span class="sxs-lookup"><span data-stu-id="05039-167">1</span></span>|<span data-ttu-id="05039-168">封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-168">The package failed.</span></span>|  
|<span data-ttu-id="05039-169">3</span><span class="sxs-lookup"><span data-stu-id="05039-169">3</span></span>|<span data-ttu-id="05039-170">使用者取消封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-170">The package was canceled by the user.</span></span>|  
|<span data-ttu-id="05039-171">4</span><span class="sxs-lookup"><span data-stu-id="05039-171">4</span></span>|<span data-ttu-id="05039-172">公用程式找不到所要求的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-172">The utility was unable to locate the requested package.</span></span> <span data-ttu-id="05039-173">找不到這個封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-173">The package could not be found.</span></span>|  
|<span data-ttu-id="05039-174">5</span><span class="sxs-lookup"><span data-stu-id="05039-174">5</span></span>|<span data-ttu-id="05039-175">公用程式無法載入所要求的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-175">The utility was unable to load the requested package.</span></span> <span data-ttu-id="05039-176">無法載入這個封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-176">The package could not be loaded.</span></span>|  
|<span data-ttu-id="05039-177">6</span><span class="sxs-lookup"><span data-stu-id="05039-177">6</span></span>|<span data-ttu-id="05039-178">公用程式在命令列中發現內部語法錯誤或語意錯誤。</span><span class="sxs-lookup"><span data-stu-id="05039-178">The utility encountered an internal error of syntactic or semantic errors in the command line.</span></span>|  
  
##  <a name="syntax-rules"></a><a name="syntaxRules"></a> <span data-ttu-id="05039-179">語法與規則</span><span class="sxs-lookup"><span data-stu-id="05039-179">Syntax Rules</span></span>  
 <span data-ttu-id="05039-180">**公用程式語法規則**</span><span class="sxs-lookup"><span data-stu-id="05039-180">**Utility syntax rules**</span></span>  
  
 <span data-ttu-id="05039-181">所有選項的開頭都必須是斜線 (/) 或減號 (-)。</span><span class="sxs-lookup"><span data-stu-id="05039-181">All options must start with a slash (/) or a minus sign (-).</span></span> <span data-ttu-id="05039-182">此處顯示的選項的開頭為斜線 (/)，但可以用減號 (-) 來替代。</span><span class="sxs-lookup"><span data-stu-id="05039-182">The options that are shown here start with a slash (/), but the minus sign (-) can be substituted.</span></span>  
  
 <span data-ttu-id="05039-183">如果引數中包含空格，則引數必須包含在引號內。</span><span class="sxs-lookup"><span data-stu-id="05039-183">An argument must be enclosed in quotation marks if it contains a space.</span></span> <span data-ttu-id="05039-184">如果引數沒有用引號括住，則引數不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="05039-184">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="05039-185">加上引號的字串內的雙引號代表逸出的單引號。</span><span class="sxs-lookup"><span data-stu-id="05039-185">Doubled quotation marks within quoted strings represent escaped single quotation marks.</span></span>  
  
 <span data-ttu-id="05039-186">除了密碼以外，選項和引數都沒有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="05039-186">Options and arguments are not case-sensitive, except for passwords.</span></span>  
  
##  <a name="using-dtexec-from-the-xp_cmdshell"></a><a name="cmdshell"></a> <span data-ttu-id="05039-187">使用 xp_cmdshell 的 dtexec</span><span class="sxs-lookup"><span data-stu-id="05039-187">Using dtexec from the xp_cmdshell</span></span>  
 <span data-ttu-id="05039-188">**使用 xp_cmdshell 的 dtexec**</span><span class="sxs-lookup"><span data-stu-id="05039-188">**Using dtexec from the xp_cmdshell**</span></span>  
  
 <span data-ttu-id="05039-189">您可以從 **xp_cmdshell** 提示處執行 dtexec。</span><span class="sxs-lookup"><span data-stu-id="05039-189">You can run dtexec from the **xp_cmdshell** prompt.</span></span> <span data-ttu-id="05039-190">下列範例顯示如何執行名為 UpsertData.dtsx 的封裝，並忽略傳回碼：</span><span class="sxs-lookup"><span data-stu-id="05039-190">The following example shows how to run a package called UpsertData.dtsx and ignore the return code:</span></span>  
  
```  
EXEC xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
 <span data-ttu-id="05039-191">下列範例顯示如何執行同一個封裝，並擷取傳回碼：</span><span class="sxs-lookup"><span data-stu-id="05039-191">The following example shows how to run the same package and capture the return code:</span></span>  
  
```  
DECLARE @returncode int  
EXEC @returncode = xp_cmdshell 'dtexec /f "C:\UpsertData.dtsx"'  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="05039-192">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，新安裝的 **xp_cmdshell** 選項預設為停用。</span><span class="sxs-lookup"><span data-stu-id="05039-192">In [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **xp_cmdshell** option is disabled by default on new installations.</span></span> <span data-ttu-id="05039-193">您可以執行 **sp_configure** 系統預存程序以啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="05039-193">The option can be enabled by running the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="05039-194">如需詳細資訊，請參閱 [xp_cmdshell 伺服器組態選項](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-194">For more information, see [xp_cmdshell Server Configuration Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).</span></span>  
  
##  <a name="syntax"></a><a name="syntax"></a> <span data-ttu-id="05039-195">語法</span><span class="sxs-lookup"><span data-stu-id="05039-195">Syntax</span></span>  
  
```  
dtexec /option [value] [/option [value]]...  
```  
  
##  <a name="parameters"></a><a name="parameter"></a> <span data-ttu-id="05039-196">參數</span><span class="sxs-lookup"><span data-stu-id="05039-196">Parameters</span></span>  
  
-   <span data-ttu-id="05039-197">**/?**</span><span class="sxs-lookup"><span data-stu-id="05039-197">**/?**</span></span> <span data-ttu-id="05039-198">[*option_name*]：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-198">[*option_name*]: Optional.</span></span> <span data-ttu-id="05039-199">顯示命令提示字元選項，或顯示指定之 *option_name* 的說明，然後關閉公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-199">Displays the command prompt options, or displays help for the specified *option_name* and then closes the utility.</span></span>  
  
     <span data-ttu-id="05039-200">如果您指定*option_name*引數，則會 `dtexec` 啟動《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》，並顯示 dtexec 公用程式主題。</span><span class="sxs-lookup"><span data-stu-id="05039-200">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="05039-201">**/Ca [llerInfo]**：</span><span class="sxs-lookup"><span data-stu-id="05039-201">**/Ca[llerInfo]**:</span></span>   
                  <span data-ttu-id="05039-202">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-202">Optional.</span></span> <span data-ttu-id="05039-203">指定封裝執行的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="05039-203">Specifies additional information for a package execution.</span></span> <span data-ttu-id="05039-204">當您使用 SQL Server Agent 執行封裝時，代理程式會設定此引數以指示透過 SQL Server Agent 叫用封裝執行。</span><span class="sxs-lookup"><span data-stu-id="05039-204">When you run a package using SQL Server Agent, agent sets this argument to indicate that the package execution is invoked by SQL Server Agent.</span></span> <span data-ttu-id="05039-205">從命令列執行 `dtexec` 公用程式時，會忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="05039-205">This parameter is ignored when the `dtexec` utility is run from the command line.</span></span>  
  
-   <span data-ttu-id="05039-206">**/CheckF[ile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="05039-206">**/CheckF[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="05039-207">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-207">Optional.</span></span> <span data-ttu-id="05039-208">將 `CheckpointFileName` 封裝上的屬性設定為*filespec*中的路徑和檔案 spemandcified。</span><span class="sxs-lookup"><span data-stu-id="05039-208">Sets the `CheckpointFileName` property on the package to the path and file spemandcified in *filespec*.</span></span> <span data-ttu-id="05039-209">當重新啟動封裝時，會使用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-209">This file is used when the package restarts.</span></span> <span data-ttu-id="05039-210">如果指定這個選項時沒有使用檔案名稱值，就會將封裝的 `CheckpointFileName` 設為空字串。</span><span class="sxs-lookup"><span data-stu-id="05039-210">If this option is specified and no value is supplied for the file name, the `CheckpointFileName` for the package is set to an empty string.</span></span> <span data-ttu-id="05039-211">如果沒有指定這個選項，就會保留封裝中的值。</span><span class="sxs-lookup"><span data-stu-id="05039-211">If this option is not specified, the values in the package are retained.</span></span>  
  
-   <span data-ttu-id="05039-212">**/CheckP [ointing]** _{on\off}_：</span><span class="sxs-lookup"><span data-stu-id="05039-212">**/CheckP[ointing]** _{on\off}_:</span></span>   
                  <span data-ttu-id="05039-213">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-213">Optional.</span></span> <span data-ttu-id="05039-214">設定一個值來決定在執行封裝期間，封裝是否要使用檢查點。</span><span class="sxs-lookup"><span data-stu-id="05039-214">Sets a value that determines whether the package will use checkpoints during package execution.</span></span> <span data-ttu-id="05039-215">**on** 值可指定重新執行失敗的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-215">The value **on** specifies that a failed package is to be rerun.</span></span> <span data-ttu-id="05039-216">當重新執行失敗的封裝時，執行階段引擎會使用檢查點，從失敗點重新啟動封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-216">When the failed package is rerun, the run-time engine uses the checkpoint file to restart the package from the point of failure.</span></span>  
  
     <span data-ttu-id="05039-217">如果宣告的選項不含任何值，則預設值是 on。</span><span class="sxs-lookup"><span data-stu-id="05039-217">The default value is on if the option is declared without a value.</span></span> <span data-ttu-id="05039-218">如果此值設為 on，但找不到檢查點檔案，則封裝執行失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-218">Package execution will fail if the value is set to on and the checkpoint file cannot be found.</span></span> <span data-ttu-id="05039-219">如果沒有指定這個選項，就會保留封裝中所設定的值。</span><span class="sxs-lookup"><span data-stu-id="05039-219">If this option is not specified, the value set in the package is retained.</span></span> <span data-ttu-id="05039-220">如需詳細資訊，請參閱 [使用檢查點來重新啟動封裝](restart-packages-by-using-checkpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-220">For more information, see [Restart Packages by Using Checkpoints](restart-packages-by-using-checkpoints.md).</span></span>  
  
     <span data-ttu-id="05039-221">Dtexec 的 **/checkpointing on**選項相當於將封裝的屬性設定 `SaveCheckpoints` 為 True，並將 `CheckpointUsage` 屬性設為 Always。</span><span class="sxs-lookup"><span data-stu-id="05039-221">The **/CheckPointing on** option of dtexec is equivalent to setting the `SaveCheckpoints` property of the package to True, and the `CheckpointUsage` property to Always.</span></span>  
  
-   <span data-ttu-id="05039-222">**/Com[mandFile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="05039-222">**/Com[mandFile]** _filespec_:</span></span>   
                  <span data-ttu-id="05039-223">(選擇性)。</span><span class="sxs-lookup"><span data-stu-id="05039-223">(Optional).</span></span> <span data-ttu-id="05039-224">指定要與 `dtexec` 一起執行的命令選項。</span><span class="sxs-lookup"><span data-stu-id="05039-224">Specifies the command options that run with `dtexec`.</span></span> <span data-ttu-id="05039-225">*filespec* 中指定的檔案會開啟，並且讀取檔案中的選項，直到在檔案中找到 EOF 為止。</span><span class="sxs-lookup"><span data-stu-id="05039-225">The file specified in *filespec* is opened and options from the file are read until EOF is found in the file.</span></span> <span data-ttu-id="05039-226">*filespec* 是文字檔。</span><span class="sxs-lookup"><span data-stu-id="05039-226">*filespec* is a text file.</span></span> <span data-ttu-id="05039-227">*filespec* 引數會指定要與封裝的執行產生關聯之命令檔的檔名和路徑。</span><span class="sxs-lookup"><span data-stu-id="05039-227">The *filespec* argument specifies the file name and path of the command file to associate with the execution of the package.</span></span>  
  
-   <span data-ttu-id="05039-228">**/Conf [igFile]** _filespec_：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-228">**/Conf[igFile]** _filespec_: Optional.</span></span> <span data-ttu-id="05039-229">指定要擷取值的來源組態檔。</span><span class="sxs-lookup"><span data-stu-id="05039-229">Specifies a configuration file to extract values from.</span></span> <span data-ttu-id="05039-230">使用這個選項時，您可以設定一個執行階段組態，這個執行階段組態與封裝設計階段所指定的組態不同。</span><span class="sxs-lookup"><span data-stu-id="05039-230">Using this option, you can set a run-time configuration that differs from the configuration that was specified at design time for the package.</span></span> <span data-ttu-id="05039-231">您可以將不同的組態設定儲存在 XML 組態檔中，然後在執行封裝之前，利用 **/ConfigFile** 選項載入設定。</span><span class="sxs-lookup"><span data-stu-id="05039-231">You can store different configuration settings in an XML configuration file and then load the settings before package execution by using the **/ConfigFile** option.</span></span>  
  
     <span data-ttu-id="05039-232">您可以使用 **/ConfigFile** 選項在執行階段載入您未在設計階段指定的其他組態。</span><span class="sxs-lookup"><span data-stu-id="05039-232">You can use the **/ConfigFile** option to load additional configurations at run time that you did not specify at design time.</span></span> <span data-ttu-id="05039-233">但您不可使用 **/ConfigFile** 選項取代您在設計階段指定過的設定值。</span><span class="sxs-lookup"><span data-stu-id="05039-233">However, you cannot use the **/ConfigFile** option to replace configured values that you also specified at design time.</span></span> <span data-ttu-id="05039-234">如需了解封裝組態套用的方式，請參閱＜ [Package Configurations](../package-configurations.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-234">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md).</span></span>  
  
-   <span data-ttu-id="05039-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_：</span><span class="sxs-lookup"><span data-stu-id="05039-235">**/Conn[ection]** _id_or_name;connection_string [[;id_or_name;connection_string]...]_:</span></span>   
                  <span data-ttu-id="05039-236">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-236">Optional.</span></span> <span data-ttu-id="05039-237">指定具有指定名稱或 GUID 的連接管理員位於此封裝中，並指定連接字串。</span><span class="sxs-lookup"><span data-stu-id="05039-237">Specifies that the connection manager with the specified name or GUID is located in the package, and specifies a connection string.</span></span>  
  
     <span data-ttu-id="05039-238">這個選項需要同時指定這兩個參數：在 *id_or_name* 引數中必須提供連接管理員名稱或 GUID，而且在 *connection_string* 引數中必須指定有效的連接字串。</span><span class="sxs-lookup"><span data-stu-id="05039-238">This option requires that both parameters be specified: the connection manager name or GUID must be provided in the *id_or_name* argument, and a valid connection string must be specified in the *connection_string* argument.</span></span> <span data-ttu-id="05039-239">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-239">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
     <span data-ttu-id="05039-240">您可以在執行階段使用 **/Connection** 選項，從不同於設計時所指定的位置載入封裝組態。</span><span class="sxs-lookup"><span data-stu-id="05039-240">At run time, you can use the **/Connection** option to load package configurations from a location other than the location that you specified at design time.</span></span> <span data-ttu-id="05039-241">然後這些組態的值會取代您原本指定的值。</span><span class="sxs-lookup"><span data-stu-id="05039-241">The values of these configurations then replace the values that were originally specified.</span></span> <span data-ttu-id="05039-242">但 **/Connection** 選項只可用於使用連接管理員的組態，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態。</span><span class="sxs-lookup"><span data-stu-id="05039-242">However you can use the **/Connection** option only for configurations, such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurations, that use a connection manager.</span></span> <span data-ttu-id="05039-243">若要瞭解封裝設定的套用方式，請參閱[SQL Server 2014 中 Integration Services 功能的](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)[套件](../package-configurations.md)設定和行為變更。</span><span class="sxs-lookup"><span data-stu-id="05039-243">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="05039-244">**/Cons [oleLog]** [[*displayoptions*]; [*list_options*;*src_name_or_guid*]...]：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-244">**/Cons[oleLog]** [[*displayoptions*];[*list_options*;*src_name_or_guid*]...]: Optional.</span></span> <span data-ttu-id="05039-245">在執行封裝期間，於主控台中顯示指定的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="05039-245">Displays specified log entries to the console during package execution.</span></span> <span data-ttu-id="05039-246">如果省略了這個選項，主控台便不會顯示任何記錄項目。</span><span class="sxs-lookup"><span data-stu-id="05039-246">If this option is omitted, no log entries are shown in the console.</span></span> <span data-ttu-id="05039-247">如果指定了這個選項，但未設定用來限制顯示的參數，就會顯示每個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="05039-247">If the option is specified without parameters that limit the display, every log entry will display.</span></span> <span data-ttu-id="05039-248">若要限制主控台顯示的項目，您可以使用 *displayoptions* 參數指定要顯示的資料行，以及使用 *list_options* 參數來限制記錄項目類型。</span><span class="sxs-lookup"><span data-stu-id="05039-248">To limit the entries that are displayed to the console, you can specify the columns to show by using the *displayoptions* parameter, and limit the log entry types by using the *list_options* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05039-249">當您使用參數在伺服器上執行封裝時 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] `/ISSERVER` ，主控台輸出會受到限制，而且大部分的 **/Cons [oleLog]** 選項都不適用。</span><span class="sxs-lookup"><span data-stu-id="05039-249">When you run a package on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server by using the `/ISSERVER` parameter, console output is limited and most of the **/Cons[oleLog]** options are not applicable.</span></span> <span data-ttu-id="05039-250">所有執行記錄都可以從伺服器的相關檢視中查看，或透過 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中提供的標準報表查看。</span><span class="sxs-lookup"><span data-stu-id="05039-250">All execution logs can be seen from the server in the related views or by using standard reports available in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="05039-251">如需報表的詳細資訊，請參閱 [Integration Services 伺服器的報表](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="05039-251">For more information about the reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
     <span data-ttu-id="05039-252">*displayoptions* 值如下：</span><span class="sxs-lookup"><span data-stu-id="05039-252">The *displayoptions* values are as follows:</span></span>  
  
    -   <span data-ttu-id="05039-253">N (名稱)</span><span class="sxs-lookup"><span data-stu-id="05039-253">N (Name)</span></span>  
  
    -   <span data-ttu-id="05039-254">C (電腦)</span><span class="sxs-lookup"><span data-stu-id="05039-254">C (Computer)</span></span>  
  
    -   <span data-ttu-id="05039-255">O (操作員)</span><span class="sxs-lookup"><span data-stu-id="05039-255">O (Operator)</span></span>  
  
    -   <span data-ttu-id="05039-256">S (來源名稱)</span><span class="sxs-lookup"><span data-stu-id="05039-256">S (Source Name)</span></span>  
  
    -   <span data-ttu-id="05039-257">G (來源 GUID)</span><span class="sxs-lookup"><span data-stu-id="05039-257">G (Source GUID)</span></span>  
  
    -   <span data-ttu-id="05039-258">X (執行 GUID)</span><span class="sxs-lookup"><span data-stu-id="05039-258">X (Execution GUID)</span></span>  
  
    -   <span data-ttu-id="05039-259">M (訊息)</span><span class="sxs-lookup"><span data-stu-id="05039-259">M (Message)</span></span>  
  
    -   <span data-ttu-id="05039-260">T (開始和結束時間)</span><span class="sxs-lookup"><span data-stu-id="05039-260">T (Time Start and End)</span></span>  
  
     <span data-ttu-id="05039-261">*list_options* 值如下：</span><span class="sxs-lookup"><span data-stu-id="05039-261">The *list_options* values are as follows:</span></span>  
  
    -   <span data-ttu-id="05039-262">*I* - 指定包含清單。</span><span class="sxs-lookup"><span data-stu-id="05039-262">*I* - Specifies the inclusion list.</span></span> <span data-ttu-id="05039-263">只記錄指定的來源名稱或 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-263">Only the source names or GUIDs that are specified are logged.</span></span>  
  
    -   <span data-ttu-id="05039-264">*E* - 指定排除清單。</span><span class="sxs-lookup"><span data-stu-id="05039-264">*E* - Specifies the exclusion list.</span></span> <span data-ttu-id="05039-265">不記錄指定的來源名稱或 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-265">The source names or GUIDs that are specified are not logged.</span></span>  
  
    -   <span data-ttu-id="05039-266">對包含或排除指定的 *src_name_or_guid* 參數為事件名稱、來源名稱或來源 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-266">The *src_name_or_guid* parameter specified for inclusion or exclusion is an event name, source name, or source GUID.</span></span>  
  
     <span data-ttu-id="05039-267">您如在同一個命令提示字元處使用多個 **/ConsoleLog** 選項，這些選項的互動方式如下：</span><span class="sxs-lookup"><span data-stu-id="05039-267">If you use multiple **/ConsoleLog** options on the same command prompt, they interact as follows:</span></span>  
  
    -   <span data-ttu-id="05039-268">顯示順序不受影響。</span><span class="sxs-lookup"><span data-stu-id="05039-268">Their order of appearance has no effect.</span></span>  
  
    -   <span data-ttu-id="05039-269">如果命令列上沒有包含清單，則排除清單會套用至所有類型的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="05039-269">If no inclusion lists are present on the command line, exclusion lists are applied against all kinds of log entries.</span></span>  
  
    -   <span data-ttu-id="05039-270">如果命令列上出現任何包含清單，則排除清單會套用至所有包含清單的聯集。</span><span class="sxs-lookup"><span data-stu-id="05039-270">If any inclusion lists are present on the command line, exclusion lists are applied against the union of all inclusion lists.</span></span>  
  
     <span data-ttu-id="05039-271">如需 **/ConsoleLog**選項的範例，請參閱**備註**一節。</span><span class="sxs-lookup"><span data-stu-id="05039-271">For examples of the **/ConsoleLog** option, see the **Remarks** section.</span></span>  
  
-   <span data-ttu-id="05039-272">**/D[ts]** _package_path_：</span><span class="sxs-lookup"><span data-stu-id="05039-272">**/D[ts]** _package_path_:</span></span>   
                  <span data-ttu-id="05039-273">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-273">Optional.</span></span> <span data-ttu-id="05039-274">從 SSIS 封裝存放區中載入封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-274">Loads a package from the SSIS Package Store.</span></span> <span data-ttu-id="05039-275">儲存在 SSIS 封裝存放區中的封裝是使用舊版封裝部署模型所部署。</span><span class="sxs-lookup"><span data-stu-id="05039-275">Packages that are stored in the SSIS Package Store, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="05039-276">若要使用專案部署模型，執行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的封裝，請使用 `/ISServer` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-276">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05039-277">如需有關封裝和專案部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-277">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="05039-278">*package_path* 引數指定 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的相對路徑，從 SSIS 封裝存放區的根目錄開始，並包括 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-278">The *package_path* argument specifies the relative path of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package, starting at the root of the SSIS Package Store, and includes the name of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="05039-279">如果 *package_path* 引數中指定的路徑或檔案名稱包含空格，必須將 *package_path* 引數括以引號。</span><span class="sxs-lookup"><span data-stu-id="05039-279">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="05039-280">`/DTS` 選項不可與 `/File` 或 `/SQL` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-280">The `/DTS` option cannot be used together with the `/File` or `/SQL` option.</span></span> <span data-ttu-id="05039-281">如果指定多個選項，`dtexec` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-281">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05039-282">**/De [crypt]**  _password_：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-282">**/De[crypt]**  _password_: Optional.</span></span> <span data-ttu-id="05039-283">設定載入含密碼加密的封裝時，所用的解密密碼。</span><span class="sxs-lookup"><span data-stu-id="05039-283">Sets the decryption password that is used when you load a package with password encryption.</span></span>  
  
-   <span data-ttu-id="05039-284">**/Dump** _error code_：</span><span class="sxs-lookup"><span data-stu-id="05039-284">**/Dump** _error code_:</span></span>  
                  <span data-ttu-id="05039-285">選擇性：當封裝正在執行時，如果發生一或多個指定的事件，則會建立 .mdmp 和 .tmp 的調試檔。</span><span class="sxs-lookup"><span data-stu-id="05039-285">Optional Creates the debug dump files, .mdmp and .tmp, when one or more specified events occur while the package is running.</span></span> <span data-ttu-id="05039-286">*error code* 引數會指定事件代碼的類型 (錯誤、警告或資訊)，這些事件代碼將會觸發系統建立偵錯傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-286">The *error code* argument specifies the type of event code-error, warning, or information-that will trigger the system to create the debug dump files.</span></span> <span data-ttu-id="05039-287">若要指定多個事件代碼，請用分號 (;) 隔開每一個「錯誤碼」  引數。</span><span class="sxs-lookup"><span data-stu-id="05039-287">To specify multiple event codes, separate each *error code* argument by a semi-colon (;).</span></span> <span data-ttu-id="05039-288">*error code* 引數中請勿包含引號。</span><span class="sxs-lookup"><span data-stu-id="05039-288">Do not include quotes with the *error code* argument.</span></span>  
  
     <span data-ttu-id="05039-289">下列範例會在 DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER 錯誤發生時，產生偵錯傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-289">The following example generates the debug dump files when the DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER error occurs.</span></span>  
  
    ```  
    /Dump 0xC020801C  
    ```  
  
     <span data-ttu-id="05039-290">根據預設，會將偵錯工具傾印檔案 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 儲存在 *\<drive>* 下列資料夾中： \PROGRAM Files\Microsoft SQL server\110\shared\errordumps 資料夾。</span><span class="sxs-lookup"><span data-stu-id="05039-290">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05039-291">偵錯傾印檔案可能會包含敏感性資訊。</span><span class="sxs-lookup"><span data-stu-id="05039-291">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="05039-292">您可以使用存取控制清單 (ACL) 來限制這些檔案的存取權，或將這些檔案複製到具有限制性存取權的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05039-292">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="05039-293">例如，在您將偵錯檔案傳送給 Microsoft 支援服務之前，我們建議您先移除任何敏感性或機密資訊。</span><span class="sxs-lookup"><span data-stu-id="05039-293">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="05039-294">若要將此選項套用到 `dtexec` 公用程式執行的所有封裝，請將**DumpOnCodes** REG_SZ 值新增至 HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="05039-294">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnCodes** REG_SZ value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="05039-295">**DumpOnCodes** 的資料值會指定觸發系統建立偵錯傾印檔案的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="05039-295">The data value in **DumpOnCodes** specifies the error code or codes that will trigger the system to create debug dump files.</span></span> <span data-ttu-id="05039-296">多個錯誤碼必須以分號 (;) 隔開。</span><span class="sxs-lookup"><span data-stu-id="05039-296">Multiple error codes must be separated by a semi-colon (;).</span></span>  
  
     <span data-ttu-id="05039-297">若您將 **DumpOnCodes** 值加入此登錄機碼中，並使用 **/Dump** 選項，系統將會建立以這兩個設定為根據的偵錯傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-297">If you add a **DumpOnCodes** value to the registry key, and use the **/Dump** option, the system will create debug dump files that are based on both settings.</span></span>  
  
     <span data-ttu-id="05039-298">如需有關偵錯傾印檔案的詳細資訊，請參閱＜ [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-298">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
-   <span data-ttu-id="05039-299">**/DumpOnError**：</span><span class="sxs-lookup"><span data-stu-id="05039-299">**/DumpOnError**:</span></span>   
                  <span data-ttu-id="05039-300">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-300">Optional.</span></span> <span data-ttu-id="05039-301">當封裝正在執行時，如果發生任何錯誤，就會建立 .mdmp 和 .tmp 的「調試傾印」檔案。</span><span class="sxs-lookup"><span data-stu-id="05039-301">Creates the debug dump files, .mdmp and .tmp, when any error occurs while the package is running.</span></span>  
  
     <span data-ttu-id="05039-302">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 預設會將偵錯傾印檔案儲存在 *\<drive>* :\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="05039-302">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores the debug dump files in the folder, *\<drive>*:\Program Files\Microsoft SQL Server\110\Shared\ErrorDumps folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05039-303">偵錯傾印檔案可能會包含敏感性資訊。</span><span class="sxs-lookup"><span data-stu-id="05039-303">Debug dump files may contain sensitive information.</span></span> <span data-ttu-id="05039-304">您可以使用存取控制清單 (ACL) 來限制這些檔案的存取權，或將這些檔案複製到具有限制性存取權的資料夾。</span><span class="sxs-lookup"><span data-stu-id="05039-304">Use an access control list (ACL) to restrict access to the files, or copy the files to a folder with restricted access.</span></span> <span data-ttu-id="05039-305">例如，在您將偵錯檔案傳送給 Microsoft 支援服務之前，我們建議您先移除任何敏感性或機密資訊。</span><span class="sxs-lookup"><span data-stu-id="05039-305">For example, before you send your debug files to Microsoft support services, we recommended that you remove any sensitive or confidential information.</span></span>  
  
     <span data-ttu-id="05039-306">若要將此選項套用到 `dtexec` 公用程式執行的所有封裝，請將**DumpOnError** REG_DWORD 值新增至 HKEY_LOCAL_MACHINE \software\microsoft\microsoft SQL Server\110\SSIS\Setup\DtsPath 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="05039-306">To apply this option to all packages that the `dtexec` utility runs, add a **DumpOnError** REG_DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS\Setup\DtsPath registry key.</span></span> <span data-ttu-id="05039-307">**DumpOnError**的值 REG_DWORD 值會決定 **/DumpOnError**選項是否需要與 `dtexec` 公用程式搭配使用：</span><span class="sxs-lookup"><span data-stu-id="05039-307">The value of the **DumpOnError** REG_DWORD value determines whether the **/DumpOnError** option needs to be used with the `dtexec` utility:</span></span>  
  
    -   <span data-ttu-id="05039-308">非零的資料值表示系統將會在發生任何錯誤時建立「偵錯工具」傾印檔案，不論您是否使用 **/DumpOnError**選項搭配 `dtexec` 公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-308">A non-zero data value indicates that the system will create debug dump files when any error occurs, regardless of whether you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
    -   <span data-ttu-id="05039-309">零的資料值表示系統將不會建立 debug 傾印檔案，除非您搭配公用程式使用 **/DumpOnError**選項 `dtexec` 。</span><span class="sxs-lookup"><span data-stu-id="05039-309">A zero data value indicates that the system will not create the debug dump files unless you use the **/DumpOnError** option with the `dtexec` utility.</span></span>  
  
     <span data-ttu-id="05039-310">如需有關偵錯傾印檔案的詳細資訊，請參閱＜ [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-310">For more information about debug dump files, see [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md)</span></span>  
  
-   <span data-ttu-id="05039-311">`/Env[Reference]`*環境參考識別碼*：</span><span class="sxs-lookup"><span data-stu-id="05039-311">`/Env[Reference]` *environment reference ID*:</span></span>   
                  <span data-ttu-id="05039-312">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-312">Optional.</span></span> <span data-ttu-id="05039-313">針對部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的封裝，指定封裝執行所使用的環境參考 (ID)。</span><span class="sxs-lookup"><span data-stu-id="05039-313">Specifies the environment reference (ID) that is used by the package execution, for a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05039-314">設定為繫結至變數的參數將使用環境中包含之變數的值。</span><span class="sxs-lookup"><span data-stu-id="05039-314">The parameters configured to bind to variables will use the values of the variables that are contained in the environment.</span></span>  
  
     <span data-ttu-id="05039-315">您可以將 `/Env[Reference]` 選項與 `/ISServer` 及 `/Server` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-315">You use `/Env[Reference]` option together with the `/ISServer` and the `/Server` options.</span></span>  
  
     <span data-ttu-id="05039-316">此參數是由 SQL Server Agent 所使用。</span><span class="sxs-lookup"><span data-stu-id="05039-316">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="05039-317">**/F[ile]** _filespec_：</span><span class="sxs-lookup"><span data-stu-id="05039-317">**/F[ile]** _filespec_:</span></span>   
                  <span data-ttu-id="05039-318">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-318">Optional.</span></span> <span data-ttu-id="05039-319">載入儲存在檔案系統中的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-319">Loads a package that is saved in the file system.</span></span> <span data-ttu-id="05039-320">儲存在檔案系統中的封裝是使用舊版封裝部署模型所部署。</span><span class="sxs-lookup"><span data-stu-id="05039-320">Packages that are saved in the file system, are deployed using the legacy package deployment model.</span></span> <span data-ttu-id="05039-321">若要使用專案部署模型，執行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的封裝，請使用 `/ISServer` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-321">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05039-322">如需封裝和專案部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-322">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)</span></span>  
  
     <span data-ttu-id="05039-323">*filespec* 引數指定封裝的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-323">The *filespec* argument specifies the path and file name of the package.</span></span> <span data-ttu-id="05039-324">您可以指定路徑為通用命名慣例 (UNC) 路徑或本機路徑。</span><span class="sxs-lookup"><span data-stu-id="05039-324">You can specify the path as either a Universal Naming Convention (UNC) path or a local path.</span></span> <span data-ttu-id="05039-325">如果 *filespec* 引數中指定的路徑或檔案名稱包含空格，必須將 *filespec* 引數括以引號。</span><span class="sxs-lookup"><span data-stu-id="05039-325">If the path or file name specified in the *filespec* argument contains a space, you must put quotation marks around the *filespec* argument.</span></span>  
  
     <span data-ttu-id="05039-326">`/File` 選項不可與 `/DTS` 或 `/SQL` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-326">The `/File` option cannot be used together with the `/DTS` or `/SQL` option.</span></span> <span data-ttu-id="05039-327">如果指定多個選項，`dtexec` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-327">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05039-328">**/H [elp]** [*Option_name*]：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-328">**/H[elp]** [*option_name*]: Optional.</span></span> <span data-ttu-id="05039-329">顯示選項的說明，或顯示指定之 *option_name* 的說明，並關閉公用程式。</span><span class="sxs-lookup"><span data-stu-id="05039-329">Displays help for the options, or displays help for the specified *option_name* and closes the utility.</span></span>  
  
     <span data-ttu-id="05039-330">如果您指定*option_name*引數，則會 `dtexec` 啟動《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》，並顯示 dtexec 公用程式主題。</span><span class="sxs-lookup"><span data-stu-id="05039-330">If you specify an *option_name* argument, `dtexec` starts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online and displays the dtexec Utility topic.</span></span>  
  
-   <span data-ttu-id="05039-331">`/ISServer`*packagepath*：</span><span class="sxs-lookup"><span data-stu-id="05039-331">`/ISServer` *packagepath*:</span></span>  
                  <span data-ttu-id="05039-332">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-332">Optional.</span></span> <span data-ttu-id="05039-333">執行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-333">Runs a package that is deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05039-334">*PackagePath* 引數會指定部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器之封裝的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-334">The *PackagePath* argument specifies the full path and file name of the package deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="05039-335">如果 *PackagePath* 引數中指定的路徑或檔案名稱包含空格，必須將 *PackagePath* 引數括以引號。</span><span class="sxs-lookup"><span data-stu-id="05039-335">If the path or file name specified in the *PackagePath* argument contains a space, you must put quotation marks around the *PackagePath* argument.</span></span>  
  
     <span data-ttu-id="05039-336">封裝格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="05039-336">The package format is as follows:</span></span>  
  
    ```  
    \<catalog name>\<folder name>\<project name>\package file name  
    ```  
  
     <span data-ttu-id="05039-337">您可以將 `/Server` 選項與 `/ISSERVER` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-337">You use `/Server` option together with the `/ISSERVER` option.</span></span> <span data-ttu-id="05039-338">只有 Windows 驗證可以執行 SSIS 伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-338">Only Windows Authentication can execute a package on the SSIS Server.</span></span> <span data-ttu-id="05039-339">目前的 Windows 使用者用來存取封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-339">The current Windows user is used to access the package.</span></span> <span data-ttu-id="05039-340">如果省略 /Server 選項，將假設使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="05039-340">If the /Server option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="05039-341">`/ISSERVER` 選項無法與 `/DTS`, `/SQL` 或 `/File` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-341">The `/ISSERVER` option cannot be used together with the `/DTS`, `/SQL` or `/File` option.</span></span> <span data-ttu-id="05039-342">如果指定了多個選項，dtexec 便會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-342">If multiple options are specified, dtexec fails.</span></span>  
  
     <span data-ttu-id="05039-343">此參數是由 SQL Server Agent 所使用。</span><span class="sxs-lookup"><span data-stu-id="05039-343">This parameter is used by SQL Server Agent.</span></span>  
  
-   <span data-ttu-id="05039-344">**/L[ogger]** _classid_orprogid;configstring_：</span><span class="sxs-lookup"><span data-stu-id="05039-344">**/L[ogger]** _classid_orprogid;configstring_:</span></span>  
                  <span data-ttu-id="05039-345">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-345">Optional.</span></span> <span data-ttu-id="05039-346">建立一或多個記錄提供者與 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝執行作業的關聯性。</span><span class="sxs-lookup"><span data-stu-id="05039-346">Associates one or more log providers with the execution of an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="05039-347">*classid_orprogid* 參數指定記錄提供者，並可指定為類別 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-347">The *classid_orprogid* parameter specifies the log provider, and can be specified as a class GUID.</span></span> <span data-ttu-id="05039-348">*configstring* 是用來設定記錄提供者的字串。</span><span class="sxs-lookup"><span data-stu-id="05039-348">The *configstring* is the string that is used to configure the log provider.</span></span>  
  
     <span data-ttu-id="05039-349">下列清單顯示可用的記錄提供者：</span><span class="sxs-lookup"><span data-stu-id="05039-349">The following list shows the available log providers:</span></span>  
  
    -   <span data-ttu-id="05039-350">文字檔：</span><span class="sxs-lookup"><span data-stu-id="05039-350">Text file:</span></span>  
  
        -   <span data-ttu-id="05039-351">ProgID：DTS.LogProviderTextFile.1</span><span class="sxs-lookup"><span data-stu-id="05039-351">ProgID: DTS.LogProviderTextFile.1</span></span>  
  
        -   <span data-ttu-id="05039-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span><span class="sxs-lookup"><span data-stu-id="05039-352">ClassID: {59B2C6A5-663F-4C20-8863-C83F9B72E2EB}</span></span>  
  
    -   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<span data-ttu-id="05039-353">:</span><span class="sxs-lookup"><span data-stu-id="05039-353">:</span></span>  
  
        -   <span data-ttu-id="05039-354">ProgID：DTS.LogProviderSQLProfiler.1</span><span class="sxs-lookup"><span data-stu-id="05039-354">ProgID: DTS.LogProviderSQLProfiler.1</span></span>  
  
        -   <span data-ttu-id="05039-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span><span class="sxs-lookup"><span data-stu-id="05039-355">ClassID: {5C0B8D21-E9AA-462E-BA34-30FF5F7A42A1}</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="05039-356">:</span><span class="sxs-lookup"><span data-stu-id="05039-356">:</span></span>  
  
        -   <span data-ttu-id="05039-357">ProgID：DTS.LogProviderSQLServer.1</span><span class="sxs-lookup"><span data-stu-id="05039-357">ProgID: DTS.LogProviderSQLServer.1</span></span>  
  
        -   <span data-ttu-id="05039-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span><span class="sxs-lookup"><span data-stu-id="05039-358">ClassID: {6AA833A1-E4B2-4431-831B-DE695049DC61}</span></span>  
  
    -   <span data-ttu-id="05039-359">Windows 事件記錄：</span><span class="sxs-lookup"><span data-stu-id="05039-359">Windows Event Log:</span></span>  
  
        -   <span data-ttu-id="05039-360">ProgID：DTS.LogProviderEventLog.1</span><span class="sxs-lookup"><span data-stu-id="05039-360">ProgID: DTS.LogProviderEventLog.1</span></span>  
  
        -   <span data-ttu-id="05039-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span><span class="sxs-lookup"><span data-stu-id="05039-361">ClassID: {97634F75-1DC7-4F1F-8A4C-DAF0E13AAA22}</span></span>  
  
    -   <span data-ttu-id="05039-362">XML 檔案：</span><span class="sxs-lookup"><span data-stu-id="05039-362">XML File:</span></span>  
  
        -   <span data-ttu-id="05039-363">ProgID：DTS.LogProviderXMLFile.1</span><span class="sxs-lookup"><span data-stu-id="05039-363">ProgID: DTS.LogProviderXMLFile.1</span></span>  
  
        -   <span data-ttu-id="05039-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span><span class="sxs-lookup"><span data-stu-id="05039-364">ClassID: {AFED6884-619C-484F-9A09-F42D56E1A7EA}</span></span>  
  
-   <span data-ttu-id="05039-365">**/M[axConcurrent]** _concurrent_executables_：</span><span class="sxs-lookup"><span data-stu-id="05039-365">**/M[axConcurrent]** _concurrent_executables_:</span></span>  
                  <span data-ttu-id="05039-366">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-366">Optional.</span></span> <span data-ttu-id="05039-367">指定封裝可以同時執行的可執行檔數量。</span><span class="sxs-lookup"><span data-stu-id="05039-367">Specifies the number of executable files that the package can run concurrently.</span></span> <span data-ttu-id="05039-368">指定的值必須是非負數的整數或 -1。</span><span class="sxs-lookup"><span data-stu-id="05039-368">The value specified must be either a non-negative integer, or -1.</span></span> <span data-ttu-id="05039-369">-1 值表示 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 允許同時執行的最大可執行檔數量，等於執行封裝之電腦上的處理器總數再加 2。</span><span class="sxs-lookup"><span data-stu-id="05039-369">A value of -1 means that [!INCLUDE[ssIS](../../includes/ssis-md.md)] will allow a maximum number of concurrently running executables that is equal to the total number of processors on the computer executing the package, plus two.</span></span>  
  
-   <span data-ttu-id="05039-370">**/Pack[age]** _PackageName_：</span><span class="sxs-lookup"><span data-stu-id="05039-370">**/Pack[age]** _PackageName_:</span></span>  
                  <span data-ttu-id="05039-371">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-371">Optional.</span></span> <span data-ttu-id="05039-372">指定所執行的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-372">Specifies the package that is executed.</span></span> <span data-ttu-id="05039-373">當您從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]執行封裝時，主要會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="05039-373">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="05039-374">**/P [assword]** _密碼_：</span><span class="sxs-lookup"><span data-stu-id="05039-374">**/P[assword]** _password_:</span></span>  
                  <span data-ttu-id="05039-375">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-375">Optional.</span></span> <span data-ttu-id="05039-376">允許擷取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證所保護的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-376">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="05039-377">此選項會與 **/User** 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="05039-377">This option is used together with the **/User** option.</span></span> <span data-ttu-id="05039-378">若省略 **/Password** 選項而使用 **/User** 選項，將會使用空白密碼。</span><span class="sxs-lookup"><span data-stu-id="05039-378">If the **/Password** option is omitted and the **/User** option is used, a blank password is used.</span></span> <span data-ttu-id="05039-379">*password* 值可括以引號。</span><span class="sxs-lookup"><span data-stu-id="05039-379">The *password* value may be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="05039-380">**/Par [ameter]** [$Package：： | $Project：： | $ServerOption：：] *parameter_name* [ (data_type) ];*literal_value*：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-380">**/Par[ameter]** [$Package:: | $Project:: | $ServerOption::] *parameter_name* [(data_type)]; *literal_value*: Optional.</span></span> <span data-ttu-id="05039-381">指定參數值。</span><span class="sxs-lookup"><span data-stu-id="05039-381">Specifies parameter values.</span></span> <span data-ttu-id="05039-382">可以指定多個 **/Parameter** 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-382">Multiple **/Parameter** options can be specified.</span></span> <span data-ttu-id="05039-383">資料類型為當做字串的 CLR TypeCodes。</span><span class="sxs-lookup"><span data-stu-id="05039-383">The data types are CLR TypeCodes as strings.</span></span> <span data-ttu-id="05039-384">若是非字串的參數，則會在括號中指定資料類型，後面接著參數名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-384">For a non-string parameter, the data type is specified in parenthesis, following the parameter name.</span></span>  
  
     <span data-ttu-id="05039-385">**/Parameter**選項只能與選項搭配使用 `/ISServer` 。</span><span class="sxs-lookup"><span data-stu-id="05039-385">The **/Parameter** option can be used only with the `/ISServer` option.</span></span>  
  
     <span data-ttu-id="05039-386">您可以使用 $Package、$Project 和 $ServerOption 前置詞個別表示封裝參數、專案參數，以及伺服器選項參數。</span><span class="sxs-lookup"><span data-stu-id="05039-386">You use the $Package, $Project, and $ServerOption prefixes to indicate a package parameter, project parameter, and a server option parameter, respectively.</span></span> <span data-ttu-id="05039-387">預設參數類型為封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-387">The default parameter type is package.</span></span>  
  
     <span data-ttu-id="05039-388">以下範例會執行封裝，以及為專案參數 (myparam) 提供 myvalue，並為封裝參數 (anotherparam) 提供整數值 12。</span><span class="sxs-lookup"><span data-stu-id="05039-388">The following is an example of executing a package and providing myvalue for the project parameter (myparam) and the integer value 12 for the package parameter (anotherparam).</span></span>  
  
     `Dtexec /isserver "SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "." /parameter $Project::myparam;myvalue /parameter anotherparam(int32);12`  
  
     <span data-ttu-id="05039-389">您也可以使用參數設定連接管理員屬性。</span><span class="sxs-lookup"><span data-stu-id="05039-389">You can also set connection manager properties by using parameters.</span></span> <span data-ttu-id="05039-390">使用 CM 前置詞代表連接管理員參數。</span><span class="sxs-lookup"><span data-stu-id="05039-390">You use the CM prefix to denote a connection manager parameter.</span></span>  
  
     <span data-ttu-id="05039-391">在以下的範例中，SourceServer 連接管理員的 InitialCatalog 屬性設定為 `ssisdb`。</span><span class="sxs-lookup"><span data-stu-id="05039-391">In the following example, InitialCatalog property of the SourceServer connection manager is set to `ssisdb`.</span></span>  
  
    ```  
    /parameter CM.SourceServer.InitialCatalog;ssisdb  
    ```  
  
     <span data-ttu-id="05039-392">在下列範例中，SourceServer 連接管理員的 ServerName 屬性設定為句號 (.)，表示本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="05039-392">In the following example, ServerName property of the SourceServer connection manager is set to a period (.) to indicate the local server.</span></span>  
  
    ```  
    /parameter CM.SourceServer.ServerName;.  
    ```  
  
-   <span data-ttu-id="05039-393">**/Proj[ect]** _ProjectFile_：</span><span class="sxs-lookup"><span data-stu-id="05039-393">**/Proj[ect]** _ProjectFile_:</span></span>  
                  <span data-ttu-id="05039-394">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-394">Optional.</span></span> <span data-ttu-id="05039-395">指定要從中擷取所執行之封裝的專案。</span><span class="sxs-lookup"><span data-stu-id="05039-395">Specifies the project from which to retrieve the package that is executed.</span></span> <span data-ttu-id="05039-396">*ProjectFile* 引數會指定 .ispac 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-396">The *ProjectFile* argument specifies the .ispac file name.</span></span> <span data-ttu-id="05039-397">當您從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]執行封裝時，主要會使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="05039-397">This parameter is used primarily when you execute the package from [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
-   <span data-ttu-id="05039-398">**/Rem** _comment_：</span><span class="sxs-lookup"><span data-stu-id="05039-398">**/Rem** _comment_:</span></span>  
                  <span data-ttu-id="05039-399">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-399">Optional.</span></span> <span data-ttu-id="05039-400">在命令提示字元或命令檔中加入註解。</span><span class="sxs-lookup"><span data-stu-id="05039-400">Includes comments on the command prompt or in command files.</span></span> <span data-ttu-id="05039-401">引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="05039-401">The argument is optional.</span></span> <span data-ttu-id="05039-402">*comment* 的值是一個字串，它必須以引號括住，或不包含空格。</span><span class="sxs-lookup"><span data-stu-id="05039-402">The value of *comment* is a string that must be enclosed in quotation marks, or contain no white space.</span></span> <span data-ttu-id="05039-403">如果未指定引數，將會插入空白行。</span><span class="sxs-lookup"><span data-stu-id="05039-403">If no argument is specified, a blank line is inserted.</span></span> <span data-ttu-id="05039-404">命令取得階段將會捨棄*comment* 值。</span><span class="sxs-lookup"><span data-stu-id="05039-404">*comment* values are discarded during the command sourcing phase.</span></span>  
  
-   <span data-ttu-id="05039-405">**/Rep [orting]** _level_ [*; event_guid_or_name*[*; event_guid_or_name*[...]]：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-405">**/Rep[orting]** _level_ [*;event_guid_or_name*[*;event_guid_or_name*[...]]: Optional.</span></span> <span data-ttu-id="05039-406">指定要報告的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="05039-406">Specifies what types of messages to report.</span></span> <span data-ttu-id="05039-407">*level* 可用的報告選項如下：</span><span class="sxs-lookup"><span data-stu-id="05039-407">The available reporting options for *level* are as follows:</span></span>  
  
     <span data-ttu-id="05039-408">**N** ...無報告。</span><span class="sxs-lookup"><span data-stu-id="05039-408">**N** No reporting.</span></span>  
  
     <span data-ttu-id="05039-409">`E`報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="05039-409">`E` Errors are reported.</span></span>  
  
     <span data-ttu-id="05039-410">**W** ...報告警告。</span><span class="sxs-lookup"><span data-stu-id="05039-410">**W** Warnings are reported.</span></span>  
  
     <span data-ttu-id="05039-411">`I`系統會報告參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="05039-411">`I` Informational messages are reported.</span></span>  
  
     <span data-ttu-id="05039-412">**C** ...報告自訂事件。</span><span class="sxs-lookup"><span data-stu-id="05039-412">**C** Custom events are reported.</span></span>  
  
     <span data-ttu-id="05039-413">**D** ...報告資料流程工作事件。</span><span class="sxs-lookup"><span data-stu-id="05039-413">**D** Data Flow task events are reported.</span></span>  
  
     <span data-ttu-id="05039-414">**P** ...報告進度。</span><span class="sxs-lookup"><span data-stu-id="05039-414">**P** Progress is reported.</span></span>  
  
     <span data-ttu-id="05039-415">**V** ...詳細資訊報告。</span><span class="sxs-lookup"><span data-stu-id="05039-415">**V** Verbose reporting.</span></span>  
  
     <span data-ttu-id="05039-416">V 和 N 引數與所有其他引數互斥；這兩個引數必須單獨指定。</span><span class="sxs-lookup"><span data-stu-id="05039-416">The arguments of V and N are mutually exclusive to all other arguments; they must be specified alone.</span></span> <span data-ttu-id="05039-417">如果未指定 **/Reporting**選項，則預設層級為 `E` (錯誤) 、 **W** (警告) ，以及**P** (進度) 。</span><span class="sxs-lookup"><span data-stu-id="05039-417">If the **/Reporting** option is not specified then the default level is `E` (errors), **W** (warnings), and **P** (progress).</span></span>  
  
     <span data-ttu-id="05039-418">所有事件前面都加上 "YY/MM/DD HH:MM:SS" 格式的時間戳記，如果有 GUID 或易記名稱，也會加上它們。</span><span class="sxs-lookup"><span data-stu-id="05039-418">All events are preceded with a timestamp in the format "YY/MM/DD HH:MM:SS", and a GUID or friendly name if available.</span></span>  
  
     <span data-ttu-id="05039-419">選擇性參數 *event_guid_or_name* 記錄提供者的例外狀況清單。</span><span class="sxs-lookup"><span data-stu-id="05039-419">The optional parameter *event_guid_or_name* is a list of exceptions to the log providers.</span></span> <span data-ttu-id="05039-420">例外狀況會指出不要記錄但可能已記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="05039-420">The exception specifies the events that are not logged that otherwise might have been logged.</span></span>  
  
     <span data-ttu-id="05039-421">您不需要排除通常預設為不要記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="05039-421">You do not have to exclude an event if the event is not ordinarily logged by default</span></span>  
  
-   <span data-ttu-id="05039-422">**/Res [tart]** {*deny | force | IfPossible*}：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-422">**/Res[tart]** {*deny | force | ifPossible*}: Optional.</span></span> <span data-ttu-id="05039-423">為這個封裝中的 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 屬性指定新值。</span><span class="sxs-lookup"><span data-stu-id="05039-423">Specifies a new value for the <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property on the package.</span></span> <span data-ttu-id="05039-424">這些參數的意義如下：</span><span class="sxs-lookup"><span data-stu-id="05039-424">The meaning of the parameters are as follows:</span></span>  
  
     <span data-ttu-id="05039-425">*Deny* 將 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 屬性設為 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>。</span><span class="sxs-lookup"><span data-stu-id="05039-425">*Deny* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_NEVER>.</span></span>  
  
     <span data-ttu-id="05039-426">*Force* 將 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 屬性設為 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>。</span><span class="sxs-lookup"><span data-stu-id="05039-426">*Force* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_ALWAYS>.</span></span>  
  
     <span data-ttu-id="05039-427">*ifPossible* 將 <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> 屬性設為 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>。</span><span class="sxs-lookup"><span data-stu-id="05039-427">*ifPossible* Sets <xref:Microsoft.SqlServer.Dts.Runtime.Package.CheckpointUsage%2A> property to <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.DTSCheckpointUsage.DTSCU_IFEXISTS>.</span></span>  
  
     <span data-ttu-id="05039-428">若未指定任何值，將會使用預設值 **force** 。</span><span class="sxs-lookup"><span data-stu-id="05039-428">The default value of **force** is used if no value is specified.</span></span>  
  
-   <span data-ttu-id="05039-429">**/Set** [$Sensitive：：]*propertyPath; 值*：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-429">**/Set** [$Sensitive::]*propertyPath;value*: Optional.</span></span> <span data-ttu-id="05039-430">覆寫封裝內的參數、變數、屬性、容器、記錄提供者、Foreach 列舉值或連接的組態。</span><span class="sxs-lookup"><span data-stu-id="05039-430">Overrides the configuration of a parameter, variable, property, container, log provider, Foreach enumerator, or connection within a package.</span></span> <span data-ttu-id="05039-431">使用此選項時， **/Set** 會將 *propertyPath* 引數變更為指定的值。</span><span class="sxs-lookup"><span data-stu-id="05039-431">When this option is used, **/Set** changes the *propertyPath* argument to the value specified.</span></span> <span data-ttu-id="05039-432">可以指定多個 **/Set** 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-432">Multiple **/Set** options can be specified.</span></span>  
  
     <span data-ttu-id="05039-433">除了使用 **/set**選項與 **/f [ile]** 選項之外，您也可以搭配選項或選項使用 **/set**選項 `/ISServer` `/Project` 。</span><span class="sxs-lookup"><span data-stu-id="05039-433">In addition to using the **/Set** option with the **/F[ile]** option, you can also use the **/Set** option with the `/ISServer` option or the `/Project` option.</span></span> <span data-ttu-id="05039-434">當您搭配使用 **/set**與時 `/Project` ， **/set**會設定參數值。</span><span class="sxs-lookup"><span data-stu-id="05039-434">When you use **/Set** with `/Project`, **/Set** sets parameter values.</span></span> <span data-ttu-id="05039-435">當您搭配使用 **/set**與時 `/ISServer` ， **/set**會設定屬性覆寫。</span><span class="sxs-lookup"><span data-stu-id="05039-435">When you use **/Set** with `/ISServer`, **/Set** sets property overrides.</span></span> <span data-ttu-id="05039-436">此外，當您搭配使用 **/set**與時， `/ISServer` 您可以使用選擇性的 $Sensitive 前置詞，表示應該在伺服器上將屬性視為機密 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="05039-436">In addition, when you use **/Set** with `/ISServer`, you can use the optional $Sensitive prefix to indicate that the property should be treated as sensitive on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="05039-437">您可以執行 [封裝組態精靈] 來決定 *propertyPath* 的值。</span><span class="sxs-lookup"><span data-stu-id="05039-437">You can determine the value of *propertyPath* by running the Package Configuration Wizard.</span></span> <span data-ttu-id="05039-438">您選取項目的路徑會顯示在最後的 **[正在完成精靈]** 頁面上，並可複製及貼上。</span><span class="sxs-lookup"><span data-stu-id="05039-438">The paths for items that you select are displayed on the final **Completing the Wizard** page, and can be copied and pasted.</span></span> <span data-ttu-id="05039-439">如果您只是為了這個目的而使用精靈，可以在複製路徑之後取消精靈。</span><span class="sxs-lookup"><span data-stu-id="05039-439">If you have used the wizard only for this purpose, you can cancel the wizard after you copy the paths.</span></span>  
  
     <span data-ttu-id="05039-440">下列範例會執行儲存在檔案系統中的封裝並提供變數的新值：</span><span class="sxs-lookup"><span data-stu-id="05039-440">The following is an example of executing a package that is saved in the file system and providing a new value for a variable:</span></span>  
  
     `dtexec /f mypackage.dtsx /set \package.variables[myvariable].Value;myvalue`  
  
     <span data-ttu-id="05039-441">下列範例會從 .ispac 專案檔案執行封裝，並設定封裝與專案參數。</span><span class="sxs-lookup"><span data-stu-id="05039-441">The following example of running a package from the .ispac project file and setting package and project parameters.</span></span>  
  
     `/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1`  
  
     <span data-ttu-id="05039-442">您可以使用 **/Set** 選項變更載入封裝組態的來源位置。</span><span class="sxs-lookup"><span data-stu-id="05039-442">You can use the **/Set** option to change the location from which package configurations are loaded.</span></span> <span data-ttu-id="05039-443">但您不可使用 **/Set** 選項覆寫先前在設計階段由組態所指定的值。</span><span class="sxs-lookup"><span data-stu-id="05039-443">However, you cannot use the **/Set** option to override a value that was specified by a configuration at design time.</span></span> <span data-ttu-id="05039-444">若要瞭解封裝設定的套用方式，請參閱[SQL Server 2014 中 Integration Services 功能的](../behavior-changes-to-integration-services-features-in-sql-server-2014.md)[套件](../package-configurations.md)設定和行為變更。</span><span class="sxs-lookup"><span data-stu-id="05039-444">To understand how package configurations are applied, see [Package Configurations](../package-configurations.md) and [Behavior Changes to Integration Services Features in SQL Server 2014](../behavior-changes-to-integration-services-features-in-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="05039-445">`/Ser[ver]`*伺服器*：</span><span class="sxs-lookup"><span data-stu-id="05039-445">`/Ser[ver]` *server*:</span></span>  
                  <span data-ttu-id="05039-446">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-446">Optional.</span></span> <span data-ttu-id="05039-447">指定 `/SQL` 或 `/DTS` 選項時，此選項會指定要擷取封裝的來源伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-447">When the `/SQL` or `/DTS` option is specified, this option specifies the name of the server from which to retrieve the package.</span></span> <span data-ttu-id="05039-448">如果省略 `/Server` 選項而指定了 `/SQL` 或 `/DTS` 選項，將會嘗試對本機伺服器執行封裝作業。</span><span class="sxs-lookup"><span data-stu-id="05039-448">If you omit the `/Server` option and the `/SQL` or `/DTS` option is specified, package execution is tried against the local server.</span></span> <span data-ttu-id="05039-449">*server_instance* 值可能會加上引號。</span><span class="sxs-lookup"><span data-stu-id="05039-449">The *server_instance* value may be quoted.</span></span>  
  
     <span data-ttu-id="05039-450">指定 `/Ser[ver]` 選項時，需要 `/ISServer` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-450">The `/Ser[ver]` option is required when the `/ISServer` option is specified.</span></span>  
  
-   <span data-ttu-id="05039-451">**/SQ[L]** _package_path_：</span><span class="sxs-lookup"><span data-stu-id="05039-451">**/SQ[L]** _package_path_:</span></span>  
                  <span data-ttu-id="05039-452">載入儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 `msdb` 資料庫中的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-452">Loads a package that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in `msdb` database.</span></span> <span data-ttu-id="05039-453">儲存在 `msdb` 資料庫中的封裝是使用封裝部署模型所部署。</span><span class="sxs-lookup"><span data-stu-id="05039-453">Packages that are stored in the `msdb` database, are deployed using the package deployment model.</span></span> <span data-ttu-id="05039-454">若要使用專案部署模型，執行部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的封裝，請使用 `/ISServer` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-454">To run packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server using the project deployment model, use the `/ISServer` option.</span></span> <span data-ttu-id="05039-455">如需有關封裝和專案部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="05039-455">For more information about the package and project deployment models, see [Deployment of Projects and Packages](deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
     <span data-ttu-id="05039-456">*package_path* 引數指定要擷取的封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-456">The *package_path* argument specifies the name of the package to retrieve.</span></span> <span data-ttu-id="05039-457">如果路徑包含資料夾，則其結尾應為反斜線 ("\\")。</span><span class="sxs-lookup"><span data-stu-id="05039-457">If folders are included in the path, they are terminated with backslashes ("\\").</span></span> <span data-ttu-id="05039-458">*Package_path* 值可以加上引號。</span><span class="sxs-lookup"><span data-stu-id="05039-458">The *package_path* value can be quoted.</span></span> <span data-ttu-id="05039-459">如果 *package_path* 引數中指定的路徑或檔案名稱包含空格，必須將 *package_path* 引數括以引號。</span><span class="sxs-lookup"><span data-stu-id="05039-459">If the path or file name specified in the *package_path* argument contains a space, you must put quotation marks around the *package_path* argument.</span></span>  
  
     <span data-ttu-id="05039-460">您可以搭配選項使用 **/user**、 **/password**和 `/Server` 選項 `/SQL` 。</span><span class="sxs-lookup"><span data-stu-id="05039-460">You can use the **/User**, **/Password**, and `/Server` options together with the `/SQL` option.</span></span>  
  
     <span data-ttu-id="05039-461">若省略 **/User** 選項，將會使用 Windows 驗證存取封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-461">If you omit the **/User** option, Windows Authentication is used to access the package.</span></span> <span data-ttu-id="05039-462">若使用 **/User** 選項，指定的 **/User** 登入名稱將會與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證建立關聯。</span><span class="sxs-lookup"><span data-stu-id="05039-462">If you use the **/User** option, the **/User** login name specified is associated with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
     <span data-ttu-id="05039-463">**/Password** 選項只能與 **/User** 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="05039-463">The **/Password** option is used only together with the **/User** option.</span></span> <span data-ttu-id="05039-464">若使用 **/Password** 選項，將會使用所提供的使用者名稱與密碼資訊存取封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-464">If you use the **/Password** option, the package is accessed with the user name and password information provided.</span></span> <span data-ttu-id="05039-465">若省略 **/Password** 選項，將會使用空白密碼。</span><span class="sxs-lookup"><span data-stu-id="05039-465">If you omit the **/Password** option, a blank password is used.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
     <span data-ttu-id="05039-466">如果省略 `/Server` 選項，將會假設使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="05039-466">If the `/Server` option is omitted, the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is assumed.</span></span>  
  
     <span data-ttu-id="05039-467">`/SQL` 選項不可與 `/DTS` 或 `/File` 選項並用。</span><span class="sxs-lookup"><span data-stu-id="05039-467">The `/SQL` option cannot be used together with the `/DTS` or `/File` option.</span></span> <span data-ttu-id="05039-468">如果指定多個選項，`dtexec` 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-468">If multiple options are specified, `dtexec` fails.</span></span>  
  
-   <span data-ttu-id="05039-469">**/Su [m]**：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-469">**/Su[m]**: Optional.</span></span> <span data-ttu-id="05039-470">顯示包含下一個元件將接收之列數的累加計數器。</span><span class="sxs-lookup"><span data-stu-id="05039-470">Shows an incremental counter that contains the number of rows that will be received by the next component.</span></span>  
  
-   <span data-ttu-id="05039-471">**/U [ser]** _user_name_：</span><span class="sxs-lookup"><span data-stu-id="05039-471">**/U[ser]** _user_name_:</span></span>  
                  <span data-ttu-id="05039-472">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-472">Optional.</span></span> <span data-ttu-id="05039-473">允許擷取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證所保護的封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-473">Allows the retrieval of a package that is protected by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="05039-474">只有在指定 `/SQL` 選項時，才會使用此選項。</span><span class="sxs-lookup"><span data-stu-id="05039-474">This option is used only when the `/SQL` option is specified.</span></span> <span data-ttu-id="05039-475">*user_name* 值可以引號括住。</span><span class="sxs-lookup"><span data-stu-id="05039-475">The *user_name* value can be quoted.</span></span>  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoteWinAuthentication](../../../includes/ssnotewinauthentication-md.md)]  
  
-   <span data-ttu-id="05039-476">**/Va [lidate]**：</span><span class="sxs-lookup"><span data-stu-id="05039-476">**/Va[lidate]**:</span></span>  
                  <span data-ttu-id="05039-477">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-477">Optional.</span></span> <span data-ttu-id="05039-478">在驗證階段之後，停止執行封裝 (並不會實際執行封裝)。</span><span class="sxs-lookup"><span data-stu-id="05039-478">Stops the execution of the package after the validatation phase, without actually running the package.</span></span> <span data-ttu-id="05039-479">在驗證期間，使用 **/WarnAsError**選項會導致 `dtexec` 將警告視為錯誤; 因此，如果驗證期間發生警告，則封裝會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-479">During validation, use of the **/WarnAsError** option causes `dtexec` to treat a warning as an error; therefore the package fails if a warning occurs during validation.</span></span>  
  
-   <span data-ttu-id="05039-480">**/VerifyB [uild]** _主要_[*; 次要*[*; 組建*]]：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-480">**/VerifyB[uild]** _major_[*;minor*[*;build*]]: Optional.</span></span> <span data-ttu-id="05039-481">根據驗證階段期間在 *major*、 *minor*及 *build* 引數指定的組建編號，來驗證封裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="05039-481">Verifies the build number of a package against the build numbers that were specified during the verification phase in the *major*, *minor*, and *build* arguments.</span></span> <span data-ttu-id="05039-482">如果發生不符的情形，將不會執行封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-482">If a mismatch occurs, the package will not execute.</span></span>  
  
     <span data-ttu-id="05039-483">這些值是 Long 整數。</span><span class="sxs-lookup"><span data-stu-id="05039-483">The values are long integers.</span></span> <span data-ttu-id="05039-484">此引數可以是下列這三種格式的其中一種，而且 *major* 的值永遠是必要的：</span><span class="sxs-lookup"><span data-stu-id="05039-484">The argument can have one of three forms, with a value for *major* always required:</span></span>  
  
    -   <span data-ttu-id="05039-485">*major*</span><span class="sxs-lookup"><span data-stu-id="05039-485">*major*</span></span>  
  
    -   <span data-ttu-id="05039-486">*major*;*minor*</span><span class="sxs-lookup"><span data-stu-id="05039-486">*major*;*minor*</span></span>  
  
    -   <span data-ttu-id="05039-487">*major*; *minor*; *build*</span><span class="sxs-lookup"><span data-stu-id="05039-487">*major*; *minor*; *build*</span></span>  
  
-   <span data-ttu-id="05039-488">**/VerifyP[ackageID]** _packageID_：</span><span class="sxs-lookup"><span data-stu-id="05039-488">**/VerifyP[ackageID]** _packageID_:</span></span>  
                  <span data-ttu-id="05039-489">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-489">Optional.</span></span> <span data-ttu-id="05039-490">將封裝 GUID 與 *package_id* 引數所指定的值進行比較，藉此驗證要執行之封裝的 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-490">Verifies the GUID of the package to be executed by comparing it to the value specified in the *package_id* argument.</span></span>  
  
-   <span data-ttu-id="05039-491">**/VerifyS[igned]**：</span><span class="sxs-lookup"><span data-stu-id="05039-491">**/VerifyS[igned]**:</span></span>  
                  <span data-ttu-id="05039-492">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-492">Optional.</span></span> <span data-ttu-id="05039-493">使 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 檢查封裝的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="05039-493">Causes [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of the package.</span></span> <span data-ttu-id="05039-494">如果此封裝未簽署或是簽章無效，此封裝就會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-494">If the package is not signed or the signature is not valid, the package fails.</span></span> <span data-ttu-id="05039-495">如需詳細資訊，請參閱 [Identify the Source of Packages with Digital Signatures](../security/identify-the-source-of-packages-with-digital-signatures.md)(使用數位簽章識別封裝來源)。</span><span class="sxs-lookup"><span data-stu-id="05039-495">For more information, see [Identify the Source of Packages with Digital Signatures](../security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="05039-496">當 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 設定為檢查封裝的簽章時，將只會檢查數位簽章是否存在、是否有效，以及是否來自信任的來源。</span><span class="sxs-lookup"><span data-stu-id="05039-496">When configured to check the signature of the package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] only checks whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="05039-497">不會檢查封裝是否經過變更。</span><span class="sxs-lookup"><span data-stu-id="05039-497">does not check whether the package has been changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="05039-498">選擇性的**BlockedSignatureStates**登錄值所指定的設定，可以比中所設定的數位簽章選項更嚴格， [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 或在 `dtexec` 命令列中。</span><span class="sxs-lookup"><span data-stu-id="05039-498">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] or at the `dtexec` command line.</span></span> <span data-ttu-id="05039-499">在此情況下，更具限制性的登錄設定會覆寫其他設定。</span><span class="sxs-lookup"><span data-stu-id="05039-499">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
-   <span data-ttu-id="05039-500">**/VerifyV [ersionID]** _versionID_：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-500">**/VerifyV[ersionID]** _versionID_: Optional.</span></span> <span data-ttu-id="05039-501">在封裝驗證階段期間，將封裝的版本 GUID 與 *version_id* 引數所指定的值進行比較，藉此驗證要執行之封裝的版本 GUID。</span><span class="sxs-lookup"><span data-stu-id="05039-501">Verifies the version GUID of a package to be executed by comparing it to the value specified in the *version_id* argument during package Validation Phase.</span></span>  
  
-   <span data-ttu-id="05039-502">**/VLog** _[Filespec]_：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-502">**/VLog** _[Filespec]_: Optional.</span></span> <span data-ttu-id="05039-503">將所有 Integration Services 封裝事件寫入設計封裝時啟用的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="05039-503">Writes all Integration Services package events to the log providers that were enabled when the package was designed.</span></span> <span data-ttu-id="05039-504">若要讓 Integration Services 啟用文字檔的記錄提供者，並將記錄事件寫入指定的文字檔，請以 *Filespec* 參數的形式包含路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="05039-504">To have Integration Services enable a log provider for text files and write log events to a specified text file, include a path and file name as the *Filespec* parameter.</span></span>  
  
     <span data-ttu-id="05039-505">如果您未包含 *Filespec* 參數，Integration Services 將不會啟用文字檔的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="05039-505">If you do not include the *Filespec* parameter, Integration Services will not enable a log provider for text files.</span></span> <span data-ttu-id="05039-506">Integration Services 只會將記錄事件寫入設計封裝時啟用的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="05039-506">Integration Services will only write log events to the log providers that were enabled when the package was designed.</span></span>  
  
-   <span data-ttu-id="05039-507">**/W [arnAsError]**：</span><span class="sxs-lookup"><span data-stu-id="05039-507">**/W[arnAsError]**:</span></span>  
                  <span data-ttu-id="05039-508">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-508">Optional.</span></span> <span data-ttu-id="05039-509">使封裝將警告視為錯誤，因此，當驗證期間發生警告時，封裝便會失敗。</span><span class="sxs-lookup"><span data-stu-id="05039-509">Causes the package to consider a warning as an error; therefore, the package will fail if a warning occurs during validation.</span></span> <span data-ttu-id="05039-510">若驗證期間未發生警告，亦未指定 **/Validate** 選項，即會執行封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-510">If no warnings occur during validation and the **/Validate** option is not specified, the package is executed.</span></span>  
  
-   <span data-ttu-id="05039-511">**/X86**：選擇性。</span><span class="sxs-lookup"><span data-stu-id="05039-511">**/X86**: Optional.</span></span> <span data-ttu-id="05039-512">使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在 64 位元電腦上以 32 位元模式執行封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-512">Causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run the package in 32-bit mode on a 64-bit computer.</span></span> <span data-ttu-id="05039-513">當下列條件都成立時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就會設定這個選項：</span><span class="sxs-lookup"><span data-stu-id="05039-513">This option is set by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent when the following conditions are true:</span></span>  
  
    -   <span data-ttu-id="05039-514">作業步驟類型是 **[SQL Server Integration Services 封裝]** 。</span><span class="sxs-lookup"><span data-stu-id="05039-514">The job step type is **SQL Server Integration Services package**.</span></span>  
  
    -   <span data-ttu-id="05039-515">已經在 **[新增作業步驟]** 對話方塊的 **[執行選項]** 索引標籤上選取 **[使用 32 位元執行階段]** 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-515">The **Use 32 bit runtime** option on the **Execution options** tab of the **New Job Step** dialog box is selected.</span></span>  
  
     <span data-ttu-id="05039-516">您也可以針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟設定此選項，方法是使用預存程序或 SQL Server 管理物件 (SMO)，以程式設計方式建立作業。</span><span class="sxs-lookup"><span data-stu-id="05039-516">You can also set this option for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step by using stored procedures or SQL Server Management Objects (SMO) to programmatically create the job.</span></span>  
  
     <span data-ttu-id="05039-517">這個選項只能由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用。</span><span class="sxs-lookup"><span data-stu-id="05039-517">This option is only used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="05039-518">如果在命令提示字元處執行 `dtexec` 公用程式，系統將會忽略此選項。</span><span class="sxs-lookup"><span data-stu-id="05039-518">This option is ignored if you run the `dtexec` utility at the command prompt.</span></span>  
  
##  <a name="remarks"></a><a name="remark"></a> <span data-ttu-id="05039-519">備註</span><span class="sxs-lookup"><span data-stu-id="05039-519">Remarks</span></span>  
 <span data-ttu-id="05039-520">命令選項的指定順序可能會影響封裝的執行方式：</span><span class="sxs-lookup"><span data-stu-id="05039-520">The order in which you specify command options can influence the way in which the package executes:</span></span>  
  
-   <span data-ttu-id="05039-521">依照在命令列中發現選項的順序來處理選項。</span><span class="sxs-lookup"><span data-stu-id="05039-521">Options are processed in the order they are encountered on the command line.</span></span> <span data-ttu-id="05039-522">在命令列上發現命令檔案時便會加以讀取，</span><span class="sxs-lookup"><span data-stu-id="05039-522">Command files are read in as they are encountered on the command line.</span></span> <span data-ttu-id="05039-523">命令檔案中的命令也就會依照發現的順序來處理。</span><span class="sxs-lookup"><span data-stu-id="05039-523">The commands in the command file are also processed in the order they are encountered.</span></span>  
  
-   <span data-ttu-id="05039-524">如果相同選項、參數或變數在同一個命令列陳述式中重複出現，以選項的最後一個執行個體優先。</span><span class="sxs-lookup"><span data-stu-id="05039-524">If the same option, parameter, or variable appears in the same command line statement more than one time, the last instance of the option takes precedence.</span></span>  
  
-   <span data-ttu-id="05039-525">**/Set** 與 **/ConfigFile** 選項會依據發現的順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="05039-525">**/Set** and **/ConfigFile** options are processed in the order they are encountered.</span></span>  
  
##  <a name="examples"></a><a name="example"></a> <span data-ttu-id="05039-526">範例</span><span class="sxs-lookup"><span data-stu-id="05039-526">Examples</span></span>  
 <span data-ttu-id="05039-527">下列範例示範如何使用 `dtexec` 命令提示字元公用程式來設定及執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="05039-527">The following examples demonstrate how to use the `dtexec` command prompt utility to configure and execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="05039-528">**[Running Packages]**</span><span class="sxs-lookup"><span data-stu-id="05039-528">**Running Packages**</span></span>  
  
 <span data-ttu-id="05039-529">若要利用 Windows 驗證來執行儲存至 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-529">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Windows Authentication, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer  
```  
  
 <span data-ttu-id="05039-530">若要執行儲存到 SSIS 封裝存放區中檔案系統資料夾的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-530">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package saved to the File System folder in the SSIS Package Store, use the following code:</span></span>  
  
```  
dtexec /dts "\File System\MyPackage"  
```  
  
 <span data-ttu-id="05039-531">若要在不執行封裝的情況下，驗證使用 Windows 驗證且儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-531">To validate a package that uses Windows Authentication and is saved in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without executing the package, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /ser productionServer /va  
```  
  
 <span data-ttu-id="05039-532">若要執行儲存在檔案系統中的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-532">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx"   
```  
  
 <span data-ttu-id="05039-533">若要執行儲存在檔案系統中的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝，且要指定記錄選項，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-533">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system, and specify logging options, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /l "DTS.LogProviderTextFile;c:\log.txt"  
```  
  
 <span data-ttu-id="05039-534">若要執行使用 Windows 驗證、儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的預設本機執行個體，且會在執行之前確認版本的封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-534">To execute a package that uses Windows Authentication and is saved to the default local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and verify the version before it is executed, use the following code:</span></span>  
  
```  
dtexec /sq pkgOne /verifyv {c200e360-38c5-11c5-11ce-ae62-08002b2b79ef}  
```  
  
 <span data-ttu-id="05039-535">若要執行儲存在檔案系統中且在外部進行設定的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="05039-535">To execute an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package that is saved in the file system and configured externally, use the following code:</span></span>  
  
```  
dtexec /f "c:\pkgOne.dtsx" /conf "c:\pkgOneConfig.cfg"  
```  
  
> [!NOTE]  
>  <span data-ttu-id="05039-536">如果路徑或檔案名稱中包含空格，就必須將 /SQL、/DTS 或 /FILE 選項的 *package_path* 或 *filespec* 引數包含在引號中。</span><span class="sxs-lookup"><span data-stu-id="05039-536">The *package_path* or *filespec* arguments of the /SQL, /DTS, or /FILE options must be enclosed in quotation marks if the path or file name contains a space.</span></span> <span data-ttu-id="05039-537">如果引數沒有用引號括住，則引數不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="05039-537">If the argument is not enclosed in quotation marks, the argument cannot contain white space.</span></span>  
  
 <span data-ttu-id="05039-538">**記錄選項**</span><span class="sxs-lookup"><span data-stu-id="05039-538">**Logging Option**</span></span>  
  
 <span data-ttu-id="05039-539">若有三個記錄項目類型 A、B 和 C，下列不含參數的 **ConsoleLog** 選項會顯示這三個記錄類型及其所有欄位：</span><span class="sxs-lookup"><span data-stu-id="05039-539">If there are three log entry types of A, B, and C, the following **ConsoleLog** option without a parameter displays all three log types with all fields:</span></span>  
  
```  
/CONSOLELOG  
```  
  
 <span data-ttu-id="05039-540">下列選項會顯示所有記錄類型，但只會顯示 [名稱] 和 [訊息] 資料行：</span><span class="sxs-lookup"><span data-stu-id="05039-540">The following option displays all log types, but with the Name and Message columns only:</span></span>  
  
```  
/CONSOLELOG NM  
```  
  
 <span data-ttu-id="05039-541">下列選項只會顯示記錄項目類型 A 的所有資料行：</span><span class="sxs-lookup"><span data-stu-id="05039-541">The following option displays all columns, but only for log entry type A:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05039-542">下列選項只會顯示記錄項目類型 A 及其 [名稱] 和 [訊息] 資料行：</span><span class="sxs-lookup"><span data-stu-id="05039-542">The following option displays only log entry type A, with Name and Message columns:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05039-543">下列選項會顯示記錄項目類型 A 和 B 的記錄項目：</span><span class="sxs-lookup"><span data-stu-id="05039-543">The following option displays log entries for log entry types A and B:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA;LogEntryTypeB  
```  
  
 <span data-ttu-id="05039-544">您可以利用多個 **ConsoleLog** 選項來達到相同結果：</span><span class="sxs-lookup"><span data-stu-id="05039-544">You can achieve the same results by using multiple **ConsoleLog** options:</span></span>  
  
```  
/CONSOLELOG I;LogEntryTypeA /CONSOLELOG I;LogEntryTypeB  
```  
  
 <span data-ttu-id="05039-545">若使用 **ConsoleLog** 選項時不含參數，則會顯示所有欄位。</span><span class="sxs-lookup"><span data-stu-id="05039-545">If the **ConsoleLog** option is used without parameters, all fields are displayed.</span></span> <span data-ttu-id="05039-546">若包含 *list_options* 參數會使下列命令只顯示記錄項目 A 及其所有欄位：</span><span class="sxs-lookup"><span data-stu-id="05039-546">The inclusion of a *list_options* parameter causes the following to displays only log entry type A, with all fields:</span></span>  
  
```  
/CONSOLELOG NM;I;LogEntryTypeA /CONSOLELOG  
```  
  
 <span data-ttu-id="05039-547">下列項目會顯示記錄項目類型 A 以外的所有記錄項目；也就是說，它只會顯示記錄項目類型 B 和 C：</span><span class="sxs-lookup"><span data-stu-id="05039-547">The following displays all log entries except log entry type A: that is, it displays log entry types B and C:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA  
```  
  
 <span data-ttu-id="05039-548">下列範例會利用多個 **ConsoleLog** 選項和單一排除項來達到相同結果：</span><span class="sxs-lookup"><span data-stu-id="05039-548">The following example achieves the same results by using multiple **ConsoleLog** options and a single exclusion:</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG E;LogEntryTypeA  
/CONSOLELOG E;LogEntryTypeA;LogEntryTypeA  
```  
  
 <span data-ttu-id="05039-549">下列範例不會顯示任何記錄訊息，因為當記錄檔類型同時在包含和排除的清單中找到時，就會將它排除。</span><span class="sxs-lookup"><span data-stu-id="05039-549">The following example displays no log messages, because when a log file type is found in both the included and excluded lists, it will be excluded.</span></span>  
  
```  
/CONSOLELOG E;LogEntryTypeA /CONSOLELOG I;LogEntryTypeA  
```  
  
 <span data-ttu-id="05039-550">**SET 選項**</span><span class="sxs-lookup"><span data-stu-id="05039-550">**SET Option**</span></span>  
  
 <span data-ttu-id="05039-551">以下顯示如何使用 **/SET** 選項在從命令列啟動封裝時，變更任何封裝屬性或變數的值。</span><span class="sxs-lookup"><span data-stu-id="05039-551">The following example shows how to use the **/SET** option, which lets you change the value of any package property or variable when you start the package from the command line.</span></span>  
  
```  
/SET \package\DataFlowTask.Variables[User::MyVariable].Value;newValue  
```  
  
 <span data-ttu-id="05039-552">**專案選項**</span><span class="sxs-lookup"><span data-stu-id="05039-552">**Project Option**</span></span>  
  
 <span data-ttu-id="05039-553">下列範例顯示如何使用 `/Project` 及 `/Package` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-553">The following example shows how to use the `/Project` and the `/Package` option.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx  
```  
  
 <span data-ttu-id="05039-554">下列範例顯示如何使用 `/Project` 和 `/Package` 選項，以及設定封裝和專案參數。</span><span class="sxs-lookup"><span data-stu-id="05039-554">The following example shows how to use the `/Project` and `/Package` options, and set package and project parameters.</span></span>  
  
```  
/Project c:\project.ispac /Package Package1.dtsx /SET \Package.Variables[$Package::Parameter];1 /SET \Package.Variables[$Project::Parameter];1  
  
```  
  
 <span data-ttu-id="05039-555">**ISServer 選項**</span><span class="sxs-lookup"><span data-stu-id="05039-555">**ISServer Option**</span></span>  
  
 <span data-ttu-id="05039-556">下列範例顯示如何使用 `/ISServer` 選項。</span><span class="sxs-lookup"><span data-stu-id="05039-556">The following example shows how to use the `/ISServer` option.</span></span>  
  
```  
dtexec /isserver "\SSISDB\MyFolder\MyProject\MyPackage.dtsx" /server "."  
```  
  
 <span data-ttu-id="05039-557">下列範例顯示如何使用 `/ISServer` 選項，以及設定專案和連接管理員參數。</span><span class="sxs-lookup"><span data-stu-id="05039-557">The following example shows how to use the `/ISServer` option and set project and connection manager parameters.</span></span>  
  
```  
/Server localhost /ISServer "\SSISDB\MyFolder\Integration Services Project1\Package.dtsx" /Par "$Project::ProjectParameter(Int32)";1 /Par "CM.SourceServer.InitialCatalog";SourceDB  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="05039-558">相關工作</span><span class="sxs-lookup"><span data-stu-id="05039-558">Related Tasks</span></span>  
 [<span data-ttu-id="05039-559">在 SQL Server Data Tools 中執行套件</span><span class="sxs-lookup"><span data-stu-id="05039-559">Run a Package in SQL Server Data Tools</span></span>](../run-a-package-in-sql-server-data-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="05039-560">相關內容</span><span class="sxs-lookup"><span data-stu-id="05039-560">Related Content</span></span>  
 <span data-ttu-id="05039-561">[www.mattmasson.com](www.mattmasson.com) 上的部落格文章： [結束碼、DTEXEC 和 SSIS 目錄](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="05039-561">Blog entry, [Exit Codes, DTEXEC, and SSIS Catalog](https://www.mattmasson.com/2012/02/exit-codes-dtexec-and-ssis-catalog/), on www.mattmasson.com.</span></span>  
  
  
