---
title: 正在執行 Upgrade Advisor (命令提示字元) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], running
- command prompt [Upgrade Advisor]
- UpgradeAdvisorWizardCmd utility
- XML formats [Upgrade Advisor]
ms.assetid: 7c83049b-9227-4723-9b7f-66288bc6bd1d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a968f9d70788e1100af263f3ef9947493b4bd0c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584972"
---
# <a name="running-upgrade-advisor-command-prompt"></a><span data-ttu-id="a4ca9-102">執行 Upgrade Advisor (命令提示字元)</span><span class="sxs-lookup"><span data-stu-id="a4ca9-102">Running Upgrade Advisor (Command Prompt)</span></span>
  <span data-ttu-id="a4ca9-103">使用**UpgradeAdvisorWizardCmd**公用程式，從命令提示字元執行 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-103">Use the **UpgradeAdvisorWizardCmd** utility to run Upgrade Advisor from the command prompt.</span></span> <span data-ttu-id="a4ca9-104">您可以選擇以 XML 格式或含有逗號分隔值的檔案來接收結果。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-104">You can choose to receive results in XML format or in a file with comma-separated values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ca9-105">語法</span><span class="sxs-lookup"><span data-stu-id="a4ca9-105">Syntax</span></span>  
  
```  
  
      UpgradeAdvisorWizardCmd [ -? ]  |   
    [ -ConfigFilefilename | <server_info> ]  
    [ -SqlUserlogin_id-SqlPasswordpassword ]  
    [ -CSV ]  
  
where <server_info> is any combination of the following:  
        -Serverserver_name-Instanceinstance_name-ASInstanceAS_instance_name-RSInstanceRS_instance_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4ca9-106">引數</span><span class="sxs-lookup"><span data-stu-id="a4ca9-106">Arguments</span></span>  
 <span data-ttu-id="a4ca9-107">**-?**</span><span class="sxs-lookup"><span data-stu-id="a4ca9-107">**-?**</span></span>  
 <span data-ttu-id="a4ca9-108">顯示命令語法。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-108">Displays the command syntax.</span></span>  
  
 <span data-ttu-id="a4ca9-109">**-Read-configfile** _filename_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-109">**-ConfigFile** _filename_</span></span>  
 <span data-ttu-id="a4ca9-110">這是 XML 檔案的路徑名稱和檔案名，其中包含當您執行**UpgradeAdvisorWizardCmd**公用程式時所要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-110">Is the path name and file name of an XML file that contains settings to use when you run the **UpgradeAdvisorWizardCmd** utility.</span></span>  
  
 <span data-ttu-id="a4ca9-111">*<server_info>*</span><span class="sxs-lookup"><span data-stu-id="a4ca9-111">*<server_info>*</span></span>  
 <span data-ttu-id="a4ca9-112">指定要分析的電腦和執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-112">Specifies which computer and instance to analyze.</span></span> <span data-ttu-id="a4ca9-113">如果您不要使用組態檔，請使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-113">Use these options if you are not using a configuration file.</span></span>  
  
 <span data-ttu-id="a4ca9-114">*<server_info>* 可以是下列四個引數的任何組合：</span><span class="sxs-lookup"><span data-stu-id="a4ca9-114">*<server_info>* can be any combination of the following four arguments:</span></span>  
  
 <span data-ttu-id="a4ca9-115">**-伺服器** _server_name_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-115">**-Server** _server_name_</span></span>  
 <span data-ttu-id="a4ca9-116">指定要分析之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-116">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="a4ca9-117">這可以是本機電腦 (預設值) 或遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-117">This can be the local computer, which is the default value, or a remote computer.</span></span>  
  
 <span data-ttu-id="a4ca9-118">**-實例** _instance_name_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-118">**-Instance** _instance_name_</span></span>  
 <span data-ttu-id="a4ca9-119">指定要分析之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-119">Specifies the name of the instance to analyze.</span></span> <span data-ttu-id="a4ca9-120">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-120">There is no default value.</span></span> <span data-ttu-id="a4ca9-121">如果您沒有指定這個參數，就不會掃描 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-121">If you do not specify this parameter, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not scanned.</span></span> <span data-ttu-id="a4ca9-122">代表 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體的值為 MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-122">The value for a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is MSSQLSERVER.</span></span> <span data-ttu-id="a4ca9-123">若為具名執行個體，請使用執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-123">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="a4ca9-124">**-ASInstance**  _AS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-124">**-ASInstance**  _AS_instance_name_</span></span>  
 <span data-ttu-id="a4ca9-125">指定要分析之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-125">Specifies the name of the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="a4ca9-126">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-126">There is no default value.</span></span> <span data-ttu-id="a4ca9-127">如果您沒有指定這個值，就不會掃描 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-127">If you do not specify this value, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="a4ca9-128">代表 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 預設執行個體的值為 MSSQLServerOLAPService。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-128">The value for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is MSSQLServerOLAPService.</span></span> <span data-ttu-id="a4ca9-129">若為具名執行個體，請使用執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-129">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="a4ca9-130">**-RSInstance**  _RS_instance_name_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-130">**-RSInstance**  _RS_instance_name_</span></span>  
 <span data-ttu-id="a4ca9-131">指定要分析之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-131">Specifies the name of the instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to analyze.</span></span> <span data-ttu-id="a4ca9-132">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-132">There is no default value.</span></span> <span data-ttu-id="a4ca9-133">如果您沒有指定這個值，就不會掃描 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-133">If you do not specify this value, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not scanned.</span></span> <span data-ttu-id="a4ca9-134">代表 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 預設執行個體的值為 ReportServer。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-134">The value for a default instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is ReportServer.</span></span> <span data-ttu-id="a4ca9-135">若為具名執行個體，請使用執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-135">For a named instance, use the instance name.</span></span>  
  
 <span data-ttu-id="a4ca9-136">**-SqlUser** _login_id_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-136">**-SqlUser** _login_id_</span></span>  
 <span data-ttu-id="a4ca9-137">如果您要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，這個值就是 Upgrade Advisor 將用來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-137">If you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, this value is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that Upgrade Advisor will use to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4ca9-138">如果您沒有指定登入，就會使用 Windows 驗證來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-138">If you do not specify a login, Windows Authentication is used to connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="a4ca9-139">**-SqlPassword** _密碼_</span><span class="sxs-lookup"><span data-stu-id="a4ca9-139">**-SqlPassword** _password_</span></span>  
 <span data-ttu-id="a4ca9-140">如果您使用 **-SqlUser**引數，請使用這個引數來指定登入的密碼 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-140">If you use the **-SqlUser** argument, use this argument to specify the password for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="a4ca9-141">**-CSV**</span><span class="sxs-lookup"><span data-stu-id="a4ca9-141">**-CSV**</span></span>  
 <span data-ttu-id="a4ca9-142">指定除了標準 XML 結果以外，還要將結果當做逗號分隔值提供至 .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-142">Specifies to provide results as comma-separated values to a .csv file in addition to the standard XML results.</span></span> <span data-ttu-id="a4ca9-143">結果會寫入 [我的文件] \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級 upgrade advisor\110\reports 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-143">Results are written to the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports folder.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="a4ca9-144">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4ca9-144">Return Values</span></span>  
 <span data-ttu-id="a4ca9-145">下表顯示**UpgradeAdvisorWizardCmd**所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-145">The following table shows the values that **UpgradeAdvisorWizardCmd** returns.</span></span>  
  
|<span data-ttu-id="a4ca9-146">值</span><span class="sxs-lookup"><span data-stu-id="a4ca9-146">Value</span></span>|<span data-ttu-id="a4ca9-147">描述</span><span class="sxs-lookup"><span data-stu-id="a4ca9-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4ca9-148">0</span><span class="sxs-lookup"><span data-stu-id="a4ca9-148">0</span></span>|<span data-ttu-id="a4ca9-149">分析成功，未找到升級問題。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-149">Analysis succeeded, no upgrade issues found.</span></span>|  
|<span data-ttu-id="a4ca9-150">正整數</span><span class="sxs-lookup"><span data-stu-id="a4ca9-150">positive integer</span></span>|<span data-ttu-id="a4ca9-151">分析成功，找到升級問題。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-151">Analysis succeeded, upgrade issues found.</span></span>|  
|<span data-ttu-id="a4ca9-152">負整數</span><span class="sxs-lookup"><span data-stu-id="a4ca9-152">negative integer</span></span>|<span data-ttu-id="a4ca9-153">分析失敗。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-153">Analysis failed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4ca9-154">備註</span><span class="sxs-lookup"><span data-stu-id="a4ca9-154">Remarks</span></span>  
 <span data-ttu-id="a4ca9-155">除了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證使用者名稱和密碼以外，您可以在 XML 組態檔中提供執行分析所需的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-155">All information that is required to run the analysis, other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication user names and passwords, can be provided in an XML configuration file.</span></span> <span data-ttu-id="a4ca9-156">這個 XML 組態檔記載於範本中。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-156">This XML configuration file is documented in the template.</span></span> <span data-ttu-id="a4ca9-157">如果您沒有使用組態檔，可以透過指定電腦名稱和執行個體名稱，使用預設設定來分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有已安裝的元件。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-157">If you do not use a configuration file, you can analyze all installed components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using default settings by specifying computer names and instance names.</span></span> <span data-ttu-id="a4ca9-158">如需預設組態檔設定的描述，請參閱本主題後面的「元素描述」表。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-158">See the "Element Descriptions" table later in this topic for a description of the default configuration file settings.</span></span>  
  
## <a name="configuration-file-template"></a><span data-ttu-id="a4ca9-159">組態檔範本</span><span class="sxs-lookup"><span data-stu-id="a4ca9-159">Configuration File Template</span></span>  
 <span data-ttu-id="a4ca9-160">您可以使用下列 XML 當做範本，以便建立自己的組態檔。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-160">Use the following XML as a template for creating your own configuration files.</span></span> <span data-ttu-id="a4ca9-161">您可以針對組織的需求來修改此範本。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-161">You can modify the template to meet the needs of your organization.</span></span>  
  
```xml  
<Configuration>  
    <Server> </Server>  
    <Instance></Instance>  
    <Components>  
        <SQLServer>  
            <Databases>  
                <Database></Database>  
            </Databases>  
            <TraceFiles>  
                <TraceFile></TraceFile>  
            </TraceFiles>  
            <BatchFiles>  
                <BatchFile></BatchFile>  
            </BatchFiles>  
            <BatchSeparator></BatchSeparator>  
        </SQLServer>  
        <AnalysisServices>  
            <ASInstance></ASInstance>  
            <Databases>  
                <Database></Database>  
            </Databases>  
        </AnalysisServices>  
        <ReportingServices>  
            <RSInstance></RSInstance>  
        </ReportingServices>  
        <IntegrationServices>  
            <PackagePath></PackagePath>  
        </IntegrationServices>  
    </Components>  
</Configuration>  
```  
  
## <a name="element-descriptions"></a><span data-ttu-id="a4ca9-162">元素描述</span><span class="sxs-lookup"><span data-stu-id="a4ca9-162">Element Descriptions</span></span>  
  
|<span data-ttu-id="a4ca9-163">Tag</span><span class="sxs-lookup"><span data-stu-id="a4ca9-163">Tag</span></span>|<span data-ttu-id="a4ca9-164">定義</span><span class="sxs-lookup"><span data-stu-id="a4ca9-164">Definition</span></span>|<span data-ttu-id="a4ca9-165">出現次數</span><span class="sxs-lookup"><span data-stu-id="a4ca9-165">Occurrence</span></span>|  
|---------|----------------|----------------|  
|`Configuration`|<span data-ttu-id="a4ca9-166">Upgrade Advisor 組態檔的父元素。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-166">Parent element for Upgrade Advisor configuration file.</span></span>|<span data-ttu-id="a4ca9-167">(必要) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-167">Required once per configuration file.</span></span>|  
|`Server`|<span data-ttu-id="a4ca9-168">要分析之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-168">Name of the server to analyze.</span></span>|<span data-ttu-id="a4ca9-169">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-169">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-170">預設值為本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-170">The default value is the local computer.</span></span>|  
|`Instance`|<span data-ttu-id="a4ca9-171">要分析之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-171">Name of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance to analyze.</span></span>|<span data-ttu-id="a4ca9-172">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-172">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-173">預設值為預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-173">The default value is the default instance.</span></span><br /><br /> <span data-ttu-id="a4ca9-174">如果伺服器上出現 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元素或 `IntegrationServices` 元素，則每個組態檔必須出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-174">Required once per configuration file, if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] element or an `IntegrationServices` element is present on the server.</span></span>|  
|`Components`|<span data-ttu-id="a4ca9-175">包含指定要分析之元件的元素。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-175">Contains elements that specify which components to analyze.</span></span>|<span data-ttu-id="a4ca9-176">(必要) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-176">Required once per configuration file.</span></span>|  
|`SQLServer`|<span data-ttu-id="a4ca9-177">包含 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的分析設定。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-177">Contains analysis settings for an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>|<span data-ttu-id="a4ca9-178">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-178">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-179">如果沒有指定，就不會分析 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-179">If not specified, [!INCLUDE[ssDE](../../includes/ssde-md.md)] databases are not analyzed.</span></span>|  
|<span data-ttu-id="a4ca9-180">`Databases` 元素的 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="a4ca9-180">`Databases` for `SQLServer` element</span></span>|<span data-ttu-id="a4ca9-181">包含要分析之資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-181">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="a4ca9-182">每個元素選用一次 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-182">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="a4ca9-183">如果這個元素不存在，就會分析執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-183">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="a4ca9-184">`Database` 元素的 `SQLServer`</span><span class="sxs-lookup"><span data-stu-id="a4ca9-184">`Database` for `SQLServer` element</span></span>|<span data-ttu-id="a4ca9-185">指定要分析之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-185">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="a4ca9-186">(必要) 如果 `Databases` 元素存在，就出現一或多次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-186">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="a4ca9-187">如果 `Database` 元素包含 "\*" 值，就會分析執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-187">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="a4ca9-188">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-188">There is no default value.</span></span>|  
|`TraceFiles`|<span data-ttu-id="a4ca9-189">包含要分析之追蹤檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-189">Contains a list of trace files to analyze.</span></span>|<span data-ttu-id="a4ca9-190">每個元素選用一次 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-190">Optional once per `SQLServer` element.</span></span>|  
|`TraceFile`|<span data-ttu-id="a4ca9-191">指定要分析之追蹤檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-191">Specifies the path and name of a trace file to analyze.</span></span>|<span data-ttu-id="a4ca9-192">(必要) 如果 `TraceFiles` 元素存在，就出現一或多次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-192">Required once or more if the `TraceFiles` element is present.</span></span> <span data-ttu-id="a4ca9-193">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-193">There is no default value.</span></span>|  
|`BatchFiles`|<span data-ttu-id="a4ca9-194">包含要分析之批次檔案的清單。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-194">Contains a list of batch files to analyze.</span></span>|<span data-ttu-id="a4ca9-195">每個元素選用一次 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-195">Optional once per `SQLServer` element.</span></span>|  
|`BatchFile`|<span data-ttu-id="a4ca9-196">指定要分析的批次檔案。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-196">Specifies a batch file to analyze.</span></span> <span data-ttu-id="a4ca9-197">可以有多個。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-197">Can be multiple.</span></span>|<span data-ttu-id="a4ca9-198">(必要) 如果 `BatchFiles` 元素存在，就出現一或多次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-198">Required once or more if the `BatchFiles` element is present.</span></span> <span data-ttu-id="a4ca9-199">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-199">There is no default value.</span></span>|  
|`BatchSeparator`|<span data-ttu-id="a4ca9-200">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 批次檔案中所使用的批次分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-200">Specifies the batch separator used in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch files.</span></span>|<span data-ttu-id="a4ca9-201">每個元素選用一次 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-201">Optional once per `SQLServer` element.</span></span> <span data-ttu-id="a4ca9-202">預設值為 GO。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-202">The default value is GO.</span></span>|  
|`AnalysisServices`|<span data-ttu-id="a4ca9-203">包含 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的分析設定。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-203">Contains analysis settings for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="a4ca9-204">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-204">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-205">如果沒有指定，就不會分析 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-205">If not specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases are not analyzed.</span></span>|  
|`ASInstance`|<span data-ttu-id="a4ca9-206">指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-206">Specifies the name of an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|<span data-ttu-id="a4ca9-207">(必要) 每個 `AnalysisServices` 元素出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-207">Required once per `AnalysisServices` element.</span></span> <span data-ttu-id="a4ca9-208">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-208">There is no default value.</span></span>|  
|<span data-ttu-id="a4ca9-209">`Databases` 元素的 `Analysis Services`</span><span class="sxs-lookup"><span data-stu-id="a4ca9-209">`Databases` for `Analysis Services` element</span></span>|<span data-ttu-id="a4ca9-210">包含要分析之資料庫的清單。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-210">Contains a list of databases to analyze.</span></span>|<span data-ttu-id="a4ca9-211">每個元素選用一次 `AnalysisServices` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-211">Optional once per `AnalysisServices` element.</span></span> <span data-ttu-id="a4ca9-212">如果這個元素不存在，就會分析執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-212">If this element is not present, all databases in the instance are analyzed.</span></span>|  
|<span data-ttu-id="a4ca9-213">`Database` 元素的 `AnalysisServices`</span><span class="sxs-lookup"><span data-stu-id="a4ca9-213">`Database` for `AnalysisServices` element</span></span>|<span data-ttu-id="a4ca9-214">指定要分析之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-214">Specifies the name of a database to analyze.</span></span>|<span data-ttu-id="a4ca9-215">(必要) 如果 `Databases` 元素存在，就出現一或多次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-215">Required once or more if the `Databases` element is present.</span></span> <span data-ttu-id="a4ca9-216">如果 `Database` 元素包含 "\*" 值，就會分析執行個體中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-216">If a `Database` element contains the value "\*", all databases in the instance are analyzed.</span></span> <span data-ttu-id="a4ca9-217">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-217">There is no default value.</span></span>|  
|`ReportingServices`|<span data-ttu-id="a4ca9-218">指定要針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行分析。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-218">Specifies to run analysis against [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="a4ca9-219">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-219">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-220">如果沒有指定，就不會分析 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-220">If not specified, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not analyzed.</span></span>|  
|`RSInstance`|<span data-ttu-id="a4ca9-221">指定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-221">Specifies the name of an instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>|<span data-ttu-id="a4ca9-222">(必要) 每個 `ReportingServices` 元素出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-222">Required once per `ReportingServices` element.</span></span> <span data-ttu-id="a4ca9-223">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-223">There is no default value.</span></span>|  
|`IntegrationServices`|<span data-ttu-id="a4ca9-224">包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的分析設定。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-224">Contains analysis settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>|<span data-ttu-id="a4ca9-225">(選擇性) 每個組態檔出現一次。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-225">Optional once per configuration file.</span></span> <span data-ttu-id="a4ca9-226">如果沒有指定，就不會分析 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-226">If not specified, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is not analyzed.</span></span>|  
|`PackagePath`|<span data-ttu-id="a4ca9-227">指定一組 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的路徑。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-227">Specifies the path of a set of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>|<span data-ttu-id="a4ca9-228">每個元素選用一次 `IntegrationServices` 。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-228">Optional once per `IntegrationServices` element.</span></span> <span data-ttu-id="a4ca9-229">如果這個元素不存在，就會針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體進行分析，而且不會分析儲存於外部的封裝。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-229">If this element is not present, analysis occurs on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, and no externally stored packages are analyzed.</span></span> <span data-ttu-id="a4ca9-230">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-230">There is no default value.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="a4ca9-231">範例</span><span class="sxs-lookup"><span data-stu-id="a4ca9-231">Examples</span></span>  
  
### <a name="a-run-upgrade-advisor-using-a-configuration-file"></a><span data-ttu-id="a4ca9-232">A.</span><span class="sxs-lookup"><span data-stu-id="a4ca9-232">A.</span></span> <span data-ttu-id="a4ca9-233">使用組態檔來執行 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="a4ca9-233">Run Upgrade Advisor Using a Configuration File</span></span>  
 <span data-ttu-id="a4ca9-234">下列範例將示範如何使用指定分析項目的組態檔，從命令提示字元執行 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-234">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file that specifies what to analyze.</span></span> <span data-ttu-id="a4ca9-235">這則範例會使用 Windows 驗證來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-235">This example uses Windows Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"  
```  
  
### <a name="b-run-upgrade-advisor-using-default-configuration-settings"></a><span data-ttu-id="a4ca9-236">B.</span><span class="sxs-lookup"><span data-stu-id="a4ca9-236">B.</span></span> <span data-ttu-id="a4ca9-237">使用預設組態設定來執行 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="a4ca9-237">Run Upgrade Advisor Using Default Configuration Settings</span></span>  
 <span data-ttu-id="a4ca9-238">下列範例將示範如何使用預設組態設定和 Windows 驗證，從命令提示字元執行 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-238">The following example shows how to run Upgrade Advisor from the command prompt by using default configuration settings and Windows Authentication.</span></span>  
  
```  
UpgradeAdvisorWizardCmd -Server MyServer -Instance MyInst   
```  
  
### <a name="c-run-upgrade-advisor-using-ssnoversion-authentication"></a><span data-ttu-id="a4ca9-239">C.</span><span class="sxs-lookup"><span data-stu-id="a4ca9-239">C.</span></span> <span data-ttu-id="a4ca9-240">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來執行 Upgrade Advisor</span><span class="sxs-lookup"><span data-stu-id="a4ca9-240">Run Upgrade Advisor Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication</span></span>  
 <span data-ttu-id="a4ca9-241">下列範例將示範如何使用組態檔，從命令提示字元執行 Upgrade Advisor。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-241">The following example shows how to run Upgrade Advisor from the command prompt by using a configuration file.</span></span> <span data-ttu-id="a4ca9-242">這則範例會指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者名稱和密碼，以便連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4ca9-242">This example specifies a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user name and password to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
UpgradeAdvisorWizardCmd -ConfigFile "C:\My Documents\UpgradeConfig1.xml"   
    -SqlUser "MyUserName" -SqlPassword "QweRTy-55"  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4ca9-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4ca9-243">See Also</span></span>  
 <span data-ttu-id="a4ca9-244">[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="a4ca9-244">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="a4ca9-245">[使用 Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="a4ca9-245">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="a4ca9-246">正在執行 Upgrade Advisor &#40;使用者介面&#41;</span><span class="sxs-lookup"><span data-stu-id="a4ca9-246">Running Upgrade Advisor &#40;User Interface&#41;</span></span>](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)  
  
  
