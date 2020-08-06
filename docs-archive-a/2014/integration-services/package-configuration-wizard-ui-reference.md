---
title: 套件設定向導 UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.configwizard.selectobjects.f1
- sql12.dts.configwizard.selecconfigtype.f1
- sql12.dts.configwizard.finishdtsconfiguration.f1
- sql12.dts.configwizard.welcome.f1
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 222c5f58ca4e942dd23909b433ab346c500fceed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599586"
---
# <a name="package-configuration-wizard-ui-reference"></a><span data-ttu-id="8e2e5-102">封裝組態精靈 UI 參考</span><span class="sxs-lookup"><span data-stu-id="8e2e5-102">Package Configuration Wizard UI Reference</span></span>
  <span data-ttu-id="8e2e5-103">使用 **[封裝組態精靈]** ，即可建立在執行階段更新 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝及其物件之屬性的組態。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-103">Use the **Package Configuration Wizard** to create configurations that update the properties of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and its objects at run time.</span></span> <span data-ttu-id="8e2e5-104">當您在 **[封裝組態組合管理]** 對話方塊中加入新的組態或修改現有的組態時，這個精靈便會執行</span><span class="sxs-lookup"><span data-stu-id="8e2e5-104">This wizard runs when you add a new configuration or modify an existing one in the **Package Configurations Organizer** dialog box.</span></span> <span data-ttu-id="8e2e5-105">若要開啟 **[封裝組態組合管理]** 對話方塊，請在 **中選取** [SSIS] **功能表上的** [封裝組態] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-105">To open the **Package Configurations Organizer** dialog box, select **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8e2e5-106">如需詳細資訊，請參閱 [建立封裝組態](../../2014/integration-services/create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-106">For more information, see [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e2e5-107">組態可用於封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="8e2e5-108">參數是用來取代專案部署模型的組態。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="8e2e5-109">專案部署模型讓您能將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="8e2e5-110">如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="8e2e5-111">下列章節描述精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-111">The following sections describe pages of the Wizard.</span></span>  
  
## <a name="welcome-to-the-package-configuration-wizard-page"></a><span data-ttu-id="8e2e5-112">歡迎使用封裝組態精靈頁面</span><span class="sxs-lookup"><span data-stu-id="8e2e5-112">Welcome to the Package Configuration Wizard Page</span></span>  
 <span data-ttu-id="8e2e5-113">使用 **[SSIS 組態精靈]** ，即可建立在執行階段更新封裝及其物件之屬性的組態。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-113">Use the **SSIS Configuration Wizard** to create configurations that update the properties of a package and its objects at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="8e2e5-114">選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-114">Options</span></span>  
 <span data-ttu-id="8e2e5-115">**不要再顯示此頁面**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-115">**Don't show this page again**</span></span>  
 <span data-ttu-id="8e2e5-116">下次開啟精靈時略過歡迎頁面。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-116">Skip the welcome page the next time you open the wizard.</span></span>  
  
 <span data-ttu-id="8e2e5-117">**下一個**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-117">**Next**</span></span>  
 <span data-ttu-id="8e2e5-118">移至精靈的下一個頁面。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-118">Go the next page in the wizard.</span></span>  
  
## <a name="select-configuration-type-page"></a><span data-ttu-id="8e2e5-119">選取組態類型頁面</span><span class="sxs-lookup"><span data-stu-id="8e2e5-119">Select Configuration Type Page</span></span>  
 <span data-ttu-id="8e2e5-120">使用 **[選取組態類型]** 頁面，即可指定要建立的組態類型。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-120">Use the **Select Configuration Type** page to specify the type of configuration to create.</span></span>  
  
 <span data-ttu-id="8e2e5-121">如果需要其他資訊才可決定要使用的組態類型，請參閱＜ [Package Configurations](../../2014/integration-services/package-configurations.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-121">If you need additional information to determine which type of configuration to use, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="8e2e5-122">靜態選項</span><span class="sxs-lookup"><span data-stu-id="8e2e5-122">Static Options</span></span>  
 <span data-ttu-id="8e2e5-123">**組態類型**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-123">**Configuration type**</span></span>  
 <span data-ttu-id="8e2e5-124">使用下列選項，即可選取儲存組態的來源類型：</span><span class="sxs-lookup"><span data-stu-id="8e2e5-124">Select the type of source in which to store the configuration, using the following options:</span></span>  
  
|<span data-ttu-id="8e2e5-125">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-125">Value</span></span>|<span data-ttu-id="8e2e5-126">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-127">**XML 組態檔**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-127">**XML configuration file**</span></span>|<span data-ttu-id="8e2e5-128">將組態儲存為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-128">Store the configuration as an XML file.</span></span> <span data-ttu-id="8e2e5-129">選取這個值就會顯示 **[組態類型]** 區段中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-129">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="8e2e5-130">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-130">**Environment variable**</span></span>|<span data-ttu-id="8e2e5-131">將組態儲存在其中一個環境變數中。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-131">Store the configuration in one of the environment variables.</span></span> <span data-ttu-id="8e2e5-132">選取這個值就會顯示 **[組態類型]** 區段中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-132">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="8e2e5-133">**登錄項目**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-133">**Registry entry**</span></span>|<span data-ttu-id="8e2e5-134">將組態儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-134">Store the configuration in the Registry.</span></span> <span data-ttu-id="8e2e5-135">選取這個值就會顯示 **[組態類型]** 區段中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-135">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="8e2e5-136">**父封裝變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-136">**Parent package variable**</span></span>|<span data-ttu-id="8e2e5-137">以變數將組態儲存在包含工作的封裝中。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-137">Store the configuration as a variable in the package that contains the task.</span></span>  <span data-ttu-id="8e2e5-138">選取這個值就會顯示 **[組態類型]** 區段中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-138">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
|<span data-ttu-id="8e2e5-139">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-139">**SQL Server**</span></span>|<span data-ttu-id="8e2e5-140">將組態儲存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的資料表中。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-140">Store the configuration in a table in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8e2e5-141">選取這個值就會顯示 **[組態類型]** 區段中的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-141">Selecting this value displays the dynamic options in the section, **Configuration Type**.</span></span>|  
  
 <span data-ttu-id="8e2e5-142">**下一個**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-142">**Next**</span></span>  
 <span data-ttu-id="8e2e5-143">檢視精靈順序的下一頁。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-143">View the next page in the wizard sequence.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="8e2e5-144">動態選項</span><span class="sxs-lookup"><span data-stu-id="8e2e5-144">Dynamic Options</span></span>  
  
#### <a name="configuration-type-option--xml-configuration-file"></a><span data-ttu-id="8e2e5-145">組態類型選項 = XML 組態檔</span><span class="sxs-lookup"><span data-stu-id="8e2e5-145">Configuration Type Option = XML Configuration File</span></span>  
 <span data-ttu-id="8e2e5-146">**直接指定組態設定**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-146">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="8e2e5-147">這可用來直接指定設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-147">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="8e2e5-148">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-148">Value</span></span>|<span data-ttu-id="8e2e5-149">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-150">**組態檔名稱**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-150">**Configuration file name**</span></span>|<span data-ttu-id="8e2e5-151">鍵入精靈產生之組態檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-151">Type the path of the configuration file that the wizard generates.</span></span>|  
|<span data-ttu-id="8e2e5-152">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-152">**Browse**</span></span>|<span data-ttu-id="8e2e5-153">使用 **[選取組態檔位置]** 對話方塊，即可指定精靈產生之組態檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-153">Use the **Select Configuration File Location** dialog box to specify the path of the configuration file that the wizard generates.</span></span> <span data-ttu-id="8e2e5-154">如果檔案不存在，精靈就會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-154">If the file does not exist, it is created by the wizard.</span></span>|  
  
 <span data-ttu-id="8e2e5-155">**組態位置儲存在環境變數中**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-155">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="8e2e5-156">這可用來指定儲存組態的環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-156">Use to specify the environment variable in which to store the configuration.</span></span>  
  
|<span data-ttu-id="8e2e5-157">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-157">Value</span></span>|<span data-ttu-id="8e2e5-158">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-158">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-159">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-159">**Environment variable**</span></span>|<span data-ttu-id="8e2e5-160">從清單中選取環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-160">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--environment-variable"></a><span data-ttu-id="8e2e5-161">組態類型選項 = 環境變數</span><span class="sxs-lookup"><span data-stu-id="8e2e5-161">Configuration Type Option = Environment Variable</span></span>  
 <span data-ttu-id="8e2e5-162">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-162">**Environment variable**</span></span>  
 <span data-ttu-id="8e2e5-163">選取包含組態資訊的環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-163">Select the environment variable that contains the configuration information.</span></span>  
  
#### <a name="configuration-type-option--registry-entry"></a><span data-ttu-id="8e2e5-164">組態類型選項 = 登錄項目</span><span class="sxs-lookup"><span data-stu-id="8e2e5-164">Configuration Type Option = Registry Entry</span></span>  
 <span data-ttu-id="8e2e5-165">**直接指定組態設定**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-165">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="8e2e5-166">這可用來直接指定設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-166">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="8e2e5-167">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-167">Value</span></span>|<span data-ttu-id="8e2e5-168">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-168">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-169">**登錄項目**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-169">**Registry entry**</span></span>|<span data-ttu-id="8e2e5-170">輸入包含組態資訊的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-170">Type the Registry key that contains the configuration information.</span></span> <span data-ttu-id="8e2e5-171">格式為 \<registry key>。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-171">The format is \<registry key>.</span></span><br /><br /> <span data-ttu-id="8e2e5-172">登錄機碼必須已經存在於 HKEY_CURRENT_USER 中且具有名為 Value 的值。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-172">The Registry key must already exist in HKEY_CURRENT_USER and have a value named Value.</span></span> <span data-ttu-id="8e2e5-173">該值可以是 DWORD 或字串。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-173">The value can be a DWORD or a string.</span></span><br /><br /> <span data-ttu-id="8e2e5-174">如果想要使用不是在 HKEY_CURRENT_USER 根目錄的登錄機碼，請使用 \<Registry key\registry key\\...> 格式來識別該機碼。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-174">If you want to use a Registry key is not at the root of HKEY_CURRENT_USER, use the format \<Registry key\registry key\\...> to identify the key.</span></span>|  
  
 <span data-ttu-id="8e2e5-175">**組態位置儲存在環境變數中**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-175">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="8e2e5-176">這可用來指定儲存組態的環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-176">Use to specify the environment variable to store the configuration in.</span></span>  
  
|<span data-ttu-id="8e2e5-177">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-177">Value</span></span>|<span data-ttu-id="8e2e5-178">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-179">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-179">**Environment variable**</span></span>|<span data-ttu-id="8e2e5-180">從清單中選取環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-180">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-option--parent-package-variable"></a><span data-ttu-id="8e2e5-181">組態類型選項 = 父封裝變數</span><span class="sxs-lookup"><span data-stu-id="8e2e5-181">Configuration Type Option = Parent Package Variable</span></span>  
 <span data-ttu-id="8e2e5-182">**直接指定組態設定**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-182">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="8e2e5-183">這可用來直接指定設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-183">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="8e2e5-184">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-184">Value</span></span>|<span data-ttu-id="8e2e5-185">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-185">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-186">**父變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-186">**Parent variable**</span></span>|<span data-ttu-id="8e2e5-187">在包含組態資訊的父封裝中指定變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-187">Specify the variable in the parent package that contains the configuration information.</span></span>|  
  
 <span data-ttu-id="8e2e5-188">**組態位置儲存在環境變數中**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-188">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="8e2e5-189">這可用來指定儲存組態的環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-189">Use to specify the environment variable that stores the configuration.</span></span>  
  
|<span data-ttu-id="8e2e5-190">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-190">Value</span></span>|<span data-ttu-id="8e2e5-191">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-191">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-192">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-192">**Environment variable**</span></span>|<span data-ttu-id="8e2e5-193">從清單中選取環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-193">Select an environment variable from the list.</span></span>|  
  
#### <a name="configuration-type-options--sql-server"></a><span data-ttu-id="8e2e5-194">組態類型選項 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="8e2e5-194">Configuration Type Options = SQL Server</span></span>  
 <span data-ttu-id="8e2e5-195">**直接指定組態設定**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-195">**Specify configuration settings directly**</span></span>  
 <span data-ttu-id="8e2e5-196">這可用來直接指定設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-196">Use to specify settings directly.</span></span>  
  
|<span data-ttu-id="8e2e5-197">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-197">Value</span></span>|<span data-ttu-id="8e2e5-198">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-198">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-199">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-199">**Connection**</span></span>|<span data-ttu-id="8e2e5-200">請從清單中選取連接，或按一下 **[新增]** 即可建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-200">Select a connection from the list, or click **New** to create a new connection.</span></span>|  
|<span data-ttu-id="8e2e5-201">**組態資料表**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-201">**Configuration table**</span></span>|<span data-ttu-id="8e2e5-202">選取現有的資料表，或按一下 **[新增]** ，即可撰寫建立新資料表的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-202">Select an existing table, or click **New** to write a SQL statement that creates a new table.</span></span>|  
|<span data-ttu-id="8e2e5-203">**組態篩選**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-203">**Configuration filter**</span></span>|<span data-ttu-id="8e2e5-204">選取現有的組態名稱或鍵入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-204">Select an existing configuration name or type a new name.</span></span><br /><br /> <span data-ttu-id="8e2e5-205">許多 SQL Server 組態可儲存在相同的資料表中，且每個組態都可包括多個組態項目。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-205">Many SQL Server configurations can be stored in the same table, and each configuration can include multiple configuration items.</span></span><br /><br /> <span data-ttu-id="8e2e5-206">這個使用者自訂值是儲存在資料表中，以識別特定組態所屬的組態項目。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-206">This user-defined value is stored in the table to identify configuration items that belong to a particular configuration</span></span>|  
  
 <span data-ttu-id="8e2e5-207">**組態位置儲存在環境變數中**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-207">**Configuration location is stored in an environment variable**</span></span>  
 <span data-ttu-id="8e2e5-208">這可用來指定儲存組態的環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-208">Use to specify the environment variable where the configuration is stored.</span></span>  
  
|<span data-ttu-id="8e2e5-209">值</span><span class="sxs-lookup"><span data-stu-id="8e2e5-209">Value</span></span>|<span data-ttu-id="8e2e5-210">描述</span><span class="sxs-lookup"><span data-stu-id="8e2e5-210">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e2e5-211">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-211">**Environment variable**</span></span>|<span data-ttu-id="8e2e5-212">從清單中選取環境變數。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-212">Select an environment variable from the list.</span></span>|  
  
## <a name="select-objects-to-export-page"></a><span data-ttu-id="8e2e5-213">選取要匯出的物件頁面</span><span class="sxs-lookup"><span data-stu-id="8e2e5-213">Select Objects to Export Page</span></span>  
 <span data-ttu-id="8e2e5-214">使用 **[選取目標屬性] 或 [選取要匯出的屬性]** 頁面，即可指定組態包含的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-214">Use the **Select Target Property or Select Properties to Export** page to specify the object properties that the configuration contains.</span></span> <span data-ttu-id="8e2e5-215">只有選取 XML 組態類型時，才能選取多個屬性。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-215">The ability to select multiple properties is available only if you select the XML configuration type.</span></span>  
  
### <a name="options"></a><span data-ttu-id="8e2e5-216">選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-216">Options</span></span>  
 <span data-ttu-id="8e2e5-217">**物件**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-217">**Objects**</span></span>  
 <span data-ttu-id="8e2e5-218">展開封裝階層，並選取要匯出的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-218">Expand the package hierarchy and select the properties to export.</span></span>  
  
 <span data-ttu-id="8e2e5-219">**Property 屬性**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-219">**Property attributes**</span></span>  
 <span data-ttu-id="8e2e5-220">檢視屬性 (property) 的屬性 (attribute)。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-220">View the attributes of a property.</span></span>  
  
 <span data-ttu-id="8e2e5-221">**下一個**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-221">**Next**</span></span>  
 <span data-ttu-id="8e2e5-222">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-222">Go to the next page in the wizard.</span></span>  
  
## <a name="completing-the-wizard-page"></a><span data-ttu-id="8e2e5-223">正在完成精靈頁面</span><span class="sxs-lookup"><span data-stu-id="8e2e5-223">Completing the Wizard Page</span></span>  
 <span data-ttu-id="8e2e5-224">使用 **[正在完成精靈]** 頁面，即可提供組態的名稱，並檢視精靈用來建立組態的設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-224">Use the **Completing the Wizard** page to provide a name for the configuration and view settings used by the wizard to create the configuration.</span></span> <span data-ttu-id="8e2e5-225">在精靈完成之後，就會顯示 **[封裝組態組合管理]** ，其中會列出封裝的所有組態。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-225">After the wizard completes, the **Package Configurations Organizer** is displayed, which lists all configurations for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="8e2e5-226">選項。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-226">Options</span></span>  
 <span data-ttu-id="8e2e5-227">**組態名稱**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-227">**Configuration name**</span></span>  
 <span data-ttu-id="8e2e5-228">鍵入組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-228">Type the name of the configuration.</span></span>  
  
 <span data-ttu-id="8e2e5-229">**預覽**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-229">**Preview**</span></span>  
 <span data-ttu-id="8e2e5-230">檢視精靈用來建立組態的設定。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-230">View the settings used by the wizard to create the configuration.</span></span>  
  
 <span data-ttu-id="8e2e5-231">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="8e2e5-231">**Finish**</span></span>  
 <span data-ttu-id="8e2e5-232">建立組態，並結束 [封裝組態精靈]  。</span><span class="sxs-lookup"><span data-stu-id="8e2e5-232">Create the configuration and exit the **Package Configuration Wizard**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e2e5-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e2e5-233">See Also</span></span>  
 [<span data-ttu-id="8e2e5-234">建立套件設定</span><span class="sxs-lookup"><span data-stu-id="8e2e5-234">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
