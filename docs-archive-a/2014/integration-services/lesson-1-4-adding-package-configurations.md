---
title: 步驟 4：新增套件設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e04a5321-63d5-4ec5-85b9-cb4eaf6c87f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 416cf17f967a145fccef1341b77f71a02ff3f3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596134"
---
# <a name="step-4-adding-package-configurations"></a><span data-ttu-id="5c431-102">步驟 4：新增封裝組態</span><span class="sxs-lookup"><span data-stu-id="5c431-102">Step 4: Adding Package Configurations</span></span>
  <span data-ttu-id="5c431-103">在這項工作中，您會為每個封裝加入組態。</span><span class="sxs-lookup"><span data-stu-id="5c431-103">In this task, you will add a configuration to each package.</span></span> <span data-ttu-id="5c431-104">組態會在執行階段更新封裝屬性和封裝物件的值。</span><span class="sxs-lookup"><span data-stu-id="5c431-104">Configurations update the values of package properties and package objects at run time.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="5c431-105">提供各種組態類型。</span><span class="sxs-lookup"><span data-stu-id="5c431-105">provides a variety of configuration types.</span></span> <span data-ttu-id="5c431-106">您可以將組態儲存在環境變數、登錄項目、使用者自訂變數、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表和 XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="5c431-106">You can store configurations in environment variables, registry entries, user-defined variables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables, and XML files.</span></span> <span data-ttu-id="5c431-107">為了提供更大的彈性， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 還支援使用間接組態。</span><span class="sxs-lookup"><span data-stu-id="5c431-107">To provide additional flexibility, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supports the use of indirect configurations.</span></span> <span data-ttu-id="5c431-108">這表示您可以使用環境變數來指定組態的位置，進而指定實際的值。</span><span class="sxs-lookup"><span data-stu-id="5c431-108">This means that you use an environment variable to specify the location of the configuration, which in turn specifies the actual values.</span></span> <span data-ttu-id="5c431-109">「部署教學課程」專案中的封裝會使用 XML 組態檔和間接組態的組合。</span><span class="sxs-lookup"><span data-stu-id="5c431-109">The packages in the Deployment Tutorial project use a combination of XML configuration files and indirect configurations.</span></span> <span data-ttu-id="5c431-110">XML 組態檔可以包含多個屬性的組態，而且在適當的情況下，可以由多個封裝參考。</span><span class="sxs-lookup"><span data-stu-id="5c431-110">An XML configuration file can include configurations for multiple properties, and when appropriate, can be referenced by multiple packages.</span></span> <span data-ttu-id="5c431-111">在這個教學課程中，您會針對各個封裝使用不同的組態檔。</span><span class="sxs-lookup"><span data-stu-id="5c431-111">In this tutorial, you will use a separate configuration file for each package.</span></span>  
  
 <span data-ttu-id="5c431-112">組態檔通常會包含像是連接字串等機密資訊。</span><span class="sxs-lookup"><span data-stu-id="5c431-112">Configuration files frequently contain sensitive information such as connection strings.</span></span> <span data-ttu-id="5c431-113">因此，您應該使用存取控制清單 (ACL) 來限制對儲存檔案所在位置或資料夾的存取，只將存取權授與給允許執行封裝的使用者或帳戶。</span><span class="sxs-lookup"><span data-stu-id="5c431-113">Therefore, you should use an access control list (ACL) to restrict access to the location or folder where you store the files, and give access only to users or accounts that are permitted to run packages.</span></span> <span data-ttu-id="5c431-114">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../../2014/integration-services/access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="5c431-114">For more information, see [Access to Files Used by Packages](../../2014/integration-services/access-to-files-used-by-packages.md).</span></span>  
  
 <span data-ttu-id="5c431-115">您在前一項工作中加入至「部署教學課程」專案的封裝 (DataTransfer 和 LoadXMLData) 需要設定，才能在部署到目標伺服器之後順利執行。</span><span class="sxs-lookup"><span data-stu-id="5c431-115">The packages (DataTransfer and LoadXMLData) that you added to the Deployment Tutorial project in the previous task need configurations to run successfully after they are deployed to the target server.</span></span> <span data-ttu-id="5c431-116">若要實作組態，必須先為 XML 組態檔建立間接組態，然後再建立 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="5c431-116">To implement configurations, you will first create the indirect configurations for the XML configuration files, and then you will create the XML configuration files.</span></span>  
  
 <span data-ttu-id="5c431-117">您將會建立兩個組態檔 DataTransferConfig.dtsConfig 和 LoadXMLData.dtsConfig。</span><span class="sxs-lookup"><span data-stu-id="5c431-117">You will create two configuration files, DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig.</span></span> <span data-ttu-id="5c431-118">這些檔案包含了可更新封裝內屬性的名稱-值組，這些屬性會指定封裝所用之資料檔和記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-118">These files contain name-value pairs that update the properties in packages that specify the location of the data and log files used by the package.</span></span> <span data-ttu-id="5c431-119">在部署程序的稍後步驟中，您將會更新組態檔中的值，以反映這些檔案在目的地電腦上的新位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-119">Later, as a step in the deployment process, you will update the values in the configuration files to reflect the new location of the files on the destination computer.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="5c431-120">知道 DataTransferConfig.dtsConfig 和 LoadXMLData.dtsConfig 是 DataTransfer 和 LoadXMLData 封裝的相依性，因此當您在下一課中建立部署配套時，將會自動包含組態檔。</span><span class="sxs-lookup"><span data-stu-id="5c431-120">recognizes that the DataTransferConfig.dtsConfig and LoadXMLData.dtsConfig are dependencies of the DataTransfer and LoadXMLData packages, and automatically includes the configuration files when you create the deployment bundle in the next lesson.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-datatransfer-package"></a><span data-ttu-id="5c431-121">若要為 DataTransfer 封裝建立間接組態</span><span class="sxs-lookup"><span data-stu-id="5c431-121">To create indirect configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="5c431-122">在 [方案總管] 中，按兩下 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="5c431-122">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="5c431-123">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下控制流程設計介面背景中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-123">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="5c431-124">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-124">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="5c431-125">在 [Package Configuration Organize (封裝組態組合管理)]  對話方塊中，選取 [啟用封裝組態]  (如果尚未選取的話)，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-125">In the **Package Configuration Organize**r dialog box, select **Enable package configurations** if it is not already selected, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="5c431-126">在 [封裝組態精靈] 的歡迎使用頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-126">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="5c431-127">在 [選取設定類型] 頁面上，選取 [設定**類型**] 清單中的 [ **XML 設定檔**]，選取 [設定**位置儲存在環境變數**中] 選項，然後 `DataTransfer,` 在清單中輸入或選取**DataTransfer**環境變數。</span><span class="sxs-lookup"><span data-stu-id="5c431-127">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, and type `DataTransfer,` or select the **DataTransfer** environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c431-128">若要在清單中提供環境變數，可能必須在加入變數之後重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="5c431-128">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span> <span data-ttu-id="5c431-129">如果不想要重新啟動電腦，可以輸入環境變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c431-129">If you do not want to restart the computer, you can type the name of the environment variable.</span></span>  
  
7.  <span data-ttu-id="5c431-130">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-130">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="5c431-131">在 [正在完成精靈] 頁面的 [組態名稱]  方塊中，輸入「DataTransfer 環境變數組態」  、在 [預覽]  窗格中檢閱組態內容，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-131">On the Completing the Wizard page, type **DataTransfer EV Configuration** in the **Configuration name** box, review the configuration contents in the **Preview** pane, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="5c431-132">關閉 [Package Configuration Organize (封裝組態組合管理)]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5c431-132">Close the **Package Configuration Organize**r dialog box.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-datatransfer-package"></a><span data-ttu-id="5c431-133">若要為 DataTransfer 封裝建立 XML 組態</span><span class="sxs-lookup"><span data-stu-id="5c431-133">To create the XML configuration for the DataTransfer package</span></span>  
  
1.  <span data-ttu-id="5c431-134">在 [方案總管] 中，按兩下 DataTransfer.dtsx。</span><span class="sxs-lookup"><span data-stu-id="5c431-134">In Solution Explorer, double-click DataTransfer.dtsx.</span></span>  
  
2.  <span data-ttu-id="5c431-135">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下控制流程設計介面背景中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-135">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="5c431-136">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-136">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="5c431-137">在 [Package Configuration Organizer (封裝組態組合管理)] 對話方塊中，選取 [啟用封裝組態]  核取方塊，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-137">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="5c431-138">在 [封裝組態精靈] 的歡迎使用頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-138">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="5c431-139">在 [選取組態類型] 頁面上，從 [組態類型]  清單中選取 [XML 組態檔]  ，然後按一下 [瀏覽]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-139">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and then click **Browse**.</span></span>  
  
7.  <span data-ttu-id="5c431-140">在 [選取組態檔位置]  對話方塊中，導覽至 C:\DeploymentTutorial 並且在 [檔案名稱]  方塊中輸入 **DataTransferConfig**，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-140">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **DataTransferConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="5c431-141">在 [選取組態類型] 頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-141">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="5c431-142">在 [選取要匯出的屬性] 頁面上，依序展開 [DataTransfer]、[連接管理員]、[Deployment Tutorial Log] 和 [屬性]，然後選取 [連接字串]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c431-142">On the Select Properties to Export page, expand DataTransfer, Connection Managers, Deployment Tutorial Log, and Properties, and then select the **Connection String** check-box.</span></span>  
  
10. <span data-ttu-id="5c431-143">在 [連接管理員] 內，展開 [NewCustomers]，然後選取 [連接字串]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c431-143">Within Connection Managers, expand NewCustomers, and then select the **Connection String** check-box.</span></span>  
  
11. <span data-ttu-id="5c431-144">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-144">Click **Next**.</span></span>  
  
12. <span data-ttu-id="5c431-145">在 [正在完成精靈] 頁面的 [組態名稱]  方塊中，輸入「DataTransfer 組態」  、檢閱組態的內容，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-145">On the Completing the Wizard page, type **DataTransfer Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="5c431-146">在 [Package Configuration Organizer (封裝組態組合管理)]  對話方塊中，確認第一個列出的是「DataTransfer 環境變數組態」，第二個列出的是「DataTransfer 組態」，然後按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-146">In the **Package Configuration Organizer** dialog box, verify that DataTransfer EV Configuration is listed first, and DataTransfer Configuration is listed second, and then click **Close**.</span></span>  
  
### <a name="to-create-indirect-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="5c431-147">若要為 LoadXMLData 封裝建立間接組態</span><span class="sxs-lookup"><span data-stu-id="5c431-147">To create indirect configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="5c431-148">在 [方案總管] 中，按兩下 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="5c431-148">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="5c431-149">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下控制流程設計介面背景中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-149">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="5c431-150">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-150">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="5c431-151">在 [Package Configuration Organize (封裝組態組合管理)]  對話方塊中，按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-151">In the **Package Configuration Organize**r dialog box, Click **Add**.</span></span>  
  
5.  <span data-ttu-id="5c431-152">在 [封裝組態精靈] 的歡迎使用頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-152">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="5c431-153">在 [選取設定類型] 頁面上，選取 [設定**類型**] 清單中的 [ **XML 設定檔**]，選取 [設定**位置儲存在環境變數**中] 選項，然後輸入 `LoadXMLData` 或選取 `LoadXMLData` 清單中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="5c431-153">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list, select the **Configuration location is stored in an environment variable** option, type `LoadXMLData` or select the `LoadXMLData` environment variable in the list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c431-154">若要在清單中提供環境變數，可能必須在加入變數之後重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="5c431-154">To make the environment variable available in the list, you may have to restart your computer after adding the variable.</span></span>  
  
7.  <span data-ttu-id="5c431-155">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-155">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="5c431-156">在 [正在完成精靈] 頁面的 [組態名稱]  方塊中，輸入「LoadXMLData EV 組態」  、檢閱組態的內容，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-156">On the Completing the Wizard page, type **LoadXMLData EV Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
### <a name="to-create-the-xml-configuration-for-the-loadxmldata-package"></a><span data-ttu-id="5c431-157">若要為 LoadXMLData 封裝建立 XML 組態</span><span class="sxs-lookup"><span data-stu-id="5c431-157">To create the XML configuration for the LoadXMLData package</span></span>  
  
1.  <span data-ttu-id="5c431-158">在 [方案總管] 中，按兩下 LoadXMLData.dtsx。</span><span class="sxs-lookup"><span data-stu-id="5c431-158">In Solution Explorer, double-click LoadXMLData.dtsx.</span></span>  
  
2.  <span data-ttu-id="5c431-159">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下控制流程設計介面背景中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="5c431-159">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click anywhere in the background of the control flow design surface.</span></span>  
  
3.  <span data-ttu-id="5c431-160">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-160">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="5c431-161">在 [Package Configuration Organizer (封裝組態組合管理)] 對話方塊中，選取 [啟用封裝組態]  核取方塊，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-161">In the Package Configuration Organizer dialog box, select the **Enable Package Configurations** check-box, and click **Add**.</span></span>  
  
5.  <span data-ttu-id="5c431-162">在 [封裝組態精靈] 的歡迎使用頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-162">On the welcome page of the Package Configuration Wizard, click **Next**.</span></span>  
  
6.  <span data-ttu-id="5c431-163">在 [選取組態類型] 頁面上，從 [組態類型]  清單中選取 [XML 組態檔]  ，然後按一下 [瀏覽]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-163">On the Select Configuration Type page, select **XML configuration file** in the **Configuration type** list and click **Browse**.</span></span>  
  
7.  <span data-ttu-id="5c431-164">在 [選取組態檔位置]  對話方塊中，導覽至 C:\DeploymentTutorial 並且在 [檔案名稱]  方塊中輸入 **LoadXMLDataConfig**，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-164">In **Select Configuration File Location** dialog box, navigate to C:\DeploymentTutorial and type **LoadXMLDataConfig** in the **File name** box, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="5c431-165">在 [選取組態類型] 頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-165">On the Select Configuration Type page, click **Next**.</span></span>  
  
9. <span data-ttu-id="5c431-166">在 [選取要匯出的屬性] 頁面上，依序展開 [LoadXMLData]、[可執行檔]、[載入 XML 資料] 和 [屬性]，然後選取 [[XMLSource].[XMLData]]  和 [[XMLSource].[XMLSchemaDefinition]]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c431-166">On the Select Properties to Export page, expand LoadXMLData, Executables, Load XML Data, and Properties, and then select the **[XMLSource].[XMLData]** and **[XMLSource].[XMLSchemaDefinition]** check boxes.</span></span>  
  
10. <span data-ttu-id="5c431-167">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-167">Click **Next**.</span></span>  
  
11. <span data-ttu-id="5c431-168">在 [正在完成精靈] 頁面的 [組態名稱]  方塊中，輸入「LoadXMLData 組態」  、檢閱組態的內容，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-168">On the Completing the Wizard page, type **LoadXMLData Configuration** in the **Configuration name** box, review the content of the configuration, and then click **Finish**.</span></span>  
  
12. <span data-ttu-id="5c431-169">在 [Package Configuration Organizer (封裝組態組合管理)]  對話方塊中，確認第一個列出的是「LoadXMLData 環境變數組態」，第二個列出的是「LoadXMLData 組態」，然後按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="5c431-169">In the **Package Configuration Organizer** dialog box, verify that the LoadXMLData EV Configuration is listed first, and the LoadXMLData Configuration is listed second, and then click **Close**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="5c431-170">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="5c431-170">Next Task in Lesson</span></span>  
 [<span data-ttu-id="5c431-171">步驟 5：測試更新的套件</span><span class="sxs-lookup"><span data-stu-id="5c431-171">Step 5: Testing the Updated Packages</span></span>](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
<span data-ttu-id="5c431-172">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="5c431-172">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5c431-173">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="5c431-173">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5c431-174">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="5c431-174">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5c431-175">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="5c431-175">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c431-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c431-176">See Also</span></span>  
 <span data-ttu-id="5c431-177">[套件設定](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="5c431-177">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="5c431-178">[建立套件設定](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="5c431-178">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 [<span data-ttu-id="5c431-179">套件所用檔案的存取</span><span class="sxs-lookup"><span data-stu-id="5c431-179">Access to Files Used by Packages</span></span>](../../2014/integration-services/access-to-files-used-by-packages.md)  
  
  
