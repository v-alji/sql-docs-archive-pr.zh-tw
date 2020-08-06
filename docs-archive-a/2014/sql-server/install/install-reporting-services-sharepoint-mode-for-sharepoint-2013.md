---
title: 安裝 SharePoint 2013 Reporting Services SharePoint 模式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: b29d0f45-0068-4c84-bd7e-5b8a9cd1b538
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9190f990503a66a088351323effa6c17695f9757
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607242"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2013"></a><span data-ttu-id="8466f-102">安裝適用於 SharePoint 2013 的 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="8466f-102">Install Reporting Services SharePoint Mode for SharePoint 2013</span></span>
  <span data-ttu-id="8466f-103">本主題中的程序會引導您完成 SharePoint 模式之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的單一伺服器安裝。</span><span class="sxs-lookup"><span data-stu-id="8466f-103">The procedures in this topic guide you through a single server installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="8466f-104">這些步驟包含執行 [SQL Server 安裝精靈]，以及使用 SharePoint 管理中心的設定工作。</span><span class="sxs-lookup"><span data-stu-id="8466f-104">The steps include running the SQL Server installation wizard as well as configuration tasks that use SharePoint Central Administration.</span></span> <span data-ttu-id="8466f-105">本主題也可以用於更新現有安裝的個別程序，例如建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-105">The topic can also be used for individual procedures for updating an existing installation, for example to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8466f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124;**注意：** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sharepoint 模式不**not**支援 sharepoint Server 多重租用。</span><span class="sxs-lookup"><span data-stu-id="8466f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; **Note:** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode does **not** support SharePoint Server multi-tenancy.</span></span>|  
  
 <span data-ttu-id="8466f-107">如需有關將其他 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器加入至現有伺服器陣列的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="8466f-107">For information on adding more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers to an existing farm, see the following:</span></span>  
  
-   [<span data-ttu-id="8466f-108">將其他報表伺服器加入至伺服器陣列 &#40;SSRS 向外延展&#41;</span><span class="sxs-lookup"><span data-stu-id="8466f-108">Add an Additional Report Server to a Farm &#40;SSRS Scale-out&#41;</span></span>](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
-   [<span data-ttu-id="8466f-109">將其他 Reporting Services Web 前端加入至伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="8466f-109">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 <span data-ttu-id="8466f-110">單一伺服器安裝對開發和測試案例很實用，但是不建議在實際執行環境中使用。</span><span class="sxs-lookup"><span data-stu-id="8466f-110">A single server installation is useful for development and testing scenarios but it is not recommended for production environments.</span></span>  
  
 <span data-ttu-id="8466f-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="8466f-111">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="8466f-112">單一伺服器部署範例</span><span class="sxs-lookup"><span data-stu-id="8466f-112">Example Single-Server Deployment</span></span>](#bkmk_singleserver)  
  
-   [<span data-ttu-id="8466f-113">安裝程式帳戶</span><span class="sxs-lookup"><span data-stu-id="8466f-113">Setup accounts</span></span>](#bkmk_setupaccounts)  
  
-   [<span data-ttu-id="8466f-114">步驟 1：在 SharePoint 模式下安裝 Reporting Services 報表伺服器</span><span class="sxs-lookup"><span data-stu-id="8466f-114">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>](#bkmk_install_SSRS)  
  
-   [<span data-ttu-id="8466f-115">步驟2：註冊並啟動 Reporting Services SharePoint 服務</span><span class="sxs-lookup"><span data-stu-id="8466f-115">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>](#bkmk_install_SSRS_sharedservice)  
  
-   [<span data-ttu-id="8466f-116">步驟3：建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="8466f-116">Step 3: Create a Reporting Services Service Application</span></span>](#bkmk_create_serrviceapplication)  
  
-   [<span data-ttu-id="8466f-117">步驟4：啟動 Power View 網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-117">Step 4: Activate the Power View Site Collection Feature.</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="8466f-118">適用于步驟1-4 的 Windows PowerShell 腳本</span><span class="sxs-lookup"><span data-stu-id="8466f-118">Windows PowerShell script for Steps 1-4</span></span>](#bkmk_full_script)  
  
-   <span data-ttu-id="8466f-119">[Additional Configuration](#bkmk_additional_config) 包括提供訂閱和警示、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 內容類型，以及將 Excel Services 設定為使用 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8466f-119">[Additional Configuration](#bkmk_additional_config) including provisioning for subscriptions and alerts, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] content types, and configuring Excel Services to Use an Analysis Services Server.</span></span>  
  
-   [<span data-ttu-id="8466f-120">驗證安裝</span><span class="sxs-lookup"><span data-stu-id="8466f-120">Verify the installation</span></span>](#bkmk_verify_installation)  
  
##  <a name="example-single-server-deployment"></a><a name="bkmk_singleserver"></a> <span data-ttu-id="8466f-121">單一伺服器部署範例</span><span class="sxs-lookup"><span data-stu-id="8466f-121">Example Single-Server Deployment</span></span>  
 <span data-ttu-id="8466f-122">單一伺服器安裝對開發和測試案例很實用，但是不建議在實際執行環境中使用單一伺服器。</span><span class="sxs-lookup"><span data-stu-id="8466f-122">A single-server installation is useful for development and testing scenarios but a single-server is not recommended for a production environment.</span></span> <span data-ttu-id="8466f-123">單一伺服器環境是指在同一部電腦上安裝 SharePoint 和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的單一電腦。</span><span class="sxs-lookup"><span data-stu-id="8466f-123">The single-server environment refers to a single computer that has SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components installed on the same computer.</span></span> <span data-ttu-id="8466f-124">本主題並未涵蓋具有多部 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器的向外延展。</span><span class="sxs-lookup"><span data-stu-id="8466f-124">The topic does not cover scale-out with multiple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="8466f-125">下圖說明單一伺服器 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署之一部分的元件。</span><span class="sxs-lookup"><span data-stu-id="8466f-125">The following diagram illustrates the components that are part of a single server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deployment.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8466f-126">\*\* (1) \*\*</span><span class="sxs-lookup"><span data-stu-id="8466f-126">**(1)**</span></span>|<span data-ttu-id="8466f-127">從 SQL Server 安裝所安裝的 SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-127">SharePoint service installed from SQL Server installation.</span></span> <span data-ttu-id="8466f-128">您可以建立一個或多個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-128">You can create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>|  
|<span data-ttu-id="8466f-129">\*\* (2) \*\*</span><span class="sxs-lookup"><span data-stu-id="8466f-129">**(2)**</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8466f-130">適用於 SharePoint 產品的增益集會在 SharePoint 伺服器上提供使用者介面元件。</span><span class="sxs-lookup"><span data-stu-id="8466f-130">add-in for SharePoint products provides the user interface components on the SharePoint Servers.</span></span>|  
|<span data-ttu-id="8466f-131">\*\* (3) \*\*</span><span class="sxs-lookup"><span data-stu-id="8466f-131">**(3)**</span></span>|<span data-ttu-id="8466f-132">由 Power View 和 PowerPivot 所使用的 Excel 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-132">The Excel Service Application used by Power View and PowerPivot.</span></span>|  
|<span data-ttu-id="8466f-133">\*\* (4) \*\*</span><span class="sxs-lookup"><span data-stu-id="8466f-133">**(4)**</span></span>|<span data-ttu-id="8466f-134">PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-134">PowerPivot service application.</span></span>|  
  
 <span data-ttu-id="8466f-135">![SSRS SharePoint 模式單一伺服器部署](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint 模式單一伺服器部署")</span><span class="sxs-lookup"><span data-stu-id="8466f-135">![SSRS SharePoint Mode Single Server Deployment](../../../2014/sql-server/install/media/rs-sharepoint-1server-deployment.gif "SSRS SharePoint Mode Single Server Deployment")</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8466f-136"> 如需更多複雜的部署範例，請參閱＜ [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md)＞。</span><span class="sxs-lookup"><span data-stu-id="8466f-136">For more complex deployment examples, see [Deployment Topologies for SQL Server BI Features in SharePoint](deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).</span></span>  
  
##  <a name="setup-accounts"></a><a name="bkmk_setupaccounts"></a> <span data-ttu-id="8466f-137">安裝程式帳戶</span><span class="sxs-lookup"><span data-stu-id="8466f-137">Setup accounts</span></span>  
 <span data-ttu-id="8466f-138">本節將描述用於 SharePoint 模式之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 主要部署步驟的帳戶和權限。</span><span class="sxs-lookup"><span data-stu-id="8466f-138">This section describes the accounts and permissions used for the primary deployment steps of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="8466f-139">**安裝和註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務：**</span><span class="sxs-lookup"><span data-stu-id="8466f-139">**Installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service:**</span></span>  
  
-   <span data-ttu-id="8466f-140">在安裝期間，目前的帳戶 (稱為 SharePoint 模式中的「安裝程式」帳戶) 必須 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 擁有本機電腦的系統管理許可權。</span><span class="sxs-lookup"><span data-stu-id="8466f-140">The current account during the installation (referred to as the 'setup' account) of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode needs to have administrative rights in the local computer.</span></span> <span data-ttu-id="8466f-141">如果您是在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝 sharepoint 之後安裝，而且「安裝程式」帳戶也是 sharepoint 伺服器陣列系統管理員群組的成員，則 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝將會 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 為您註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-141">If you are installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] after SharePoint is installed and the 'setup' account is also a member of the SharePoint farm administrators group, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation will register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service for you.</span></span> <span data-ttu-id="8466f-142">如果您在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝 SharePoint 之前安裝，或者「安裝程式」帳戶不是伺服器陣列管理員群組的成員，您就必須手動註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-142">If you install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] before SharePoint is installed or the 'setup' account is not a member of the farm administrators group, you register the service manually.</span></span> <span data-ttu-id="8466f-143">請參閱＜ [步驟 2：註冊並啟動 Reporting Services SharePoint 服務](#bkmk_install_SSRS_sharedservice)。</span><span class="sxs-lookup"><span data-stu-id="8466f-143">See the section [Step 2: Register and Start the Reporting Services SharePoint Service](#bkmk_install_SSRS_sharedservice).</span></span>  
  
 <span data-ttu-id="8466f-144">**建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式**</span><span class="sxs-lookup"><span data-stu-id="8466f-144">**Creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Applications**</span></span>  
  
-   <span data-ttu-id="8466f-145">安裝並註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務之後，請建立一個或多個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-145">Following installation and registering the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service, create one or more [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="8466f-146">「SharePoint 伺服器陣列服務帳戶」需要暫時成為本機 Administrators 群組的成員，才能建立 Reporting Services 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-146">The "SharePoint farm service account " needs to temporarily be a member of the local administrators group so the Reporting Services service application can be created.</span></span> <span data-ttu-id="8466f-147">如需 SharePoint 2013 帳戶許可權的詳細資訊，請參閱[sharepoint 2013 中的帳戶許可權和安全性設定](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="8466f-147">For more information on SharePoint 2013 account permissions, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx) (https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
     <span data-ttu-id="8466f-148">安全性最佳作法是避免讓 SharePoint 伺服陣列管理員帳戶同時成為本機作業系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-148">It is security best practice that SharePoint farm administrator accounts are not also local operating system administrator accounts.</span></span> <span data-ttu-id="8466f-149">如果您在安裝程序中，將伺服陣列管理員帳戶加入至本機 Administrators 群組，建議您在安裝完成之後，從本機 Administrators 群組中移除該帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-149">If you add a farm admin account to the local administrators group as part of your installation process, it is recommended you remove the account from the local administrators group after installation is complete.</span></span>  
  
##  <a name="step-1-install-reporting-services-report-server-in-sharepoint-mode"></a><a name="bkmk_install_SSRS"></a><span data-ttu-id="8466f-150">步驟1：在 SharePoint 模式中安裝 Reporting Services 報表伺服器</span><span class="sxs-lookup"><span data-stu-id="8466f-150">Step 1: Install Reporting Services Report Server in SharePoint mode</span></span>  
 <span data-ttu-id="8466f-151">這個步驟會在 SharePoint 模式下安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器以及適用於 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="8466f-151">This step installs a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in SharePoint mode and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span> <span data-ttu-id="8466f-152">根據電腦上已經安裝的元件而定，您可能不會看見下列步驟所描述的部分安裝頁面。</span><span class="sxs-lookup"><span data-stu-id="8466f-152">Depending on what is already installed on your computer, you may not see some of the installation pages described in the following steps.</span></span>  
  
1.  <span data-ttu-id="8466f-153">執行 [SQL Server 安裝精靈] \(Setup.exe)。</span><span class="sxs-lookup"><span data-stu-id="8466f-153">Run the SQL Server Installation Wizard (Setup.exe).</span></span>  
  
2.  <span data-ttu-id="8466f-154">在精靈的左側按一下 **[安裝]** ，然後按一下 **[新增 SQL Server 獨立安裝或將功能加入至現有安裝]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-154">Click **Installation** in the left side of the wizard and then click **New SQL Server stand-alone installation or add features to an existing installation**.</span></span>  
  
3.  <span data-ttu-id="8466f-155">在 **[安裝程式支援規則]** 頁面上按一下 **[確定]** (假設已通過所有規則)。</span><span class="sxs-lookup"><span data-stu-id="8466f-155">Click **OK** on the **Setup Support Rules** page, assuming all rules passed.</span></span>  
  
4.  <span data-ttu-id="8466f-156">在 **[安裝程式支援檔案]** 頁面中按一下 **[安裝]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-156">Click **Install** on the **Setup Support Files** page.</span></span> <span data-ttu-id="8466f-157">根據電腦上已經安裝的元件而定，您可能會看見下列訊息：</span><span class="sxs-lookup"><span data-stu-id="8466f-157">Depending on what is already installed on your computer, you might see the following message:</span></span>  
  
    -   <span data-ttu-id="8466f-158">「一個或多個受影響的檔案有暫止的作業。</span><span class="sxs-lookup"><span data-stu-id="8466f-158">"One or more affected files have operations pending.</span></span> <span data-ttu-id="8466f-159">您必須在安裝程序完成之後重新啟動電腦。」</span><span class="sxs-lookup"><span data-stu-id="8466f-159">You must restart your computer after the setup process is completed."</span></span>  
  
    -   <span data-ttu-id="8466f-160">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-160">Click **Ok**.</span></span>  
  
5.  <span data-ttu-id="8466f-161">在支援檔案完成安裝而且 **[支援規則]** 頁面顯示 **[通過]** 狀態之後，請按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-161">Click **Next** after the support files have completed installing and the **Support Rules** pages show a status of **Passed**.</span></span> <span data-ttu-id="8466f-162">檢閱任何警告或封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="8466f-162">Review any warnings or blocking issues.</span></span>  
  
6.  <span data-ttu-id="8466f-163">在 **[安裝類型]** 頁面上，按一下 **[將功能加入到現有的 SQL Server 2014 執行個體]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-163">On the **Installation Type** page, click **Add features to an existing instance of SQL Server 2014**.</span></span> <span data-ttu-id="8466f-164">在下拉式清單中選取正確的執行個體，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-164">Select the correct instance in the drop-down list and click **Next**.</span></span>  
  
7.  <span data-ttu-id="8466f-165">如果您看見 [產品金鑰]\*\*\*\* 頁面，請輸入您的金鑰或接受 "Enterprise Evaluation" 版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="8466f-165">If you see the **Product Key** page, type your key or accept the default of the 'Enterprise Evaluation' edition.</span></span>  
  
     <span data-ttu-id="8466f-166">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-166">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="8466f-167">如果您看見 [授權條款] 頁面，請檢閱並接受這些授權條款。</span><span class="sxs-lookup"><span data-stu-id="8466f-167">If you see the License terms page, review and accept the license terms.</span></span> <span data-ttu-id="8466f-168">Microsoft 感謝您同意傳送功能使用資料，協助改進產品功能及支援。</span><span class="sxs-lookup"><span data-stu-id="8466f-168">Microsoft appreciates you clicking to agree to send feature usage data to help improve product features and support.</span></span>  
  
     <span data-ttu-id="8466f-169">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-169">Click **Next**.</span></span>  
  
9. <span data-ttu-id="8466f-170">如果您看見 **[安裝程式角色]** 頁面，請選取 **[SQL Server 功能安裝]**</span><span class="sxs-lookup"><span data-stu-id="8466f-170">If you see the **Setup Role** page, select **SQL Server Feature Installation**</span></span>  
  
     <span data-ttu-id="8466f-171">按 **[下一步]**</span><span class="sxs-lookup"><span data-stu-id="8466f-171">Click **Next**</span></span>  
  
     <span data-ttu-id="8466f-172">![適用於安裝程式角色的 SQL Server 功能安裝](../../../2014/sql-server/install/media/rs-setuprole.gif "適用於安裝程式角色的 SQL Server 功能安裝")</span><span class="sxs-lookup"><span data-stu-id="8466f-172">![SQL Server Feature Installation for setup role](../../../2014/sql-server/install/media/rs-setuprole.gif "SQL Server Feature Installation for setup role")</span></span>  
  
10. <span data-ttu-id="8466f-173">在 **[特徵選取]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="8466f-173">Select the following on the **Feature Selection** page:</span></span>  
  
    -   <span data-ttu-id="8466f-174">**Reporting Services-SharePoint**</span><span class="sxs-lookup"><span data-stu-id="8466f-174">**Reporting Services - SharePoint**</span></span>  
  
    -   <span data-ttu-id="8466f-175">**適用于 SharePoint 產品的 Reporting Services 增益集**。</span><span class="sxs-lookup"><span data-stu-id="8466f-175">**Reporting Services add-in for SharePoint Products**.</span></span>  
  
         <span data-ttu-id="8466f-176">![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")安裝增益集的 [安裝精靈] 選項是版本的新功能 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-176">![note](../../../2014/reporting-services/media/rs-fyinote.png "note") The installation wizard option for installing the add-in is new with the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release.</span></span>  
  
    -   <span data-ttu-id="8466f-177">如果您尚未有 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體，您也可以針對完整的環境選取 **[Database Engine Services]** 和 **[管理工具 - 完整]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-177">If you do not already have an instance of SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], you could also select **Database Engine Services** and **Management Tools Complete** for a complete environment.</span></span>  
  
     <span data-ttu-id="8466f-178">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-178">Click **Next**.</span></span>  
  
     <span data-ttu-id="8466f-179">![適用于 SharePoint 模式的 SSRS 功能選取](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "適用于 SharePoint 模式的 SSRS 功能選取")</span><span class="sxs-lookup"><span data-stu-id="8466f-179">![SSRS Feature Selection for SharePoint mode](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "SSRS Feature Selection for SharePoint mode")</span></span>  
  
11. <span data-ttu-id="8466f-180">如果您看見 **[安裝規則]** 頁面，</span><span class="sxs-lookup"><span data-stu-id="8466f-180">If you see the **Installation Rules** page.</span></span> <span data-ttu-id="8466f-181">檢閱任何警告或封鎖問題。</span><span class="sxs-lookup"><span data-stu-id="8466f-181">Review any warnings or blocking issues.</span></span> <span data-ttu-id="8466f-182">然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="8466f-182">Then click **Next**</span></span>  
  
12. <span data-ttu-id="8466f-183">如果您選取 Database Engine 服務，請接受 **[執行個體組態]** 頁面上的預設 **[MSSQLSERVER]** 執行個體，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-183">If you selected the Database Engine services, accept the default instance of **MSSQLSERVER** on the **Instance Configuration** page and click **Next**.</span></span>  
  
     <span data-ttu-id="8466f-184">![注意](../../../2014/reporting-services/media/rs-fyinote.png "注意")Reporting Services SharePoint 服務架構不以 SQL Server「執行個體」為基礎，和舊版的 Reporting Services 架構不同。</span><span class="sxs-lookup"><span data-stu-id="8466f-184">![note](../../../2014/reporting-services/media/rs-fyinote.png "note")The Reporting Services SharePoint service architecture is not based on a SQL Server "instance" as was the previous Reporting Services architecture.</span></span>  
  
13. <span data-ttu-id="8466f-185">檢閱 **[磁碟空間需求]** 頁面，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-185">Review the **Disk Space Requirements** page and click **Next**.</span></span>  
  
14. <span data-ttu-id="8466f-186">如果您看見 **[伺服器組態]** 頁面，請輸入適當的認證。</span><span class="sxs-lookup"><span data-stu-id="8466f-186">If you see the **Server Configuration** page type appropriate credentials.</span></span> <span data-ttu-id="8466f-187">如果您想要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示或訂閱功能，則必須將 SQL Server Agent 的 **[啟動類型]** 變更為 **[自動]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-187">If you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerting or subscription features, you need to change the **Startup Type** for SQL Server Agent to **Automatic**.</span></span> <span data-ttu-id="8466f-188">根據電腦上已經安裝的元件而定，您可能不會看見 **[伺服器組態]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="8466f-188">You may not see the **Server Configuration** page, depending on what is already installed on the computer.</span></span>  
  
     <span data-ttu-id="8466f-189">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-189">Click **Next**.</span></span>  
  
15. <span data-ttu-id="8466f-190">如果您選取了 Database Engine 服務，就會看到 **[資料庫引擎組態]** 頁面。請將適當的帳戶加入至 SQL 管理員清單，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-190">If you selected the Database Engine services, you will see the **Database Engine Configuration** page, add appropriate accounts to the list of SQL Administrators and click **Next**.</span></span>  
  
16. <span data-ttu-id="8466f-191">在 **[Reporting Services 組態]** 頁面上，您應該會看到已選取 **[只安裝]** 選項。</span><span class="sxs-lookup"><span data-stu-id="8466f-191">On the **Reporting Services Configuration** page you should see the **Install only** option is selected.</span></span> <span data-ttu-id="8466f-192">這個選項會安裝報表伺服器檔案，但是不會設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]的 SharePoint 環境。</span><span class="sxs-lookup"><span data-stu-id="8466f-192">This option installs the report server files, and does not configure the SharePoint environment for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8466f-193">當 SQL Server 安裝完成時，請遵循本主題其他章節來設定 SharePoint 環境。</span><span class="sxs-lookup"><span data-stu-id="8466f-193">When the SQL Server installation is complete, follow the other sections of this topic to configure the SharePoint environment.</span></span> <span data-ttu-id="8466f-194">包括安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共用服務及建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-194">This Includes installing the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service and creating [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span>  
  
     <span data-ttu-id="8466f-195">![SQL Server 安裝精靈 - SSRS 組態頁面](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server 安裝精靈 - SSRS 組態頁面")</span><span class="sxs-lookup"><span data-stu-id="8466f-195">![SQL Server Setup Wizard - SSRS Configuration Page](../../../2014/sql-server/install/media/rs-2012sp1-setup-ssrs-configpage-with-circles.gif "SQL Server Setup Wizard - SSRS Configuration Page")</span></span>  
  
17. <span data-ttu-id="8466f-196">按一下 **[錯誤報告]** 頁面上的核取方塊傳送錯誤報告，協助 Microsoft 改進 SQL Server 功能與服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-196">Help Microsoft improve SQL Server features and services by clicking the check box to send error reports on the **Error Reporting** page.</span></span>  
  
     <span data-ttu-id="8466f-197">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-197">Click **Next**.</span></span>  
  
18. <span data-ttu-id="8466f-198">檢閱任何警告，然後在 **[安裝組態規則]** 頁面上按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-198">Review any warnings and then click **Next** on the **Installation Configuration Rules** page.</span></span>  
  
19. <span data-ttu-id="8466f-199">在 **[準備安裝]** 頁面上檢閱安裝摘要，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-199">On the **Ready to Install** page, review the installation summary and then click **Next**.</span></span> <span data-ttu-id="8466f-200">此摘要將包括其值顯示為 **[SharePointFilesOnlyMode]** 的 **[Reporting Services SharePoint 模式]** 子節點。</span><span class="sxs-lookup"><span data-stu-id="8466f-200">The summary will include a **Reporting Services SharePoint Mode** child node that will show a value of **SharePointFilesOnlyMode**.</span></span> <span data-ttu-id="8466f-201">按一下 [安裝] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-201">Click **Install**.</span></span>  
  
20. <span data-ttu-id="8466f-202">安裝需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="8466f-202">The installation will take several minutes.</span></span> <span data-ttu-id="8466f-203">您將會看見 **[完成]** 頁面，其中列出功能以及每項功能的狀態。</span><span class="sxs-lookup"><span data-stu-id="8466f-203">You will see the **Complete** page with the features listed and the status of each feature.</span></span> <span data-ttu-id="8466f-204">您可能會看見資訊對話方塊，指出電腦需要重新啟動。</span><span class="sxs-lookup"><span data-stu-id="8466f-204">You may see an information dialog indicating the computer needs to be restarted.</span></span>  
  
##  <a name="step-2-register-and-start-the-reporting-services-sharepoint-service"></a><a name="bkmk_install_SSRS_sharedservice"></a> <span data-ttu-id="8466f-205">步驟 2：註冊並啟動 Reporting Services SharePoint 服務</span><span class="sxs-lookup"><span data-stu-id="8466f-205">Step 2: Register and Start the Reporting Services SharePoint Service</span></span>  
 <span data-ttu-id="8466f-206">![PowerShell 相關內容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="8466f-206">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8466f-207">如果您要在現有的 SharePoint 伺服器陣列中進行安裝，則不需要完成本節中的步驟。</span><span class="sxs-lookup"><span data-stu-id="8466f-207">If you are installing into an existing SharePoint farm, you do not need to complete the steps in this section.</span></span> <span data-ttu-id="8466f-208">當您在本文件的上一節執行 SQL Server 安裝精靈時，就會安裝並啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-208">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint service is installed and started when you ran the SQL Server installation wizard as part of the previous section of this document.</span></span>  
  
 <span data-ttu-id="8466f-209">您需要手動註冊 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務的常見原因如下。</span><span class="sxs-lookup"><span data-stu-id="8466f-209">The following are the common reasons why you need to manually register the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="8466f-210">您在安裝 SharePoint 之前已安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="8466f-210">You installed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode before SharePoint was installed.</span></span>  
  
-   <span data-ttu-id="8466f-211">此用來安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的帳戶，不是 SharePoint 伺服器陣列管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="8466f-211">The account used to install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, was not a member of the SharePoint farm administrators group.</span></span> <span data-ttu-id="8466f-212">如需詳細資訊，請參閱＜ [Setup accounts](#bkmk_setupaccounts)＞一節。</span><span class="sxs-lookup"><span data-stu-id="8466f-212">For more information, see the section [Setup accounts](#bkmk_setupaccounts).</span></span>  
  
 <span data-ttu-id="8466f-213">必要檔案會隨 [SQL Server 安裝精靈] 安裝，但是您必須在 SharePoint 伺服器陣列中註冊服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-213">The necessary files were installed as part of the SQL Server installation wizard, but the services need to be registered into the SharePoint farm.</span></span> <span data-ttu-id="8466f-214">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 版本引進了適用於 SharePoint 模式中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 PowerShell 支援。</span><span class="sxs-lookup"><span data-stu-id="8466f-214">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] release introduces PowerShell support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span>  
  
 <span data-ttu-id="8466f-215">下列步驟將引導您開啟 SharePoint 管理命令介面並執行指令程式：</span><span class="sxs-lookup"><span data-stu-id="8466f-215">The following steps guide you through opening the SharePoint Management Shell and running cmdlets:</span></span>  
  
1.  <span data-ttu-id="8466f-216">按一下 [**開始**] 按鈕</span><span class="sxs-lookup"><span data-stu-id="8466f-216">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="8466f-217">按一下 **[Microsoft SharePoint 2013 產品]** 群組。</span><span class="sxs-lookup"><span data-stu-id="8466f-217">Click the **Microsoft SharePoint 2013 Products** group.</span></span>  
  
3.  <span data-ttu-id="8466f-218">以滑鼠右鍵按一下 **[SharePoint 2013 管理命令介面]** ，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-218">Right-click **SharePoint 2013 Management Shell** click **Run as administrator**.</span></span> <span data-ttu-id="8466f-219">注意：標準 Windows PowerShell 視窗無法辨識 SharePoint 命令。</span><span class="sxs-lookup"><span data-stu-id="8466f-219">NOTE: the SharePoint commands are not recognized in the standard Windows PowerShell window.</span></span> <span data-ttu-id="8466f-220">請使用 **[SharePoint 2013 管理命令介面]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-220">Use the **SharePoint 2013 Management Shell**.</span></span>  
  
4.  <span data-ttu-id="8466f-221">執行下列 PowerShell 命令安裝 SharePoint 服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-221">Run the following PowerShell command to install the SharePoint service.</span></span> <span data-ttu-id="8466f-222">成功完成命令會在管理命令介面中顯示新行。</span><span class="sxs-lookup"><span data-stu-id="8466f-222">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="8466f-223">成功完成命令之後，**不會有任何訊息傳回** 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="8466f-223">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSService  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8466f-224">如果您看到類似下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="8466f-224">If you see an error message similar to the following:</span></span>  
    >   
    >  <span data-ttu-id="8466f-225">安裝-Install-sprsserviceinstall-sprsservice： ' Install-Install-sprsserviceinstall-sprsservice ' 一詞**無法**辨識為</span><span class="sxs-lookup"><span data-stu-id="8466f-225">Install-SPRSService : The term 'Install-SPRSService' **is not recognized** as the</span></span>  
    > <span data-ttu-id="8466f-226">Cmdlet、函數、指令檔或可執行程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="8466f-226">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="8466f-227">請參閱</span><span class="sxs-lookup"><span data-stu-id="8466f-227">Check the</span></span>  
    > <span data-ttu-id="8466f-228">名稱拼字是否正確，如果包含路徑的話，請確認路徑是否</span><span class="sxs-lookup"><span data-stu-id="8466f-228">spelling of the name, or if a path was included, verify that the path is</span></span>  
    > <span data-ttu-id="8466f-229">正確，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="8466f-229">correct and try again.</span></span>  
  
5.  <span data-ttu-id="8466f-230">執行下列 PowerShell 命令以安裝服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8466f-230">Run the following PowerShell command to install the service proxy.</span></span> <span data-ttu-id="8466f-231">成功完成命令會在管理命令介面中顯示新行。</span><span class="sxs-lookup"><span data-stu-id="8466f-231">A successful completion of the command displays a new line in the management shell.</span></span> <span data-ttu-id="8466f-232">成功完成命令之後，**不會有任何訊息傳回** 管理命令介面：</span><span class="sxs-lookup"><span data-stu-id="8466f-232">**No message is returned** to the management shell when the command completes successfully:</span></span>  
  
    ```powershell
    Install-SPRSServiceProxy  
    ```  
  
6.  <span data-ttu-id="8466f-233">執行下列 PowerShell 命令以啟動服務，或參閱下列附註，以取得有關如何從 SharePoint 管理中心啟動服務的指示：</span><span class="sxs-lookup"><span data-stu-id="8466f-233">Run the following PowerShell command to start the service or see the following notes for instructions on how to start the service from SharePoint Central administration:</span></span>  
  
    ```powershell
    Get-SPServiceInstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 <span data-ttu-id="8466f-234">您使用的可能是 Windows Powershell 而非 SharePoint 管理命令介面，或者未安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="8466f-234">Either you are in the Windows Powershell instead of the SharePoint Management Shell  or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode is not installed.</span></span> <span data-ttu-id="8466f-235">如需 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 PowerShell 的詳細資訊，請參閱 [Reporting Services SharePoint 模式的 PowerShell Cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-235">For more information on [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and PowerShell, see [PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
 <span data-ttu-id="8466f-236">您也可以從 SharePoint 管理中心啟動服務，而不是執行第三個 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="8466f-236">You can also start the service from SharePoint central Administration rather than running the third PowerShell command.</span></span> <span data-ttu-id="8466f-237">下列步驟也可用於確認服務是否執行。</span><span class="sxs-lookup"><span data-stu-id="8466f-237">The following steps are also useful to verify that the service is running.</span></span>  
  
1.  <span data-ttu-id="8466f-238">在 SharePoint 管理中心內，按一下 **[系統設定]** 群組中的 **[管理伺服器上的服務]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-238">In SharePoint Central Administration, click **Manage Services on Server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="8466f-239">找到 **[SQL Server Reporting Services 服務]** ，然後按一下 [動作] 欄中的 **[啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-239">Find **SQL Server Reporting Services Service** and click **Start** in the Action column.</span></span>  
  
3.  <span data-ttu-id="8466f-240">Reporting Services 服務的狀態會從 **[已停止]** 變更為 **[已啟動]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-240">The status of the Reporting Services service will change from **Stopped** to **Started**.</span></span> <span data-ttu-id="8466f-241">如果清單中沒有 Reporting Services 服務，請使用 PowerShell 安裝該服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-241">If the Reporting Services service is not in the list, use PowerShell to install the service.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8466f-242">如果 Reporting Services 服務停留在 [**啟動**中] 狀態，而未變更為 [**已啟動**]，請確認已在 Windows 伺服器管理員中啟動「SharePoint 2013 系統管理」服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-242">If the Reporting Services service stays in the **Starting** status and does not change to **Started**, verify the 'SharePoint 2013 Administration' service is started in Windows Server Manager.</span></span>  
  
##  <a name="step-3-create-a-reporting-services-service-application"></a><a name="bkmk_create_serrviceapplication"></a> <span data-ttu-id="8466f-243">步驟 3：建立 Reporting Services 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="8466f-243">Step 3: Create a Reporting Services Service Application</span></span>  
 <span data-ttu-id="8466f-244">本節提供建立服務應用程式的步驟，以及屬性的描述 (如果您要檢閱現有的服務應用程式)。</span><span class="sxs-lookup"><span data-stu-id="8466f-244">This section provides the steps to create a service application and a description of the properties, if you are reviewing an existing service application.</span></span>  
  
1.  <span data-ttu-id="8466f-245">在 [SharePoint 管理中心] 的 [**應用程式管理**] 群組中，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="8466f-245">In SharePoint Central Administration, in the **Application Management** group, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="8466f-246">在 SharePoint 功能區中，按一下 **[新增]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8466f-246">In the SharePoint ribbon, click the **New** button.</span></span>  
  
3.  <span data-ttu-id="8466f-247">在 [新增] 功能表中，按一下 **[SQL Server Reporting Services 服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-247">In the New menu, click **SQL Server Reporting Services Service Application.**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="8466f-248">如果此 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 選項未出現在清單中，表示\*\* [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 未安裝共用服務\*\*。</span><span class="sxs-lookup"><span data-stu-id="8466f-248">If the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option does not appear in the list, it is an **indication that the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] shared service is not installed**.</span></span> <span data-ttu-id="8466f-249">檢閱上一節中，如何使用 PowerShell Cmdlt 來安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8466f-249">Review the previous section on how to use PowerShell cmdlts to install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="8466f-250">在 **[建立新的 SQL Server Reporting Services 服務應用程式]** 頁面中，輸入應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="8466f-250">In the **Create SQL Server Reporting Services Service Application** page, enter a name for the application.</span></span> <span data-ttu-id="8466f-251">如果您要建立多個 Reporting Services 服務應用程式，描述性名稱和命名慣例將有助於您組織管理作業。</span><span class="sxs-lookup"><span data-stu-id="8466f-251">If you are creating multiple Reporting Services service applications, a descriptive name or naming convention will help you organize your administration and management operations.</span></span>  
  
5.  <span data-ttu-id="8466f-252">在 **[應用程式集區]** 區段中，建立應用程式的新應用程式集區 (建議)。</span><span class="sxs-lookup"><span data-stu-id="8466f-252">In **Application Pool** section, create a new application pool for the application (recommended).</span></span> <span data-ttu-id="8466f-253">如果您針對應用程式集區和服務應用程式使用相同的名稱，可讓進行中的管理更容易。</span><span class="sxs-lookup"><span data-stu-id="8466f-253">If you use the same name for both the application pool and the services application, it can make ongoing administration easier.</span></span> <span data-ttu-id="8466f-254">這可能也會受到您將建立的服務應用程式數目以及是否需要在單一應用程式集區中使用許多應用程式所影響。</span><span class="sxs-lookup"><span data-stu-id="8466f-254">This can also be affected by how many service applications you will create and if you need to use several in a single application pool.</span></span> <span data-ttu-id="8466f-255">請參閱 SharePoint Server 文件集以取得應用程式集區管理的建議事項和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="8466f-255">See the SharePoint Server documentation on recommendations and best practices for application pool management.</span></span>  
  
     <span data-ttu-id="8466f-256">針對應用程式集區選取或建立安全性帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-256">Select or create a security account for the application pool.</span></span> <span data-ttu-id="8466f-257">請務必指定網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-257">Be sure to specify a domain user account.</span></span> <span data-ttu-id="8466f-258">網域使用者帳戶會啟用 SharePoint 受管理帳戶功能，好讓您在一個地方更新密碼和帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="8466f-258">A domain user account enables the use of the SharePoint managed account feature, which lets you update passwords and account information in one place.</span></span> <span data-ttu-id="8466f-259">如果您計劃將部署向外延展，以包括在相同識別下執行的其他服務執行個體，也需要網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-259">Domain accounts are also required if you plan to scale out the deployment to include additional service instances that run under the same identity.</span></span>  
  
6.  <span data-ttu-id="8466f-260">在 **[資料庫伺服器]** 中，您可以使用目前的伺服器或選擇不同的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="8466f-260">In the **Database Server**, you can use the current server or choose a different SQL Server.</span></span>  
  
7.  <span data-ttu-id="8466f-261">在 **[資料庫名稱]** 中，預設值是 `ReportingService_<guid>`，這是唯一的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8466f-261">In **Database Name** the default value is `ReportingService_<guid>`, which is a unique database name.</span></span> <span data-ttu-id="8466f-262">若您要輸入新值，請輸入唯一值。</span><span class="sxs-lookup"><span data-stu-id="8466f-262">If you type a new value, type a unique value.</span></span> <span data-ttu-id="8466f-263">這是專門針對服務應用程式所建立的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="8466f-263">This is the new database to be created specifically for the services application.</span></span>  
  
8.  <span data-ttu-id="8466f-264">在 **[資料庫驗證]** 中，預設值是 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="8466f-264">In **Database Authentication**, the default is Windows Authentication.</span></span> <span data-ttu-id="8466f-265">如果您選擇 **[SQL 驗證]**，請參考 SharePoint 文件，以了解在 SharePoint 部署中使用這個驗證類型的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="8466f-265">If you choose **SQL Authentication**, refer to SharePoint documentation for best practices on how to use this authentication type in a SharePoint deployment.</span></span>  
  
9. <span data-ttu-id="8466f-266">在 **[Web 應用程式關聯]** 區段中，選取要佈建以供目前 Reporting Services 服務應用程式存取的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-266">In the **Web Application Association** section, select the Web Application to be provisioned for access by the current Reporting Services Service Application.</span></span> <span data-ttu-id="8466f-267">您可以建立一個 Reporting Services 服務應用程式與一個 Web 應用程式的關聯。</span><span class="sxs-lookup"><span data-stu-id="8466f-267">You can associate one Reporting Services service application to one web application.</span></span> <span data-ttu-id="8466f-268">如果目前所有的 Web 應用程式已有相關聯的 Reporting Services 服務應用程式，則會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="8466f-268">If all of the current web applications are already associated with a Reporting Services service application, you see a warning message.</span></span>  
  
10. <span data-ttu-id="8466f-269">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8466f-269">Click **OK**.</span></span>  
  
11. <span data-ttu-id="8466f-270">服務應用程式的建立程序會需要數分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="8466f-270">The process to create a service application could take several minutes to complete.</span></span> <span data-ttu-id="8466f-271">完成後，您會看到確認訊息及 **[提供訂閱和警示]** 頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="8466f-271">When it is complete, you will see a confirmation message and a link to a **Provision Subscriptions and Alerts** page.</span></span> <span data-ttu-id="8466f-272">如果您想要使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱功能或資料警示功能，請完成提供步驟。</span><span class="sxs-lookup"><span data-stu-id="8466f-272">Complete the provision step if you want to use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions feature or the data alerts feature.</span></span> <span data-ttu-id="8466f-273">如需詳細資訊，請參閱 [SSRS 服務應用程式的佈建訂用帳戶及警示](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-273">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).</span></span>  
  
 <span data-ttu-id="8466f-274">![PowerShell 相關內容](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")如需使用 PowerShell 建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的相關資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="8466f-274">![PowerShell related content](../../../2014/reporting-services/media/rs-powershellicon.jpg "PowerShell related content") For information on using PowerShell to create a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, see:</span></span>  
  
-   <span data-ttu-id="8466f-275">請參閱下一節[步驟 1 到 4 的 Windows PowerShell 指令碼](#bkmk_full_script)。</span><span class="sxs-lookup"><span data-stu-id="8466f-275">See the following section [Windows PowerShell script for Steps 1-4](#bkmk_full_script).</span></span>  
  
-   <span data-ttu-id="8466f-276">[使用 PowerShell 建立 Reporting Services 服務應用程式](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp)主題。</span><span class="sxs-lookup"><span data-stu-id="8466f-276">Topic [To create a Reporting Services Service Application using PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).</span></span>  
  
##  <a name="step-4-activate-the-power-view-site-collection-feature"></a><a name="bkmk_powerview"></a> <span data-ttu-id="8466f-277">步驟 4：啟動 Power View 網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-277">Step 4: Activate the Power View Site Collection Feature.</span></span>  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="8466f-278">(適用於 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SharePoint 產品之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] 增益集的功能) 是網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-278">, a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint Products, is a site collection feature.</span></span> <span data-ttu-id="8466f-279">將會針對根網站集合以及安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集之後所建立的網站集合自動啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-279">The feature is activated automatically for root site collections and site collections created after the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in is installed.</span></span> <span data-ttu-id="8466f-280">如果您打算使用 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]，請確認此功能是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="8466f-280">If you plan to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], verify that the feature is activated.</span></span>  
  
 <span data-ttu-id="8466f-281">如果您在安裝 SharePoint Server 之後安裝適用於 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，只會針對根網站集合啟用報表伺服器整合功能和 Power View 整合功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-281">If you install the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint Products after the installation of the SharePoint Server, then the Report Server integration feature and the Power View integration feature will only be activated for root site collections.</span></span> <span data-ttu-id="8466f-282">如果是其他網站集合，請手動啟用這些功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-282">For other site collections, manually activate the features.</span></span>  
  
#### <a name="to-activate-or-verify-the-power-view-site-collection-feature"></a><span data-ttu-id="8466f-283">若要啟動或確認 Power View 網站集合功能</span><span class="sxs-lookup"><span data-stu-id="8466f-283">To Activate or Verify the Power View Site Collection Feature</span></span>  
  
1.  <span data-ttu-id="8466f-284">下列步驟會假設您的 SharePoint 網站設定為 2013 **體驗版**。</span><span class="sxs-lookup"><span data-stu-id="8466f-284">The following steps assume your SharePoint site is configured for the 2013 **experience version**.</span></span>  
  
     <span data-ttu-id="8466f-285">開啟瀏覽器，移至所要的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="8466f-285">Open your browser to the desired SharePoint site.</span></span> <span data-ttu-id="8466f-286">例如 HTTP:// \<servername> /sites/bi</span><span class="sxs-lookup"><span data-stu-id="8466f-286">For example http://\<servername>/sites/bi</span></span>  
  
2.  <span data-ttu-id="8466f-287">按一下 [**設定**] [![SharePoint 設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")]。</span><span class="sxs-lookup"><span data-stu-id="8466f-287">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings").</span></span>  
  
3.  <span data-ttu-id="8466f-288">按一下 [**網站設定**]。</span><span class="sxs-lookup"><span data-stu-id="8466f-288">Click **Site settings**.</span></span>  
  
4.  <span data-ttu-id="8466f-289">在 **[網站集合管理]** 群組中，按一下 **[網站集合功能]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-289">In the **Site Collection Administration** group Click **Site collection features**.</span></span>  
  
5.  <span data-ttu-id="8466f-290">在清單中尋找 **[Power View 整合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-290">Find **Power View Integration Feature** in the list.</span></span>  
  
6.  <span data-ttu-id="8466f-291">按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="8466f-291">Click **Activate**.</span></span> <span data-ttu-id="8466f-292">功能狀態會變更為 **[使用中]**。</span><span class="sxs-lookup"><span data-stu-id="8466f-292">The feature status will change to **Active**.</span></span>  
  
 <span data-ttu-id="8466f-293">每個網站集合都已完成這個程序。</span><span class="sxs-lookup"><span data-stu-id="8466f-293">This procedure is completed per site collection.</span></span> <span data-ttu-id="8466f-294">如需詳細資訊，請參閱 [Activate the Report Server and Power View Integration Features in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-294">For more information, see [Activate the Report Server and Power View Integration Features in SharePoint](../../../2014/reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md).</span></span>  
  
##  <a name="windows-powershell-script-for-steps-1-4"></a><a name="bkmk_full_script"></a><span data-ttu-id="8466f-295">適用于步驟1-4 的 Windows PowerShell 腳本</span><span class="sxs-lookup"><span data-stu-id="8466f-295">Windows PowerShell script for Steps 1-4</span></span>  
 <span data-ttu-id="8466f-296">本節中的 PowerShells 指令碼與上一節的完成步驟 1 到 4 相同。</span><span class="sxs-lookup"><span data-stu-id="8466f-296">The PowerShells script in this section are the equivalent of completing steps 1 to 4 in the previous sections.</span></span> <span data-ttu-id="8466f-297">此指令碼完成下列各項：</span><span class="sxs-lookup"><span data-stu-id="8466f-297">The script completes the following:</span></span>  
  
-   <span data-ttu-id="8466f-298">安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務和服務 Proxy，以及啟動服務。</span><span class="sxs-lookup"><span data-stu-id="8466f-298">Installs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service and service proxy, and starts the service.</span></span>  
  
-   <span data-ttu-id="8466f-299">建立名為 "Reporting Services" 的服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8466f-299">Creates a service proxy named "Reporting Services".</span></span>  
  
-   <span data-ttu-id="8466f-300">建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 名為 "Reporting Services application" 的服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466f-300">Creates a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application named "Reporting Services Application".</span></span>  
  
-   <span data-ttu-id="8466f-301">啟用網站集合的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="8466f-301">Enables the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature for a site collection.</span></span>  
  
 <span data-ttu-id="8466f-302">參數</span><span class="sxs-lookup"><span data-stu-id="8466f-302">Parameters</span></span>  
  
-   <span data-ttu-id="8466f-303">更新服務 Proxy 的 **-Account** 。</span><span class="sxs-lookup"><span data-stu-id="8466f-303">Update the **-Account** for the service proxy.</span></span> <span data-ttu-id="8466f-304">帳戶必須是 SharePoint 伺服器陣列中受管理的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="8466f-304">The account needs to be a managed service account in the SharePoint farm.</span></span> <span data-ttu-id="8466f-305">如需詳細資訊，請參閱 SharePoint 主題＜ [規劃 SharePoint 2013 管理帳戶及服務帳戶](https://technet.microsoft.com/library/cc263445.aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="8466f-305">For more information, see the SharePoint topic [Plan for administrative and service accounts in SharePoint 2013](https://technet.microsoft.com/library/cc263445.aspx).</span></span>  
  
-   <span data-ttu-id="8466f-306">更新服務應用程式的 **-DatabaseServer**參數。</span><span class="sxs-lookup"><span data-stu-id="8466f-306">Update the **-DatabaseServer** parameter for the service application.</span></span> <span data-ttu-id="8466f-307">這個參數是 Database Engine 執行個體</span><span class="sxs-lookup"><span data-stu-id="8466f-307">This parameter is the database engine instance</span></span>  
  
-   <span data-ttu-id="8466f-308">更新您想要啟用功能之網站的 **-url**參數 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8466f-308">Update the **-url** parameter of the site that you want the [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] feature enabled.</span></span>  
  
 <span data-ttu-id="8466f-309">**若要使用指令碼：**</span><span class="sxs-lookup"><span data-stu-id="8466f-309">**To use the script:**</span></span>  
  
1.  <span data-ttu-id="8466f-310">使用系統管理權限來開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8466f-310">Open Windows PowerShell with administrative privileges.</span></span>  
  
2.  <span data-ttu-id="8466f-311">將下列程式碼複製到指令碼視窗。</span><span class="sxs-lookup"><span data-stu-id="8466f-311">Copy the following code into the script window.</span></span>  
  
3.  <span data-ttu-id="8466f-312">更新上一節中描述的三個參數，然後執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="8466f-312">Update the three parameters described in the previous section, and then run the script.</span></span>  
  
```powershell
#This script Configures SQL Server Reporting Services SharePoint mode  
  
$starttime = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
  
Write-Host -ForegroundColor Green "Import the SharePoint PowerShell snappin"  
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0  
  
Write-Host -ForegroundColor Green "Install SSRS Service and Service Proxy, and start the service"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
  
    Write-Host -ForegroundColor Green "Install the Reporting Services Shared Service"  
    Install-SPRSService  
  
    Write-Host -ForegroundColor Green " Install the Reporting Services Service Proxy"  
    Install-SPRSServiceProxy  
  
    # Get the ID of the RS Service Instance and start the service   
    Write-Host -ForegroundColor Green "Start the Reporting Services Service"  
    $RS = Get-SPServiceInstance | Where {$_.TypeName -eq "SQL Server Reporting Services Service"}  
    Start-SPServiceInstance -Identity $RS.Id.ToString()  
  
    # Wait for the Reporting Services Service to start...  
    $Status = Get-SPServiceInstance $RS.Id.ToString()  
    While ($Status.Status -ne "Online")  
    {  
        Write-Host -ForegroundColor Green "SSRS Service Not Online...Current Status = " $Status.Status  
        Start-Sleep -Seconds 2  
        $Status = Get-SPServiceInstance $RS.Id.ToString()  
    }  
  
$time = Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Create a new application pool and Reporting Services service application"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
Write-Host -ForegroundColor Green "Create a new application pool"  
#!!!! update "-Account" with an existing Managed Service Account  
New-SPServiceApplicationPool -Name "Reporting Services" -Account "<domain>\User name>"  
$appPool = Get-SPServiceApplicationPool "Reporting Services"  
  
Write-Host -ForegroundColor Green " Create the Reporting Services Service Application"  
#!!!! Update "-DatabaseServer", an instance of the SQL Server database engine   
$rsService = New-SPRSServiceApplication -Name "Reporting Services Application" -ApplicationPool $appPool -DatabaseName "Reporting_Services_Application" -DatabaseServer "<server name>"  
  
Write-Host -ForegroundColor Green "Create the Reporting Services Service Application Proxy"  
$rsServiceProxy = New-SPRSServiceApplicationProxy -Name "Reporting Services Application Proxy" -ServiceApplication $rsService  
  
Write-Host -ForegroundColor Green "Associate service application proxy to default web site and grant web applications rights to SSRS application pool"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"     
# Associate the Reporting Services Service Applicatoin Proxy to the default web site...  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $rsServiceProxy  
  
$time=Get-Date  
Write-Host -foregroundcolor DarkGray StartTime>> $starttime   
Write-Host -foregroundcolor DarkGray $time  
  
Write-Host -ForegroundColor Green "Enable the PowerView and reportserver site features"  
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"  
#!!!! update "-url"  of the site where you want the features enabled  
Enable-SPfeature -identity "powerview" -Url http://server/sites/bi  
Enable-SPfeature -identity "reportserver" -Url http://server/sites/bi  
  
####To Verify, you can run the following:  
#Get-SPRSServiceApplication  
#Get-SPServiceApplicationPool | where {$_.name -like "reporting*"}  
#Get-SPRSServiceApplicationProxy
```  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional_config"></a><span data-ttu-id="8466f-313">其他設定</span><span class="sxs-lookup"><span data-stu-id="8466f-313">Additional Configuration</span></span>  
 <span data-ttu-id="8466f-314">本節描述多數 SharePoint 部署中重要的其他組態步驟。</span><span class="sxs-lookup"><span data-stu-id="8466f-314">This section describes additional configuration steps that are important in most SharePoint deployments.</span></span>  
  
###  <a name="configure-excel-services-and-powerpivot"></a><a name="bkmk_configure_ECS"></a><span data-ttu-id="8466f-315">設定 Excel Services 和 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="8466f-315">Configure Excel Services and PowerPivot</span></span>  
 <span data-ttu-id="8466f-316">如果您想要在 SharePoint 中檢視 Excel 2013 活頁簿中的 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View 報表，就必須將伺服器陣列上的 Excel Services 應用程式設定為使用 SharePoint 模式中的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8466f-316">If you want to view [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Power View reports in an Excel 2013 workbook in SharePoint, an Excel Services Application on the farm needs to be configured to use an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Server in SharePoint mode.</span></span> <span data-ttu-id="8466f-317">此外， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式所使用的應用程式集區安全性帳戶必須是 Analysis Services 伺服器的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8466f-317">Also, the application pool security account used by the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, must be an administrator on the Analysis Services Server.</span></span> <span data-ttu-id="8466f-318">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="8466f-318">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="8466f-319">[PowerPivot for SharePoint 2013 安裝](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)中的「設定適用于 Analysis Services 整合的 Excel Services」一節。</span><span class="sxs-lookup"><span data-stu-id="8466f-319">The section "Configure Excel Services for Analysis Services integration" in [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
-   <span data-ttu-id="8466f-320">[管理 Excel Services 資料模型設定 (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8466f-320">[Manage Excel Services data model settings (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).</span></span>  
  
###  <a name="provision-subscriptions-and-alerts"></a><a name="bkmk_provision_agent"></a><span data-ttu-id="8466f-321">布建訂閱和警示</span><span class="sxs-lookup"><span data-stu-id="8466f-321">Provision Subscriptions and Alerts</span></span>  
 <span data-ttu-id="8466f-322">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱和資料警示可能需要 SQL Server Agent 權限組態。</span><span class="sxs-lookup"><span data-stu-id="8466f-322">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription and data alert features may require the configuration of SQL Server Agent permissions.</span></span> <span data-ttu-id="8466f-323">如果您看到錯誤訊息，指出需要 SQL Server Agent，且您已確認 SQL Server Agent 正在執行，則請更新權限。</span><span class="sxs-lookup"><span data-stu-id="8466f-323">If you see an error message that indicates SQL Server Agent is required and you have verified SQL Server Agent is running, update the permissions.</span></span> <span data-ttu-id="8466f-324">您可以在成功建立服務應用程式頁面上，按一下 **[提供訂閱和警示]** 連結，以移至其他頁面並提供 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="8466f-324">You can click the link **Provision Subscriptions and Alerts** on the create service application success page to go to another page for provisioning SQL Server Agent.</span></span> <span data-ttu-id="8466f-325">如果您的部署跨電腦界限 (例如 SQL Server 資料庫執行個體位於其他電腦上)，則需要提供步驟。</span><span class="sxs-lookup"><span data-stu-id="8466f-325">The provision step is needed if your deployment crosses machine boundaries, for example when the SQL Server database instance is on a different machine.</span></span> <span data-ttu-id="8466f-326">如需詳細資訊，請參閱[SSRS 服務應用程式的布建訂閱和警示](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span><span class="sxs-lookup"><span data-stu-id="8466f-326">For more information, see [Provision Subscriptions and Alerts for SSRS Service Applications](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)</span></span>  
  
### <a name="configure-e-mail-for-ssrs-service-applications"></a><span data-ttu-id="8466f-327">設定 SSRS 服務應用程式的電子郵件</span><span class="sxs-lookup"><span data-stu-id="8466f-327">Configure E-mail for SSRS Service Applications</span></span>  
 <span data-ttu-id="8466f-328">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料警示功能會以電子郵件訊息傳送警示。</span><span class="sxs-lookup"><span data-stu-id="8466f-328">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] data alerts feature sends alerts in e-mail messages.</span></span> <span data-ttu-id="8466f-329">若要傳送電子郵件，您可能需要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式，以及修改服務應用程式的電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8466f-329">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="8466f-330">如果您計劃針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱功能使用電子郵件傳遞延伸模組，則需要電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="8466f-330">If you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature, the e-mail settings are required.</span></span> <span data-ttu-id="8466f-331">如需詳細資訊，請參閱[設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2010 和 SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-331">For more information, see [Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)</span></span>  
  
### <a name="add-reporting-services-content-types-to-content-libraries"></a><span data-ttu-id="8466f-332">將 Reporting Services 內容類型加入至內容庫</span><span class="sxs-lookup"><span data-stu-id="8466f-332">Add Reporting Services Content Types to Content Libraries</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8466f-333">會提供預先定義的內容類型，可用來管理共用資料來源 (.rsds) 檔、報表模型 (.smdl) 檔，以及報表產生器的報表定義 (.rdl) 檔。</span><span class="sxs-lookup"><span data-stu-id="8466f-333">provides predefined content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="8466f-334">將 **[報表產生器報表]**、 **[報表模型]** 和 **[報表資料來源]** 內容類型加入至文件庫會啟用 **[新增]** 命令，讓您能夠建立該類型的新文件。</span><span class="sxs-lookup"><span data-stu-id="8466f-334">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span> <span data-ttu-id="8466f-335">如需詳細資訊，請參閱[將報表伺服器內容類型加入至程式庫 &#40;SharePoint 整合模式中的 Reporting Services&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-335">For more information, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="activate-the-report-server-file-sync-feature"></a><span data-ttu-id="8466f-336">啟動報表伺服器檔案同步處理功能</span><span class="sxs-lookup"><span data-stu-id="8466f-336">Activate the Report Server File sync Feature</span></span>  
 <span data-ttu-id="8466f-337">如果使用者經常直接上傳已發行的報表項目至 SharePoint 文件庫， **[報表伺服器檔案同步處理]** 網站層級功能會很有協助。</span><span class="sxs-lookup"><span data-stu-id="8466f-337">If users will frequently upload published report items directly to SharePoint document libraries, the **Report Server File Sync** site level feature will be beneficial.</span></span> <span data-ttu-id="8466f-338">檔案同步處理功能會更頻繁地同步處理報表伺服器目錄與文件庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="8466f-338">The file sync feature will synchronize the report server catalog with items in document libraries on a more frequent basis.</span></span> <span data-ttu-id="8466f-339">如需詳細資訊，請參閱 [在 SharePoint 管理中心啟動報表伺服器檔案同步處理功能](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="8466f-339">For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).</span></span>  
  
##  <a name="verify-the-installation"></a><a name="bkmk_verify_installation"></a><span data-ttu-id="8466f-340">確認安裝</span><span class="sxs-lookup"><span data-stu-id="8466f-340">Verify the installation</span></span>  
 <span data-ttu-id="8466f-341">以下是驗證 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式部署的建議步驟和程序。</span><span class="sxs-lookup"><span data-stu-id="8466f-341">The following are suggested steps and procedures to verify the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode deployment.</span></span>  
  
-   <span data-ttu-id="8466f-342">請參閱驗證主題＜ [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)＞中的＜SharePoint＞一節。</span><span class="sxs-lookup"><span data-stu-id="8466f-342">See the SharePoint section in the verification topic [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md).</span></span>  
  
-   <span data-ttu-id="8466f-343">在 SharePoint 文件庫中，建立只包含一個文字方塊 (例如標題) 的基本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="8466f-343">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="8466f-344">此報表不包含任何資料來源或資料集。</span><span class="sxs-lookup"><span data-stu-id="8466f-344">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="8466f-345">目標是確認您可以開啟報表產生器、建立基本報表和預覽報表。</span><span class="sxs-lookup"><span data-stu-id="8466f-345">The goal is to verify you can open Report Builder, build a basic report, and preview the report.</span></span>  
  
     <span data-ttu-id="8466f-346">將報表儲存至文件庫，然後從文件庫中執行報表。</span><span class="sxs-lookup"><span data-stu-id="8466f-346">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="8466f-347">如需使用報表產生器建立報表的詳細資訊，請參閱 [啟動報表產生器 (報表產生器)](https://technet.microsoft.com/library/ms159221.aspx)。</span><span class="sxs-lookup"><span data-stu-id="8466f-347">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8466f-348">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8466f-348">See Also</span></span>  
 <span data-ttu-id="8466f-349">[適用于 Reporting Services SharePoint 模式的 PowerShell Cmdlet](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8466f-349">[PowerShell cmdlets for Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="8466f-350">[升級和移轉 Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8466f-350">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="8466f-351">[內容藍圖：安裝及設定 SharePoint Server 和 SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span><span class="sxs-lookup"><span data-stu-id="8466f-351">[Content Roadmap: Set up and configure SharePoint Server and SQL Server BI](https://technet.microsoft.com/library/dn205112.aspx) </span></span>  
 <span data-ttu-id="8466f-352">[SQL Server 2012 版本所支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="8466f-352">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 [<span data-ttu-id="8466f-353">Reporting Services SharePoint 服務和服務應用程式</span><span class="sxs-lookup"><span data-stu-id="8466f-353">Reporting Services SharePoint Service and Service Applications</span></span>](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)
