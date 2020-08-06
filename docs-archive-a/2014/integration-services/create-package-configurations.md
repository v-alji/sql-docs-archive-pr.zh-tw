---
title: 建立套件設定 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, configurations
- Package Configurations Organizer dialog box
- SSIS packages, configurations
- Integration Services packages, configurations
- configurations [Integration Services]
- packages [Integration Services], configurations
- deploying packages [Integration Services], configurations
ms.assetid: 91ac0347-f908-44f5-bd3d-115790223af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 58c93242c9ef51a5e00076bd367e46b43187098e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594611"
---
# <a name="create-package-configurations"></a><span data-ttu-id="6e842-102">Create Package Configurations</span><span class="sxs-lookup"><span data-stu-id="6e842-102">Create Package Configurations</span></span>
  <span data-ttu-id="6e842-103">使用 [封裝組態組合管理]\*\*\*\* 對話方塊和「封裝組態精靈」，可以建立封裝組態。</span><span class="sxs-lookup"><span data-stu-id="6e842-103">You create package configurations by using the **Package Configuration Organizer** dialog box and the Package Configuration Wizard.</span></span> <span data-ttu-id="6e842-104">若要存取這些工具，請在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [SSIS]  功能表中，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-104">To access these tools, click **Package Configurations** on the **SSIS** menu in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e842-105">您也可以按一下 [設定 **] 屬性旁的省略號**按鈕，以存取 [**套件設定召集人**]。</span><span class="sxs-lookup"><span data-stu-id="6e842-105">You can also access the **Package Configuration Organizer**, by clicking the ellipsis button next to the **Configuration** property.</span></span> <span data-ttu-id="6e842-106">[組態] 屬性會顯示在封裝的屬性視窗中。</span><span class="sxs-lookup"><span data-stu-id="6e842-106">The Configuration property appears in the properties window for the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e842-107">組態可用於封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="6e842-107">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="6e842-108">參數是用來取代專案部署模型的組態。</span><span class="sxs-lookup"><span data-stu-id="6e842-108">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="6e842-109">專案部署模型讓您能將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="6e842-109">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="6e842-110">如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6e842-110">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="6e842-111">在 [封裝組態組合管理]  對話方塊中，您可啟用封裝以使用組態、加入和刪除組態，以及設定載入組態的慣用順序。</span><span class="sxs-lookup"><span data-stu-id="6e842-111">In the **Package Configuration Organizer** dialog box, you can enable packages to use configurations, add and delete configurations, and set the preferred order in which configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e842-112">以喜好的順序載入封裝組態時，組態會根據 **[封裝組態組合管理]** 對話方塊中清單顯示的順序 (由上而下) 依序載入。</span><span class="sxs-lookup"><span data-stu-id="6e842-112">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="6e842-113">不過，在執行階段，封裝組態可能不會以喜好的順序載入。</span><span class="sxs-lookup"><span data-stu-id="6e842-113">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="6e842-114">特別是，父封裝組態會在其他類型的組態後面載入。</span><span class="sxs-lookup"><span data-stu-id="6e842-114">In particular, parent package configurations load after configurations of other types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e842-115">如果多個組態設定同一物件屬性，則在執行階段會使用上次載入的值。</span><span class="sxs-lookup"><span data-stu-id="6e842-115">If multiple configurations set the same object property, the value loaded last is used at run time.</span></span>  
  
 <span data-ttu-id="6e842-116">從 [封裝組態組合管理]  對話方塊執行 [封裝組態精靈]，以逐步引導您建立組態。</span><span class="sxs-lookup"><span data-stu-id="6e842-116">From the **Package Configuration Organizer** dialog box, you run the Package Configuration Wizard, which guides you through the steps to create a configuration.</span></span> <span data-ttu-id="6e842-117">若要執行 [封裝組態精靈]，請在 [封裝組態組合管理]  對話方塊中加入新的組態，或編輯現有的組態。</span><span class="sxs-lookup"><span data-stu-id="6e842-117">To run the Package Configuration Wizard, add a new configuration in the **Package Configurations Organizer** dialog box or edit an existing one.</span></span> <span data-ttu-id="6e842-118">在精靈頁面上，選擇組態類型、選取是要直接存取組態還是使用環境變數，並選取要在組態中儲存的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-118">On the wizard pages, you choose the configuration type, select whether you want to access the configuration directly or use environment variables, and select the properties to save in the configuration.</span></span>  
  
 <span data-ttu-id="6e842-119">下列範例會顯示 [封裝組態精靈] 的 [正在完成精靈] 頁面上所顯示之變數及封裝的目標屬性：</span><span class="sxs-lookup"><span data-stu-id="6e842-119">The following example shows the target properties of a variable and a package as they appear on the Completing the Wizard page of the Package Configuration Wizard.:</span></span>  
  
 <span data-ttu-id="6e842-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span><span class="sxs-lookup"><span data-stu-id="6e842-120">\Package.Variables[User::TodaysDate].Properties[RaiseChangedEvent]</span></span>  
  
 <span data-ttu-id="6e842-121">\Package.Properties[MaximumErrorCount]</span><span class="sxs-lookup"><span data-stu-id="6e842-121">\Package.Properties[MaximumErrorCount]</span></span>  
  
 <span data-ttu-id="6e842-122">\Package.Properties[LoggingMode]</span><span class="sxs-lookup"><span data-stu-id="6e842-122">\Package.Properties[LoggingMode]</span></span>  
  
 <span data-ttu-id="6e842-123">\Package.Properties[LocaleID]</span><span class="sxs-lookup"><span data-stu-id="6e842-123">\Package.Properties[LocaleID]</span></span>  
  
 <span data-ttu-id="6e842-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span><span class="sxs-lookup"><span data-stu-id="6e842-124">\Package\My SQL Task.Variables[User::varTableName].Properties[Value]</span></span>  
  
 <span data-ttu-id="6e842-125">在此範例中，此組態會更新以下屬性：</span><span class="sxs-lookup"><span data-stu-id="6e842-125">In this example, the configuration updates these properties:</span></span>  
  
-   <span data-ttu-id="6e842-126">使用者定義變數 `TodaysDate`的 RaiseChangedEvent 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-126">The RaiseChangedEvent property of user-defined variable, `TodaysDate`.</span></span>  
  
-   <span data-ttu-id="6e842-127">封裝的 MaximumErrorCount、LoggingMode 和 LocaleID 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-127">The MaximumErrorCount, LoggingMode, and LocaleID properties of the package.</span></span>  
  
-   <span data-ttu-id="6e842-128">在 My SQL Task 工作範圍內，使用者自訂變數 `varTableName`的 Value 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-128">The Value property of user-defined variable, `varTableName`, within scope of the task, My SQL Task.</span></span>  
  
 <span data-ttu-id="6e842-129">"\Package" 代表根目錄，而句號 (.) 則會分隔物件，這些物件會定義組態所更新之屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="6e842-129">The "\Package" represents the root, and periods (.) separate the objects that define the path to the property that the configuration updates.</span></span> <span data-ttu-id="6e842-130">變數及屬性的值是以方括號括住。</span><span class="sxs-lookup"><span data-stu-id="6e842-130">The names of variables and properties are enclosed in brackets.</span></span> <span data-ttu-id="6e842-131">不論封裝名稱，組態中一律會使用 Package 這個詞彙；然而，路徑中的所有其他物件都會使用它們的使用者自訂名稱。</span><span class="sxs-lookup"><span data-stu-id="6e842-131">The term Package is always used in configuration, regardless of the package name; however, all other objects in the path use their user-defined names.</span></span>  
  
 <span data-ttu-id="6e842-132">在精靈完成後，新組態會加入 [封裝組態組合管理]  對話方塊中的組態清單。</span><span class="sxs-lookup"><span data-stu-id="6e842-132">After the wizard finishes, the new configuration is added to the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e842-133">「封裝組態精靈」的最後一頁，也就是 [正在完成精靈] 頁面，會列出組態中的目標屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-133">The last page in the Package Configuration Wizard, Completing the Wizard, lists the target properties in the configuration.</span></span> <span data-ttu-id="6e842-134">如果您想要在執行封裝時使用 **dtexec** 命令提示公用程式來更新屬性，可以執行封裝組態精靈來產生代表屬性路徑的字串，然後再將這些字串複製並貼到命令提示字元視窗中，以便搭配 **dtexec**的設定選項使用。</span><span class="sxs-lookup"><span data-stu-id="6e842-134">If you want to update properties when you run packages by using the **dtexec** command prompt utility, you can generate the strings that represent the property paths by running the Package Configuration Wizard and then copy and paste them into the command prompt window for use with the set option of **dtexec.**</span></span>  
  
 <span data-ttu-id="6e842-135">下表描述 [封裝組態組合管理]  對話方塊中組態清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="6e842-135">The following table describes the columns in the configuration list in the **Package Configuration Organizer** dialog box.</span></span>  
  
|<span data-ttu-id="6e842-136">資料行</span><span class="sxs-lookup"><span data-stu-id="6e842-136">Column</span></span>|<span data-ttu-id="6e842-137">描述</span><span class="sxs-lookup"><span data-stu-id="6e842-137">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6e842-138">**組態名稱**</span><span class="sxs-lookup"><span data-stu-id="6e842-138">**Configuration Name**</span></span>|<span data-ttu-id="6e842-139">組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e842-139">The name of the configuration.</span></span>|  
|<span data-ttu-id="6e842-140">**組態類型**</span><span class="sxs-lookup"><span data-stu-id="6e842-140">**Configuration Type**</span></span>|<span data-ttu-id="6e842-141">組態類型。</span><span class="sxs-lookup"><span data-stu-id="6e842-141">The configuration type.</span></span>|  
|<span data-ttu-id="6e842-142">**組態字串**</span><span class="sxs-lookup"><span data-stu-id="6e842-142">**Configuration String**</span></span>|<span data-ttu-id="6e842-143">組態的位置。</span><span class="sxs-lookup"><span data-stu-id="6e842-143">The location of the configuration.</span></span> <span data-ttu-id="6e842-144">此位置可以是路徑、環境變數、登錄機碼、父封裝變數名稱或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="6e842-144">The location can be a path, an environment variable, a Registry key, a parent package variable name, or a table in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="6e842-145">**目標物件**</span><span class="sxs-lookup"><span data-stu-id="6e842-145">**Target Object**</span></span>|<span data-ttu-id="6e842-146">具有擁有組態之屬性的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="6e842-146">The name of the object with a property that has a configuration.</span></span> <span data-ttu-id="6e842-147">如果組態為 XML 組態檔，則資料行是空白的，因為該組態可更新多個物件。</span><span class="sxs-lookup"><span data-stu-id="6e842-147">If the configuration is an XML configuration file, the column is blank, because the configuration can update multiple objects.</span></span>|  
|<span data-ttu-id="6e842-148">**目標屬性**</span><span class="sxs-lookup"><span data-stu-id="6e842-148">**Target Property**</span></span>|<span data-ttu-id="6e842-149">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="6e842-149">The name of the property.</span></span> <span data-ttu-id="6e842-150">如果組態寫入 XML 組態檔或 SQL Server 資料表，則資料行是空白的，因為該組態可更新多個物件。</span><span class="sxs-lookup"><span data-stu-id="6e842-150">If the configuration writes to an XML configuration file or a SQL Server table, the column is blank, because the configuration can update multiple objects.</span></span>|  
  
### <a name="to-create-a-package-configuration"></a><span data-ttu-id="6e842-151">建立封裝組態</span><span class="sxs-lookup"><span data-stu-id="6e842-151">To create a package configuration</span></span>  
  
1.  <span data-ttu-id="6e842-152">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="6e842-152">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="6e842-153">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="6e842-153">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="6e842-154">在 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下 [控制流程]  、[資料流程]  、[事件處理常式]  或 [封裝總管]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6e842-154">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, **Event Handler**, or **Package Explorer** tab.</span></span>  
  
4.  <span data-ttu-id="6e842-155">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-155">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
5.  <span data-ttu-id="6e842-156">在 [封裝組態組合管理]  對話方塊中，選取 [啟用封裝組態]  ，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-156">In the **Package Configuration Organizer** dialog box, select **Enable package configurations**, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="6e842-157">在 [封裝組態精靈] 頁面的歡迎頁面上，按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-157">On the welcome page of the Package Configuration Wizard page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="6e842-158">在 [選取組態類型] 頁面上，指定組態類型，然後設定與組態類型相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-158">On the Select Configuration Type page, specify the configuration type, and then set the properties that are relevant to the configuration type.</span></span> <span data-ttu-id="6e842-159">如需詳細資訊，請參閱 [封裝組態精靈 UI 參考](../../2014/integration-services/package-configuration-wizard-ui-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="6e842-159">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
8.  <span data-ttu-id="6e842-160">在 [選取要匯出的屬性] 頁面上，選取要併入組態之封裝物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-160">On the Select Properties to Export page, select the properties of package objects to include in the configuration.</span></span> <span data-ttu-id="6e842-161">如果組態類型僅支援一個屬性，此精靈頁面的標題將為 [選取目標屬性]。</span><span class="sxs-lookup"><span data-stu-id="6e842-161">If the configuration type supports only one property, the title of this wizard page is Select Target Property.</span></span> <span data-ttu-id="6e842-162">如需詳細資訊，請參閱 [封裝組態精靈 UI 參考](../../2014/integration-services/package-configuration-wizard-ui-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="6e842-162">For more information, see [Package Configuration Wizard UI Reference](../../2014/integration-services/package-configuration-wizard-ui-reference.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e842-163">只有 [XML 組態檔]\*\*\*\* 和 [SQL Server]\*\*\*\* 組態類型支援在組態中併入多個屬性。</span><span class="sxs-lookup"><span data-stu-id="6e842-163">Only the **XML Configuration File** and **SQL Server** configuration types support including multiple properties in a configuration.</span></span>  
  
9. <span data-ttu-id="6e842-164">在 [正在完成精靈] 頁面上，輸入組態的名稱，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-164">On the Completing the Wizard page, type the name of the configuration, and then click **Finish**.</span></span>  
  
10. <span data-ttu-id="6e842-165">檢視 [封裝組態組合管理]  對話方塊中的組態。</span><span class="sxs-lookup"><span data-stu-id="6e842-165">View the configuration in the **Package Configuration Organizer** dialog box.</span></span>  
  
11. <span data-ttu-id="6e842-166">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="6e842-166">Click **Close**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6e842-167">外部資源</span><span class="sxs-lookup"><span data-stu-id="6e842-167">External Resources</span></span>  
  
-   <span data-ttu-id="6e842-168">msdn.microsoft.com 上的技術文件： [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643)(了解 Integration Services 封裝組態)</span><span class="sxs-lookup"><span data-stu-id="6e842-168">Technical article, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), on msdn.microsoft.com</span></span>  
  
-   <span data-ttu-id="6e842-169">Www.sqlis.com 上的 Blog 專案，[以程式碼套件設定建立封裝](https://go.microsoft.com/fwlink/?LinkId=217663)。</span><span class="sxs-lookup"><span data-stu-id="6e842-169">Blog entry, [Creating packages in code - Package Configurations](https://go.microsoft.com/fwlink/?LinkId=217663), on www.sqlis.com.</span></span>  
  
-   <span data-ttu-id="6e842-170">Blog 專案， [API 範例-在 blogs.msdn.com 上以程式設計方式將設定檔新增至套件](https://go.microsoft.com/fwlink/?LinkId=217664)。</span><span class="sxs-lookup"><span data-stu-id="6e842-170">Blog entry, [API Sample - Programmatically add a configuration file to a package](https://go.microsoft.com/fwlink/?LinkId=217664), on blogs.msdn.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e842-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e842-171">See Also</span></span>  
 <span data-ttu-id="6e842-172">[套件設定](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="6e842-172">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="6e842-173">[&#40;SSIS&#41;的套件部署](packages/legacy-package-deployment-ssis.md) </span><span class="sxs-lookup"><span data-stu-id="6e842-173">[Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md) </span></span>  
 [<span data-ttu-id="6e842-174">以程式設計方式使用變數</span><span class="sxs-lookup"><span data-stu-id="6e842-174">Working with Variables Programmatically</span></span>](building-packages-programmatically/working-with-variables-programmatically.md)  
  
  
