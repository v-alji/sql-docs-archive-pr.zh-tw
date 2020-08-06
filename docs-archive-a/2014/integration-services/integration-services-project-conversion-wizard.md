---
title: Integration Services 專案轉換向導 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.migrationwizard.f1
ms.assetid: a192b094-4d0f-4c21-b911-460ec844a49f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47dc8ed1d0485a62128be732cc34de1dca35740
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596174"
---
# <a name="integration-services-project-conversion-wizard"></a><span data-ttu-id="19810-102">Integration Services 專案轉換精靈</span><span class="sxs-lookup"><span data-stu-id="19810-102">Integration Services Project Conversion Wizard</span></span>
  <span data-ttu-id="19810-103">[Integration Services 專案轉換精靈]\*\*\*\* 會將專案轉換為專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="19810-103">The **Integration Services Project Conversion Wizard** converts a project to the project deployment model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19810-104">如果專案包含一個或多個資料來源，則在完成專案轉換時，會移除資料來源。</span><span class="sxs-lookup"><span data-stu-id="19810-104">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="19810-105">若要在專案中建立可以透過封裝共用的資料來源連接，請在專案層級加入連接管理員。</span><span class="sxs-lookup"><span data-stu-id="19810-105">To create a connection to a data source that can be shared by the packages in the project, add a connection manager at the project level.</span></span> <span data-ttu-id="19810-106">如需詳細資訊，請參閱 [加入、刪除或共用封裝中的連線管理員](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="19810-106">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
 <span data-ttu-id="19810-107">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="19810-107">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="19810-108">[開啟 [Integration Services 專案轉換精靈]](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="19810-108">[Open the Integration Services Project Conversion Wizard](#open_dialog)</span></span>  
  
-   <span data-ttu-id="19810-109">[設定 [尋找封裝] 頁面上的選項](#locate)</span><span class="sxs-lookup"><span data-stu-id="19810-109">[Set Options on the Locate Packages Page](#locate)</span></span>  
  
-   <span data-ttu-id="19810-110">[設定 [選取封裝] 頁面上的選項](#selectPackages)</span><span class="sxs-lookup"><span data-stu-id="19810-110">[Set Options on the Select Packages Page](#selectPackages)</span></span>  
  
-   <span data-ttu-id="19810-111">[設定 [選取目的地] 頁面上的選項](#destination)</span><span class="sxs-lookup"><span data-stu-id="19810-111">[Set Options on the Select Destination Page](#destination)</span></span>  
  
-   <span data-ttu-id="19810-112">[設定 [指定專案屬性] 頁面上的選項](#projectProperties)</span><span class="sxs-lookup"><span data-stu-id="19810-112">[Set Options on the Specify Project Properties Page](#projectProperties)</span></span>  
  
-   <span data-ttu-id="19810-113">[設定 [更新執行封裝工作] 頁面上的選項](#executePackage)</span><span class="sxs-lookup"><span data-stu-id="19810-113">[Set Options on the Update Execute Package Task Page](#executePackage)</span></span>  
  
-   <span data-ttu-id="19810-114">[在 [選取設定] 頁面上設定選項](#configurations)</span><span class="sxs-lookup"><span data-stu-id="19810-114">[Set Options on the Select Configurations Page](#configurations)</span></span>  
  
-   <span data-ttu-id="19810-115">[設定 [建立參數] 頁面上的選項](#createParameters)</span><span class="sxs-lookup"><span data-stu-id="19810-115">[Set Options on the Create Parameters Page](#createParameters)</span></span>  
  
-   <span data-ttu-id="19810-116">[設定 [設定參數] 頁面上的選項](#configureParameters)</span><span class="sxs-lookup"><span data-stu-id="19810-116">[Set Options on the Configure Parameters Page](#configureParameters)</span></span>  
  
-   <span data-ttu-id="19810-117">[設定 [檢閱] 頁面上的選項](#review)</span><span class="sxs-lookup"><span data-stu-id="19810-117">[Set the Options on the Review page](#review)</span></span>  
  
-   <span data-ttu-id="19810-118">[設定 [執行轉換] 上的選項](#conversion)</span><span class="sxs-lookup"><span data-stu-id="19810-118">[Set the Options on the Perform Conversion](#conversion)</span></span>  
  
##  <a name="open-the-integration-services-project-conversion-wizard"></a><a name="open_dialog"></a><span data-ttu-id="19810-119">開啟 Integration Services 專案轉換向導</span><span class="sxs-lookup"><span data-stu-id="19810-119">Open the Integration Services Project Conversion Wizard</span></span>  
 <span data-ttu-id="19810-120">執行下列其中一項作業來開啟 [Integration Services 專案轉換精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19810-120">Do one of the following to open the **Integration Services Project Conversion** Wizard.</span></span>  
  
-   <span data-ttu-id="19810-121">開啟 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的專案，然後在方案總管中，以滑鼠右鍵按一下該專案，並按一下 [轉換為專案部署模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19810-121">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
-   <span data-ttu-id="19810-122">從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的物件總管中，以滑鼠右鍵按一下 [專案]\*\*\*\* 節點，然後選取 [匯入封裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19810-122">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
 <span data-ttu-id="19810-123">根據您是從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 還是從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行 [Integration Services 專案轉換精靈]\*\*\*\*，此精靈會執行不同的轉換工作。</span><span class="sxs-lookup"><span data-stu-id="19810-123">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span> <span data-ttu-id="19810-124">如需詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="19810-124">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
##  <a name="set-options-on-the-locate-packages-page"></a><a name="locate"></a><span data-ttu-id="19810-125">設定 [尋找封裝] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-125">Set Options on the Locate Packages Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19810-126">只有在您從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 執行此精靈時，才可以使用 [尋找封裝]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="19810-126">The **Locate Packages** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="19810-127">當您選取 [來源]\*\*\*\* 下拉式清單中的 [檔案系統]\*\*\*\* 時，下列選項會顯示在頁面上。</span><span class="sxs-lookup"><span data-stu-id="19810-127">The following option displays on the page when you select **File system** in the **Source** drop-down list.</span></span> <span data-ttu-id="19810-128">當封裝位於檔案系統時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="19810-128">Select this option when the package is resides in the file system.</span></span>  
  
 <span data-ttu-id="19810-129">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="19810-129">**Folder**</span></span>  
 <span data-ttu-id="19810-130">輸入封裝路徑，或按一下 [瀏覽]\*\*\*\* 巡覽到封裝。</span><span class="sxs-lookup"><span data-stu-id="19810-130">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="19810-131">當您選取 [來源]\*\*\*\* 下拉式清單中的 [SSIS 封裝存放區]\*\*\*\* 時，下列選項會顯示在頁面上。</span><span class="sxs-lookup"><span data-stu-id="19810-131">The following options display on the page when you select **SSIS Package Store** in the **Source** drop-down list.</span></span> <span data-ttu-id="19810-132">如需封裝存放區的詳細資訊，請參閱[封裝管理 &#40;SSIS 服務&#41;](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="19810-132">For more information about the package store, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="19810-133">**Server**</span><span class="sxs-lookup"><span data-stu-id="19810-133">**Server**</span></span>  
 <span data-ttu-id="19810-134">輸入伺服器名稱，選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="19810-134">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="19810-135">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="19810-135">**Folder**</span></span>  
 <span data-ttu-id="19810-136">輸入封裝路徑，或按一下 [瀏覽]\*\*\*\* 巡覽到封裝。</span><span class="sxs-lookup"><span data-stu-id="19810-136">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="19810-137">當您選取 [來源]\*\*\*\* 下拉式清單中的 [Microsoft SQL Server]\*\*\*\* 時，下列選項會顯示在頁面上。</span><span class="sxs-lookup"><span data-stu-id="19810-137">The following options display on the page when you select **Microsoft SQL Server** in the **Source** drop-down list.</span></span> <span data-ttu-id="19810-138">當封裝位於 Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="19810-138">Select this option when the package resides in Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="19810-139">**Server**</span><span class="sxs-lookup"><span data-stu-id="19810-139">**Server**</span></span>  
 <span data-ttu-id="19810-140">輸入伺服器名稱，選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="19810-140">Type the server name or select the server.</span></span>  
  
 <span data-ttu-id="19810-141">**使用 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="19810-141">**Use Windows authentication**</span></span>  
 <span data-ttu-id="19810-142">Microsoft Windows 驗證模式允許使用者透過 Windows 使用者帳戶連接。</span><span class="sxs-lookup"><span data-stu-id="19810-142">Microsoft Windows Authentication mode allows a user to connect through a Windows user account.</span></span> <span data-ttu-id="19810-143">如果您使用 Windows 驗證，就不需要提供使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="19810-143">If you use Windows Authentication, you do not need to provide a user name or password.</span></span>  
  
 <span data-ttu-id="19810-144">**使用 SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="19810-144">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="19810-145">當使用者透過不信任連接並指定登入名稱和密碼進行連接時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會驗證此連接，檢查是否已建立該 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入帳戶，而且指定的密碼是否符合先前記錄的密碼。</span><span class="sxs-lookup"><span data-stu-id="19810-145">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authenticates the connection by checking to see if a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="19810-146">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 沒有登入帳戶集，驗證將失敗，而使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="19810-146">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
 <span data-ttu-id="19810-147">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-147">**User name**</span></span>  
 <span data-ttu-id="19810-148">使用 SQL Server 驗證時，請指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-148">Specify a user name when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="19810-149">**密碼**</span><span class="sxs-lookup"><span data-stu-id="19810-149">**Password**</span></span>  
 <span data-ttu-id="19810-150">使用 SQL Server 驗證時，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="19810-150">Provide the password when you are using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="19810-151">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="19810-151">**Folder**</span></span>  
 <span data-ttu-id="19810-152">輸入封裝路徑，或按一下 [瀏覽]\*\*\*\* 巡覽到封裝。</span><span class="sxs-lookup"><span data-stu-id="19810-152">Type the package path, or navigate to the package by clicking **Browse**.</span></span>  
  
##  <a name="set-options-on-the-select-packages-page"></a><a name="selectPackages"></a><span data-ttu-id="19810-153">設定 [選取封裝] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-153">Set Options on the Select Packages Page</span></span>  
 <span data-ttu-id="19810-154">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-154">**Package Name**</span></span>  
 <span data-ttu-id="19810-155">列出封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="19810-155">Lists the package file.</span></span>  
  
 <span data-ttu-id="19810-156">**狀態**</span><span class="sxs-lookup"><span data-stu-id="19810-156">**Status**</span></span>  
 <span data-ttu-id="19810-157">指出封裝是否就緒，可以轉換成專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="19810-157">Indicates whether a package is ready to convert to the project deployment model.</span></span>  
  
 <span data-ttu-id="19810-158">**Message**</span><span class="sxs-lookup"><span data-stu-id="19810-158">**Message**</span></span>  
 <span data-ttu-id="19810-159">顯示與封裝相關聯的訊息。</span><span class="sxs-lookup"><span data-stu-id="19810-159">Displays a message associated with the package.</span></span>  
  
 <span data-ttu-id="19810-160">**密碼**</span><span class="sxs-lookup"><span data-stu-id="19810-160">**Password**</span></span>  
 <span data-ttu-id="19810-161">顯示與封裝相關聯的密碼。</span><span class="sxs-lookup"><span data-stu-id="19810-161">Displays a password associated with the package.</span></span> <span data-ttu-id="19810-162">密碼文字是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="19810-162">The password text is hidden.</span></span>  
  
 <span data-ttu-id="19810-163">**套用至選取項目**</span><span class="sxs-lookup"><span data-stu-id="19810-163">**Apply to selection**</span></span>  
 <span data-ttu-id="19810-164">按一下可將 [密碼]\*\*\*\* 文字方塊中的密碼套用至選取的一個或多個封裝。</span><span class="sxs-lookup"><span data-stu-id="19810-164">Click to apply the password in the **Password** text box, to the selected package or packages.</span></span>  
  
 <span data-ttu-id="19810-165">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="19810-165">**Refresh**</span></span>  
 <span data-ttu-id="19810-166">重新整理封裝的清單。</span><span class="sxs-lookup"><span data-stu-id="19810-166">Refreshes the list of packages.</span></span>  
  
##  <a name="set-options-on-the-select-destination-page"></a><a name="destination"></a><span data-ttu-id="19810-167">設定 [選取目的地] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-167">Set Options on the Select Destination Page</span></span>  
 <span data-ttu-id="19810-168">在此頁面上，指定新專案部署檔案 (.ispac) 的名稱和路徑，或選取現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="19810-168">On this page, specify the name and path for a new project deployment file (.ispac) or select an existing file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19810-169">只有在您從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 執行此精靈時，才可以使用 [選取目的地]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="19810-169">The **Select Destination** page is available only when you run the wizard from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="19810-170">**輸出路徑**</span><span class="sxs-lookup"><span data-stu-id="19810-170">**Output path**</span></span>  
 <span data-ttu-id="19810-171">輸入部署檔案的路徑，或按一下 [瀏覽]\*\*\*\* 巡覽到檔案。</span><span class="sxs-lookup"><span data-stu-id="19810-171">Type the path for the deployment file or navigate to the file by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="19810-172">**專案名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-172">**Project name**</span></span>  
 <span data-ttu-id="19810-173">輸入專案名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-173">Type the project name.</span></span>  
  
 <span data-ttu-id="19810-174">**保護等級**</span><span class="sxs-lookup"><span data-stu-id="19810-174">**Protection level**</span></span>  
 <span data-ttu-id="19810-175">選取保護等級。</span><span class="sxs-lookup"><span data-stu-id="19810-175">Select the protection level.</span></span> <span data-ttu-id="19810-176">如需詳細資訊，請參閱 [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="19810-176">For more information, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="19810-177">**專案描述**</span><span class="sxs-lookup"><span data-stu-id="19810-177">**Project description**</span></span>  
 <span data-ttu-id="19810-178">選擇性地輸入專案的描述。</span><span class="sxs-lookup"><span data-stu-id="19810-178">Type an optional description for the project.</span></span>  
  
##  <a name="set-options-on-the-specify-project-properties-page"></a><a name="projectProperties"></a><span data-ttu-id="19810-179">設定 [指定專案屬性] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-179">Set Options on the Specify Project Properties Page</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19810-180">只有在您從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 執行此精靈時，才可以使用 [指定專案屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="19810-180">The **Specify Project Properties** page is available only when you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="19810-181">**專案名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-181">**Project name**</span></span>  
 <span data-ttu-id="19810-182">列出專案名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-182">Lists the project name.</span></span>  
  
 <span data-ttu-id="19810-183">**保護等級**</span><span class="sxs-lookup"><span data-stu-id="19810-183">**Protection level**</span></span>  
 <span data-ttu-id="19810-184">選取專案中包含之封裝的保護等級。</span><span class="sxs-lookup"><span data-stu-id="19810-184">Select a protection level for the packages contained in the project.</span></span> <span data-ttu-id="19810-185">如需保護等級的詳細資訊，請參閱 [封裝中的敏感性資料存取控制](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="19810-185">For more information about protection levels, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span>  
  
 <span data-ttu-id="19810-186">**專案描述**</span><span class="sxs-lookup"><span data-stu-id="19810-186">**Project description**</span></span>  
 <span data-ttu-id="19810-187">選擇性地輸入專案描述。</span><span class="sxs-lookup"><span data-stu-id="19810-187">Type an optional project description.</span></span>  
  
##  <a name="set-options-on-the-update-execute-package-task-page"></a><a name="executePackage"></a><span data-ttu-id="19810-188">設定 [更新執行封裝工作] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-188">Set Options on the Update Execute Package Task Page</span></span>  
 <span data-ttu-id="19810-189">更新執行封裝工作包含在封裝中，以使用專案參考。</span><span class="sxs-lookup"><span data-stu-id="19810-189">Update Execute Package Tasks contain in the packages, to use a project-based reference.</span></span> <span data-ttu-id="19810-190">如需詳細資訊，請參閱＜ [執行封裝工作編輯器](../../2014/integration-services/execute-package-task-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="19810-190">For more information, see [Execute Package Task Editor](../../2014/integration-services/execute-package-task-editor.md).</span></span>  
  
 <span data-ttu-id="19810-191">**父封裝**</span><span class="sxs-lookup"><span data-stu-id="19810-191">**Parent Package**</span></span>  
 <span data-ttu-id="19810-192">列出使用「執行封裝」工作執行子封裝之封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-192">Lists the name of the package that executes the child package using the Execute Package task.</span></span>  
  
 <span data-ttu-id="19810-193">**工作名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-193">**Task name**</span></span>  
 <span data-ttu-id="19810-194">列出「執行封裝」工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-194">Lists the name of the Execute Package task.</span></span>  
  
 <span data-ttu-id="19810-195">**原始參考**</span><span class="sxs-lookup"><span data-stu-id="19810-195">**Original reference**</span></span>  
 <span data-ttu-id="19810-196">列出子封裝的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="19810-196">Lists the current path of the child package.</span></span>  
  
 <span data-ttu-id="19810-197">**指派參考**</span><span class="sxs-lookup"><span data-stu-id="19810-197">**Assign reference**</span></span>  
 <span data-ttu-id="19810-198">選取專案中儲存的子封裝。</span><span class="sxs-lookup"><span data-stu-id="19810-198">Select a child package stored in the project.</span></span>  
  
##  <a name="set-options-on-the-select-configurations-page"></a><a name="configurations"></a> <span data-ttu-id="19810-199">設定 [選取組態] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-199">Set Options on the Select Configurations Page</span></span>  
 <span data-ttu-id="19810-200">選取您要以參數取代的封裝組態。</span><span class="sxs-lookup"><span data-stu-id="19810-200">Select the package configurations that you want to replace with parameters.</span></span>  
  
 <span data-ttu-id="19810-201">**套件**</span><span class="sxs-lookup"><span data-stu-id="19810-201">**Package**</span></span>  
 <span data-ttu-id="19810-202">列出封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="19810-202">Lists the package file.</span></span>  
  
 <span data-ttu-id="19810-203">**型別**</span><span class="sxs-lookup"><span data-stu-id="19810-203">**Type**</span></span>  
 <span data-ttu-id="19810-204">列出組態類型，例如 XML 組態檔。</span><span class="sxs-lookup"><span data-stu-id="19810-204">Lists the type of configuration, such as an XML configuration file.</span></span>  
  
 <span data-ttu-id="19810-205">**組態字串**</span><span class="sxs-lookup"><span data-stu-id="19810-205">**Configuration String**</span></span>  
 <span data-ttu-id="19810-206">列出組態檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="19810-206">Lists the path of the configuration file.</span></span>  
  
 <span data-ttu-id="19810-207">**狀態**</span><span class="sxs-lookup"><span data-stu-id="19810-207">**Status**</span></span>  
 <span data-ttu-id="19810-208">顯示組態的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="19810-208">Displays a status message for the configuration.</span></span> <span data-ttu-id="19810-209">按一下訊息可檢視完整訊息文字。</span><span class="sxs-lookup"><span data-stu-id="19810-209">Click the message to view the entire message text.</span></span>  
  
 <span data-ttu-id="19810-210">**加入組態**</span><span class="sxs-lookup"><span data-stu-id="19810-210">**Add Configurations**</span></span>  
 <span data-ttu-id="19810-211">將其他專案中包含的封裝組態加入至您要以參數取代的可用組態清單中。</span><span class="sxs-lookup"><span data-stu-id="19810-211">Add package configurations contained in other projects to the list of available configurations that you want to replace with parameters.</span></span> <span data-ttu-id="19810-212">您可以選取儲存在檔案系統或 SQL Server 中的組態。</span><span class="sxs-lookup"><span data-stu-id="19810-212">You can select configurations stored in a file system or stored in SQL Server.</span></span>  
  
 <span data-ttu-id="19810-213">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="19810-213">**Refresh**</span></span>  
 <span data-ttu-id="19810-214">按一下可重新整理組態的清單。</span><span class="sxs-lookup"><span data-stu-id="19810-214">Click to refresh the list of configurations.</span></span>  
  
 <span data-ttu-id="19810-215">**轉換後從所有封裝移除組態**</span><span class="sxs-lookup"><span data-stu-id="19810-215">**Remove configurations from all packages after conversion**</span></span>  
 <span data-ttu-id="19810-216">建議您選取此選項以便從專案中移除所有組態。</span><span class="sxs-lookup"><span data-stu-id="19810-216">It is recommended that you remove all configurations from the project by selecting this option.</span></span>  
  
 <span data-ttu-id="19810-217">如果您沒有選取此選項，則只會移除您選擇以參數取代的組態。</span><span class="sxs-lookup"><span data-stu-id="19810-217">If you don't select this option, only the configurations that you selected to replace with parameters are removed.</span></span>  
  
##  <a name="set-options-on-the-create-parameters-page"></a><a name="createParameters"></a> <span data-ttu-id="19810-218">設定 [建立參數] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-218">Set Options on the Create Parameters Page</span></span>  
 <span data-ttu-id="19810-219">選取每個組態屬性的參數名稱和範圍。</span><span class="sxs-lookup"><span data-stu-id="19810-219">Select the parameter name and scope for each configuration property.</span></span>  
  
 <span data-ttu-id="19810-220">**套件**</span><span class="sxs-lookup"><span data-stu-id="19810-220">**Package**</span></span>  
 <span data-ttu-id="19810-221">列出封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="19810-221">Lists the package file.</span></span>  
  
 <span data-ttu-id="19810-222">**參數名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-222">**Parameter Name**</span></span>  
 <span data-ttu-id="19810-223">列出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-223">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="19810-224">**範圍**</span><span class="sxs-lookup"><span data-stu-id="19810-224">**Scope**</span></span>  
 <span data-ttu-id="19810-225">選取參數的範圍 (封裝或專案)。</span><span class="sxs-lookup"><span data-stu-id="19810-225">Select the scope of the parameter, either package or project.</span></span>  
  
##  <a name="set-options-on-the-configure-parameters-page"></a><a name="configureParameters"></a><span data-ttu-id="19810-226">設定 [設定參數] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-226">Set Options on the Configure Parameters Page</span></span>  
 <span data-ttu-id="19810-227">**名稱**</span><span class="sxs-lookup"><span data-stu-id="19810-227">**Name**</span></span>  
 <span data-ttu-id="19810-228">列出參數名稱。</span><span class="sxs-lookup"><span data-stu-id="19810-228">Lists the parameter name.</span></span>  
  
 <span data-ttu-id="19810-229">**範圍**</span><span class="sxs-lookup"><span data-stu-id="19810-229">**Scope**</span></span>  
 <span data-ttu-id="19810-230">列出參數的範圍。</span><span class="sxs-lookup"><span data-stu-id="19810-230">Lists the scope of the parameter.</span></span>  
  
 <span data-ttu-id="19810-231">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="19810-231">**Value**</span></span>  
 <span data-ttu-id="19810-232">列出參數值。</span><span class="sxs-lookup"><span data-stu-id="19810-232">Lists the parameter value.</span></span>  
  
 <span data-ttu-id="19810-233">按一下值欄位旁邊的省略符號按鈕來設定參數屬性。</span><span class="sxs-lookup"><span data-stu-id="19810-233">Click the ellipsis button next to the value field to configure the parameter properties.</span></span>  
  
 <span data-ttu-id="19810-234">在 [設定參數詳細資料]\*\*\*\* 對話方塊中，您可以編輯參數值。</span><span class="sxs-lookup"><span data-stu-id="19810-234">In the **Set Parameter Details** dialog box, you can edit the parameter value.</span></span> <span data-ttu-id="19810-235">您也可以指定在執行封裝時是否必須提供此參數值。</span><span class="sxs-lookup"><span data-stu-id="19810-235">You can also specify whether the parameter value must be provided when you run the package.</span></span>  
  
 <span data-ttu-id="19810-236">您可以按一下參數旁邊的瀏覽按鈕，在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 之 [設定]\*\*\*\* 對話方塊的 [參數]\*\*\*\* 頁面中修改值。</span><span class="sxs-lookup"><span data-stu-id="19810-236">You can modify value in the **Parameters** page of the **Configure** dialog box in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], by clicking the browse button next to the parameter.</span></span> <span data-ttu-id="19810-237">[設定參數值]\*\*\*\* 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="19810-237">The **Set Parameter Value** dialog box appears.</span></span>  
  
 <span data-ttu-id="19810-238">[設定參數詳細資料]\*\*\*\* 對話方塊也會列出參數值的資料類型，以及參數的來源。</span><span class="sxs-lookup"><span data-stu-id="19810-238">The **Set Parameter Details** dialog box also lists the data type of the parameter value and the origin of the parameter.</span></span>  
  
##  <a name="set-the-options-on-the-review-page"></a><a name="review"></a><span data-ttu-id="19810-239">設定 [審查] 頁面上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-239">Set the Options on the Review page</span></span>  
 <span data-ttu-id="19810-240">使用 [檢閱]\*\*\*\* 頁面確認您已經針對專案的轉換選取的選項。</span><span class="sxs-lookup"><span data-stu-id="19810-240">Use the **Review** page to confirm the options that you've selected for the conversion of the project.</span></span>  
  
 <span data-ttu-id="19810-241">**上一步**</span><span class="sxs-lookup"><span data-stu-id="19810-241">**Previous**</span></span>  
 <span data-ttu-id="19810-242">按一下可變更選項。</span><span class="sxs-lookup"><span data-stu-id="19810-242">Click to change an option.</span></span>  
  
 <span data-ttu-id="19810-243">**轉換**</span><span class="sxs-lookup"><span data-stu-id="19810-243">**Convert**</span></span>  
 <span data-ttu-id="19810-244">按一下可將專案轉換為專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="19810-244">Click to convert the project to the project deployment model.</span></span>  
  
##  <a name="set-the-options-on-the-perform-conversion"></a><a name="conversion"></a><span data-ttu-id="19810-245">設定 [執行轉換] 上的選項</span><span class="sxs-lookup"><span data-stu-id="19810-245">Set the Options on the Perform Conversion</span></span>  
 <span data-ttu-id="19810-246">[執行轉換] 頁面會顯示專案轉換的狀態。</span><span class="sxs-lookup"><span data-stu-id="19810-246">The Perform Conversion page shows status of the project conversion.</span></span>  
  
 <span data-ttu-id="19810-247">**動作**</span><span class="sxs-lookup"><span data-stu-id="19810-247">**Action**</span></span>  
 <span data-ttu-id="19810-248">列出特定的轉換步驟。</span><span class="sxs-lookup"><span data-stu-id="19810-248">Lists a specific conversion step.</span></span>  
  
 <span data-ttu-id="19810-249">**結果**</span><span class="sxs-lookup"><span data-stu-id="19810-249">**Result**</span></span>  
 <span data-ttu-id="19810-250">列出每個轉換步驟的狀態。</span><span class="sxs-lookup"><span data-stu-id="19810-250">Lists the status of each conversion step.</span></span> <span data-ttu-id="19810-251">如需詳細資訊，請按一下狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="19810-251">Click the status message for more information.</span></span>  
  
 <span data-ttu-id="19810-252">在專案儲存到 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中之前，不會儲存專案轉換。</span><span class="sxs-lookup"><span data-stu-id="19810-252">The project conversion is not saved until the project is saved in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="19810-253">**儲存報表**</span><span class="sxs-lookup"><span data-stu-id="19810-253">**Save report**</span></span>  
 <span data-ttu-id="19810-254">按一下可將專案轉換的摘要儲存在 .xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="19810-254">Click to save a summary of the project conversion in an .xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19810-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19810-255">See Also</span></span>  
 [<span data-ttu-id="19810-256">將專案部署至 Integration Services 伺服器</span><span class="sxs-lookup"><span data-stu-id="19810-256">Deploy Projects to Integration Services Server</span></span>](../../2014/integration-services/deploy-projects-to-integration-services-server.md)  
  
  
