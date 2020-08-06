---
title: 部署資料層應用程式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploydacwizard.updateconfiguration.f1
- sql12.swb.deploydacwizard.selectdac.f1
- sql12.swb.deploydacwizard.deploydac.f1
- sql12.swb.deploydacwizard.introduction.f1
- sql12.swb.deploydacwizard.summary.f1
helpviewer_keywords:
- Deploy data-tier application
- deploy DAC
- data-tier application [SQL Server], deploy
- How to [DAC], deploy
- wizard [DAC], deploy
ms.assetid: c117af35-aa53-44a5-8034-fa8715dc735f
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd4a09eed946863064728fd8c62230121ad3d403
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707601"
---
# <a name="deploy-a-data-tier-application"></a><span data-ttu-id="79d26-102">部署資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="79d26-102">Deploy a Data-tier Application</span></span>
  <span data-ttu-id="79d26-103">您可以使用精靈或 PowerShell 指令碼，將 DAC 封裝中的資料層應用程式 (DAC) 部署到現有的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 或 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="79d26-103">You can deploy a data-tier application (DAC) from a DAC package to an existing instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or [!INCLUDE[ssSDS](../../includes/sssds-md.md)] by using a wizard or a PowerShell script.</span></span> <span data-ttu-id="79d26-104">部署程序會將 DAC 定義儲存到 **msdb** 系統資料庫 (**中則是** master [!INCLUDE[ssSDS](../../includes/sssds-md.md)]) 來註冊 DAC 執行個體並建立資料庫，然後使用 DAC 內定義的所有資料庫物件來擴展資料庫。</span><span class="sxs-lookup"><span data-stu-id="79d26-104">The deployment process registers a DAC instance by storing the DAC definition in the **msdb** system database (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]), creates a database, and then populates the database with all the database objects defined in the DAC.</span></span>  
  
-   <span data-ttu-id="79d26-105">**開始之前：**  [SQL Server 公用程式](#SQLUtility)、 [資料庫選項和設定](#DBOptSettings)、 [限制事項](#LimitationsRestrictions)、 [必要條件](#Prerequisites)、 [安全性](#Security)、 [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="79d26-105">**Before you begin:**  [SQL Server Utility](#SQLUtility), [Database Options and Settings](#DBOptSettings), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="79d26-106">**使用下列項目，部署 DAC**  [部署資料層應用程式精靈](#UsingDeployDACWizard)、 [PowerShell](#DeployDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="79d26-106">**To deploy a DAC, using:**  [The Deploy Data-tier Application Wizard](#UsingDeployDACWizard), [PowerShell](#DeployDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> <span data-ttu-id="79d26-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="79d26-107">Before You Begin</span></span>  
 <span data-ttu-id="79d26-108">可以將相同的 DAC 封裝部署到單一 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體多次，但是一次只能執行一個部署。</span><span class="sxs-lookup"><span data-stu-id="79d26-108">The same DAC package can be deployed to a single instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] multiple times, however the deployments must be run one at a time.</span></span> <span data-ttu-id="79d26-109">針對每個部署指定的 DAC 執行個體名稱在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="79d26-109">The DAC instance name specified for each deployment must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
###  <a name="sql-server-utility"></a><a name="SQLUtility"></a><span data-ttu-id="79d26-110">SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="79d26-110">SQL Server Utility</span></span>  
 <span data-ttu-id="79d26-111">若您將 DAC 部署至 Database Engine 的受管理執行個體，下次從執行個體將公用程式收集組傳送到公用程式控制點時，部署的 DAC 就會合併至 SQL Server 公用程式。</span><span class="sxs-lookup"><span data-stu-id="79d26-111">If you deploy a DAC to a managed instance of the Database Engine, the deployed DAC is incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the utility control point.</span></span> <span data-ttu-id="79d26-112">然後 DAC 會出現在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] [公用程式總管] 的 [部署的資料層應用程式] 節點中，並在 [部署的資料層應用程式] 詳細資料頁面中報告。</span><span class="sxs-lookup"><span data-stu-id="79d26-112">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a><span data-ttu-id="79d26-113">資料庫選項和設定</span><span class="sxs-lookup"><span data-stu-id="79d26-113">Database Options and Settings</span></span>  
 <span data-ttu-id="79d26-114">根據預設，部署期間建立的資料庫將會擁有 CREATE DATABASE 陳述式中的所有預設值，但是以下項目除外：</span><span class="sxs-lookup"><span data-stu-id="79d26-114">By default, the database created during the deployment will have all of the default settings from the CREATE DATABASE statement, except:</span></span>  
  
-   <span data-ttu-id="79d26-115">資料庫定序和相容性層級設定為 DAC 封裝內所定義的值。</span><span class="sxs-lookup"><span data-stu-id="79d26-115">The database collation and compatibility level are set to the values defined in the DAC package.</span></span> <span data-ttu-id="79d26-116">在 SQL Server Developer Tools 中從資料庫專案建立的 DAC 封裝會使用資料庫專案中所設定的值。</span><span class="sxs-lookup"><span data-stu-id="79d26-116">A DAC package built from a database project in the SQL Server Developer Tools uses the values set in the database project.</span></span> <span data-ttu-id="79d26-117">從現有的資料庫中擷取的封裝會使用原始資料庫中的值。</span><span class="sxs-lookup"><span data-stu-id="79d26-117">A package extracted from an existing database uses the values from the original database.</span></span>  
  
-   <span data-ttu-id="79d26-118">您可以在 **[更新組態]** 頁面上調整某些資料庫設定，例如資料庫名稱和檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="79d26-118">You can adjust some of the database settings, such as database name and file paths, in the **Update Configuration** page.</span></span> <span data-ttu-id="79d26-119">部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]時，無法設定檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="79d26-119">You cannot set the file paths when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="79d26-120">某些資料庫選項 (例如 TRUSTWORTHY、DB_CHAINING 和 HONOR_BROKER_PRIORITY) 無法在部署過程中調整。</span><span class="sxs-lookup"><span data-stu-id="79d26-120">Some database options, such as TRUSTWORTHY, DB_CHAINING, and HONOR_BROKER_PRIORITY, cannot be adjusted as part of the deployment process.</span></span> <span data-ttu-id="79d26-121">實體屬性 (如檔案群組數目或檔案數目和大小) 無法在部署過程中更改。</span><span class="sxs-lookup"><span data-stu-id="79d26-121">Physical properties, such as the number of filegroups, or the numbers and sizes of files cannot be altered as part of the deployment process.</span></span> <span data-ttu-id="79d26-122">部署完成之後，您可以使用 ALTER DATABASE 陳述式、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 來修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="79d26-122">After the deployment completes, you can use the ALTER DATABASE statement, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell to tailor the database.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="79d26-123">限制事項</span><span class="sxs-lookup"><span data-stu-id="79d26-123">Limitations and Restrictions</span></span>  
 <span data-ttu-id="79d26-124">DAC 可部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 4 (SP4) 或更新版本的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="79d26-124">A DAC can be deployed to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="79d26-125">如果您使用更新版本建立 DAC，則 DAC 可能會包含 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]不支援的物件。</span><span class="sxs-lookup"><span data-stu-id="79d26-125">If you create a DAC using a later version, the DAC may contain objects not supported by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="79d26-126">您無法將這些 DAC 部署至 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="79d26-126">You cannot deploy those DACs to instances of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="79d26-127">必要條件</span><span class="sxs-lookup"><span data-stu-id="79d26-127">Prerequisites</span></span>  
 <span data-ttu-id="79d26-128">建議您不要部署來源不明或來源不受信任的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="79d26-128">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="79d26-129">這類封裝可能包含惡意程式碼，因此可能會執行非預期的 Transact-SQL 程式碼，或是修改結構描述而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="79d26-129">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="79d26-130">在您使用來源不明或來源不受信任的封裝之前，請解除封裝 DAC 並檢查程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="79d26-130">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span> <span data-ttu-id="79d26-131">如需有關如何執行這些檢查的詳細資訊，請參閱＜ [Validate a DAC Package](validate-a-dac-package.md)＞。</span><span class="sxs-lookup"><span data-stu-id="79d26-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="79d26-132">Security</span><span class="sxs-lookup"><span data-stu-id="79d26-132">Security</span></span>  
 <span data-ttu-id="79d26-133">為了提高安全性，SQL Server 驗證登入會儲存在 DAC 封裝中，而且沒有密碼。</span><span class="sxs-lookup"><span data-stu-id="79d26-133">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="79d26-134">當您部署或升級此封裝時，此登入會建立為停用的登入，而且會產生密碼。</span><span class="sxs-lookup"><span data-stu-id="79d26-134">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="79d26-135">若要啟用登入，請使用具有 ALTER ANY LOGIN 權限的登入進行登入，並使用 ALTER LOGIN 來啟用登入，然後指派可以傳達給使用者的新密碼。</span><span class="sxs-lookup"><span data-stu-id="79d26-135">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="79d26-136">Windows 驗證登入不需要這項處理，因為這類登入的密碼不是由 SQL Server 所管理。</span><span class="sxs-lookup"><span data-stu-id="79d26-136">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="79d26-137">權限</span><span class="sxs-lookup"><span data-stu-id="79d26-137">Permissions</span></span>  
 <span data-ttu-id="79d26-138">只有下列項目的成員才能部署 DAC： **sysadmin** 或 **serveradmin** 固定伺服器角色，或是具有 **dbcreator** 固定伺服器角色及擁有 ALTER ANY LOGIN 權限的登入。</span><span class="sxs-lookup"><span data-stu-id="79d26-138">A DAC can only be deployed by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="79d26-139">內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶 (名稱為 **sa** ) 也可以部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-139">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also deploy a DAC.</span></span> <span data-ttu-id="79d26-140">將具有登入的 DAC 部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 loginmanager 或伺服器管理員 (serveradmin) 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="79d26-140">Deploying a DAC with logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the loginmanager or serveradmin roles.</span></span> <span data-ttu-id="79d26-141">將不具有登入的 DAC 部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ，需要 dbmanager 或伺服器管理員 (serveradmin) 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="79d26-141">Deploying a DAC without logins to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the dbmanager or serveradmin roles.</span></span>  
  
##  <a name="using-the-deploy-data-tier-application-wizard"></a><a name="UsingDeployDACWizard"></a><span data-ttu-id="79d26-142">使用部署資料層應用程式嚮導</span><span class="sxs-lookup"><span data-stu-id="79d26-142">Using the Deploy Data-tier Application Wizard</span></span>  
 <span data-ttu-id="79d26-143">**若要使用精靈部署 DAC**</span><span class="sxs-lookup"><span data-stu-id="79d26-143">**To Deploy a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="79d26-144">在 **[物件總管]** 中，展開您要部署 DAC 之執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="79d26-144">In **Object Explorer**, expand the node for the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="79d26-145">以滑鼠右鍵按一下 [資料庫]  節點，然後選取 [部署資料層應用程式…] </span><span class="sxs-lookup"><span data-stu-id="79d26-145">Right-click the **Databases** node, then select **Deploy Data-tier Application...**</span></span>  
  
3.  <span data-ttu-id="79d26-146">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="79d26-146">Complete the wizard dialogs:</span></span>  
  
    -   [<span data-ttu-id="79d26-147">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-147">Introduction Page</span></span>](#Introduction)  
  
    -   [<span data-ttu-id="79d26-148">選取 DAC 封裝頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-148">Select DAC Package Page</span></span>](#Select_dac_package)  
  
    -   [<span data-ttu-id="79d26-149">檢閱原則頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-149">Review Policy Page</span></span>](#Review_policy)  
  
    -   [<span data-ttu-id="79d26-150">更新組態頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-150">Update Configuration Page</span></span>](#Update_configuration)  
  
    -   [<span data-ttu-id="79d26-151">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-151">Summary Page</span></span>](#Summary)  
  
    -   [<span data-ttu-id="79d26-152">部署頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-152">Deploy Page</span></span>](#Deploy)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="79d26-153">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-153">Introduction Page</span></span>  
 <span data-ttu-id="79d26-154">此頁面描述部署資料層應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="79d26-154">This page describes the steps for deploying a data-tier application.</span></span>  
  
 <span data-ttu-id="79d26-155">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="79d26-155">**Do not show this page again.**</span></span> <span data-ttu-id="79d26-156">- 按一下此核取方塊，之後就不會再顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-156">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="79d26-157">**下一步 >** - 繼續進行 [Select DAC Package (選取 DAC 封裝)]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-157">**Next >** - Proceeds to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="79d26-158">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-158">**Cancel** - Terminates the wizard without deploying a DAC.</span></span>  
  
##  <a name="select-dac-package-page"></a><a name="Select_dac_package"></a><span data-ttu-id="79d26-159">選取 DAC 封裝頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-159">Select DAC Package Page</span></span>  
 <span data-ttu-id="79d26-160">使用此頁面來指定包含要部署之資料層應用程式的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="79d26-160">Use this page to specify the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="79d26-161">此頁面會在三種狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="79d26-161">The page transitions through three states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="79d26-162">選取 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="79d26-162">Select the DAC Package</span></span>  
 <span data-ttu-id="79d26-163">使用此頁面的初始狀態來選擇要部署的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="79d26-163">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="79d26-164">DAC 封裝必須是有效的 DAC 封裝檔案，而且必須有 .dacpac 副檔名。</span><span class="sxs-lookup"><span data-stu-id="79d26-164">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span>  
  
 <span data-ttu-id="79d26-165">**DAC 封裝** - 指定包含要部署之資料層應用程式的 DAC 封裝的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-165">**DAC Package** - Specify the path and file name of the DAC package that contains the data-tier application to be deployed.</span></span> <span data-ttu-id="79d26-166">您可以選取方塊右邊的 **[瀏覽]** 按鈕，瀏覽到 DAC 封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="79d26-166">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="79d26-167">**應用程式名稱** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示指派之 DAC 名稱的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="79d26-167">**Application Name** - A read-only box that displays the DAC name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="79d26-168">**版本** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示指派之版本的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="79d26-168">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="79d26-169">**描述** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示撰寫之描述的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="79d26-169">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="79d26-170">\*\* \< 上一步**-返回 [**簡介\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-170">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="79d26-171">**下一步 >** - 將進度列顯示為確認選定檔案為有效 DAC 封裝的精靈。</span><span class="sxs-lookup"><span data-stu-id="79d26-171">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="79d26-172">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-172">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="79d26-173">驗證 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="79d26-173">Validating the DAC Package</span></span>  
 <span data-ttu-id="79d26-174">將進度列顯示為確認選定檔案為有效 DAC 封裝的精靈。</span><span class="sxs-lookup"><span data-stu-id="79d26-174">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="79d26-175">如果此 DAC 封裝已經驗證，此精靈會繼續回到最後一版的 **[選取封裝]** 頁面，您可以在此頁面上檢閱驗證的結果。</span><span class="sxs-lookup"><span data-stu-id="79d26-175">If the DAC package is validated, the wizard proceeds to the final version of the **Select Package** page where you can review the results of the validation.</span></span> <span data-ttu-id="79d26-176">如果檔案不是有效的 DAC 封裝，精靈會停留在 **[選取 DAC 封裝]** 上。</span><span class="sxs-lookup"><span data-stu-id="79d26-176">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package**.</span></span> <span data-ttu-id="79d26-177">請選取另一個有效的 DAC 封裝，或是取消精靈並產生新的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="79d26-177">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="79d26-178">**正在驗證 DAC 的內容** - 報告驗證程序之目前狀態的進度列。</span><span class="sxs-lookup"><span data-stu-id="79d26-178">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="79d26-179">\*\* \< 上一步**-回到 [**選取封裝\*\*] 頁面的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="79d26-179">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="79d26-180">**下一步 >** - 繼續進行最終版本的 [選取封裝]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-180">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="79d26-181">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-181">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a><span data-ttu-id="79d26-182">[審查原則] 頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-182">Review Policy Page</span></span>  
 <span data-ttu-id="79d26-183">使用此頁面來檢閱評估 DAC 伺服器選取原則的結果 (如果 DAC 有原則的話)。</span><span class="sxs-lookup"><span data-stu-id="79d26-183">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="79d26-184">DAC 伺服器選取原則為選擇性，而且當它在 Visual Studio 中建立時會指派給 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-184">The DAC server selection policy is optional, and is assigned to the DAC when it is created in Visual Studio.</span></span> <span data-ttu-id="79d26-185">此原則會使用伺服器選取原則 Facet 來指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體主控 DAC 所應該符合的條件。</span><span class="sxs-lookup"><span data-stu-id="79d26-185">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="79d26-186">**原則條件的評估結果** - 唯讀報表，顯示 DAC 部署原則的條件是否成功。</span><span class="sxs-lookup"><span data-stu-id="79d26-186">**Evaluation results of policy conditions** - A read-only report showing whether the conditions of the DAC deployment policy succeeded.</span></span> <span data-ttu-id="79d26-187">評估每個條件的結果會在個別行上報告。</span><span class="sxs-lookup"><span data-stu-id="79d26-187">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="79d26-188">將 DAC 部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]時，下列選取伺服器原則永遠評估為 false：作業系統版本、語言、具名管道已啟用、平台和 tcp 已啟用。</span><span class="sxs-lookup"><span data-stu-id="79d26-188">The following server selection policies always evaluate to false when deploying a DAC to [!INCLUDE[ssSDS](../../includes/sssds-md.md)]: operating system version, language, named pipes enabled, platform, and tcp enabled.</span></span>  
  
 <span data-ttu-id="79d26-189">**忽略違反原則** - 使用這個核取方塊可在一個或多個原則條件失敗時繼續部署。</span><span class="sxs-lookup"><span data-stu-id="79d26-189">**Ignore policy violations** - Use this check box to proceed with the deployment if one or more of the policy conditions failed.</span></span> <span data-ttu-id="79d26-190">只有當您確定所有失敗的條件都不會阻礙 DAC 作業的成功時，才選取此選項。</span><span class="sxs-lookup"><span data-stu-id="79d26-190">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="79d26-191">\*\* \< 上一步**-回到 [**選取封裝\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-191">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="79d26-192">**下一步 >** - 繼續進行 [更新組態]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-192">**Next >** - Proceeds to the **Update Configureation** page.</span></span>  
  
 <span data-ttu-id="79d26-193">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-193">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="update-configuration-page"></a><a name="Update_configuration"></a><span data-ttu-id="79d26-194">[更新設定] 頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-194">Update Configuration Page</span></span>  
 <span data-ttu-id="79d26-195">使用此頁面來指定部署作業所建立之部署的 DAC 執行個體和資料庫名稱，並設定資料庫選項。</span><span class="sxs-lookup"><span data-stu-id="79d26-195">Use this page to specify the names of the deployed DAC instance and the database created by the deployment, and to set database options.</span></span>  
  
 <span data-ttu-id="79d26-196">**資料庫名稱:** - 指定部署作業所要建立的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-196">**Database Name:** - Specify the name of the database to be created by the deployment.</span></span> <span data-ttu-id="79d26-197">預設值是擷取 DAC 的來源資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-197">The default is the name of the source database the DAC was extracted from.</span></span> <span data-ttu-id="79d26-198">此名稱在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體內必須是唯一的，且必須符合 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 識別碼的規則。</span><span class="sxs-lookup"><span data-stu-id="79d26-198">The name must be unique within the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and comply with the rules for [!INCLUDE[ssDE](../../includes/ssde-md.md)] identifiers.</span></span>  
  
 <span data-ttu-id="79d26-199">如果您變更資料庫名稱，則資料檔和記錄檔的名稱也會變更，以符合新的值。</span><span class="sxs-lookup"><span data-stu-id="79d26-199">If you change the database name, the names of the data file and log files will change to match the new value.</span></span>  
  
 <span data-ttu-id="79d26-200">資料庫名稱也會當做 DAC 執行個體的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="79d26-200">The database name is also used as the name of the DAC instance.</span></span> <span data-ttu-id="79d26-201">執行個體名稱會顯示在**物件總管**中 [資料層應用程式]  節點或是**公用程式總管**中 [部署的資料層應用程式]  節點底下的 DAC 節點上。</span><span class="sxs-lookup"><span data-stu-id="79d26-201">The instance name is displayed on the node for the DAC under the **Data-tier Applications** node in **Object Explorer**, or the **Deployed Data-tier Applications** node in the **Utility Explorer**.</span></span>  
  
 <span data-ttu-id="79d26-202">下列選項不適用於 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]，也不會在部署至 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]時顯示。</span><span class="sxs-lookup"><span data-stu-id="79d26-202">The following options do not apply to [!INCLUDE[ssSDS](../../includes/sssds-md.md)], and are not displayed when deploying to [!INCLUDE[ssSDS](../../includes/sssds-md.md)].</span></span>  
  
 <span data-ttu-id="79d26-203">**使用預設資料庫位置** - 選取此選項，可在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的預設位置中建立資料庫資料檔和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="79d26-203">**Use the default database location** - Select this option to create the database data and log files in the default location for the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="79d26-204">檔案名稱將會使用資料庫名稱來建置。</span><span class="sxs-lookup"><span data-stu-id="79d26-204">The file names will be built using the database name.</span></span>  
  
 <span data-ttu-id="79d26-205">**指定資料庫檔案** - 選取此選項可針對資料檔和記錄檔指定不同的位置或名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-205">**Specify database files** - Select this option to specify a different location or name for the data and log files.</span></span>  
  
 <span data-ttu-id="79d26-206">**資料檔路徑和名稱:** - 為資料檔指定完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-206">**Data file path and name: -** Specify the full path and file name for the data file.</span></span> <span data-ttu-id="79d26-207">此方塊中會填入預設路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-207">The box is populated with the default path and file name.</span></span> <span data-ttu-id="79d26-208">在此方塊中編輯字串來變更預設值，或使用 [瀏覽] 按鈕導覽至放置資料檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79d26-208">Edit the string in the box to change the default, or use the Browse button to navigate to the folder where the data file is to be placed.</span></span>  
  
 <span data-ttu-id="79d26-209">**記錄檔路徑和名稱:** - 為記錄檔指定完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-209">**Log file path and name:** - Specify the full path and file name for the log file.</span></span> <span data-ttu-id="79d26-210">此方塊中會填入預設路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-210">The box is populated with the default path and file name.</span></span> <span data-ttu-id="79d26-211">在此方塊中編輯字串來變更預設值，或使用 **[瀏覽]** 按鈕導覽至放置記錄檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="79d26-211">Edit the string in the box to change the default, or use the **Browse** button to navigate to the folder where the log file is to be placed.</span></span>  
  
 <span data-ttu-id="79d26-212">\*\* \< 上一步**-回到 [**選取 DAC 封裝\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-212">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="79d26-213">**下一步 >** - 繼續進行 [摘要]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="79d26-213">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="79d26-214">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-214">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="79d26-215">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-215">Summary Page</span></span>  
 <span data-ttu-id="79d26-216">使用此頁面來檢閱部署 DAC 時，精靈將會採取的動作。</span><span class="sxs-lookup"><span data-stu-id="79d26-216">Use this page to review the actions the wizard will take when deploying the DAC.</span></span>  
  
 <span data-ttu-id="79d26-217">**將使用以下設定部署您的 DAC**</span><span class="sxs-lookup"><span data-stu-id="79d26-217">**The following settings will be used to deploy your DAC.**</span></span> <span data-ttu-id="79d26-218">- 檢閱顯示的資訊，以確保採取的動作將會是正確的。</span><span class="sxs-lookup"><span data-stu-id="79d26-218">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="79d26-219">此視窗會顯示您所選取的 DAC 封裝以及您針對部署的 DAC 執行個體所選取的名稱。</span><span class="sxs-lookup"><span data-stu-id="79d26-219">The window displays the DAC package you selected, and the name you selected for the deployed DAC instance.</span></span> <span data-ttu-id="79d26-220">此視窗也會顯示當您建立與 DAC 相關聯的資料庫時，將要使用的設定。</span><span class="sxs-lookup"><span data-stu-id="79d26-220">The window also displays the settings that will be used when creating the database associated with the DAC.</span></span>  
  
 <span data-ttu-id="79d26-221">\*\* \< 上一步**-回到 [**更新\*\*設定] 頁面，變更您的選擇。</span><span class="sxs-lookup"><span data-stu-id="79d26-221">**\< Previous** - Returns you to the **Update Configuration** page to change your selections.</span></span>  
  
 <span data-ttu-id="79d26-222">**下一步 >** - 部署 DAC，並在 [部署 DAC]\*\*\*\* 頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="79d26-222">**Next >** - Deploys the DAC and displays the results in the **Deploy DAC** page.</span></span>  
  
 <span data-ttu-id="79d26-223">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-223">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="deploy-page"></a><a name="Deploy"></a><span data-ttu-id="79d26-224">[部署] 頁面</span><span class="sxs-lookup"><span data-stu-id="79d26-224">Deploy Page</span></span>  
 <span data-ttu-id="79d26-225">此頁面會報告部署作業成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="79d26-225">This page reports the success or failure of the deploy operation.</span></span>  
  
 <span data-ttu-id="79d26-226">**正在部署 DAC** - 報告為了部署 DAC 所採取的每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="79d26-226">**Deploying the DAC** - Reports the success or failure of each action taken to deploy the DAC.</span></span> <span data-ttu-id="79d26-227">檢閱資訊以判斷每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="79d26-227">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="79d26-228">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="79d26-228">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="79d26-229">選取連結來檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="79d26-229">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="79d26-230">**儲存報表** - 選取此按鈕可以將部署報告儲存到 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="79d26-230">**Save Report** - Select this button to save the deployment report to an HTML file.</span></span> <span data-ttu-id="79d26-231">此檔案會報告每個動作的狀態，包括所有動作所產生的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="79d26-231">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="79d26-232">預設資料夾為 Windows 帳戶之文件資料夾中的 SQL Server Management Studio\DAC Packages 資料夾。</span><span class="sxs-lookup"><span data-stu-id="79d26-232">The default folder is the SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="79d26-233">**完成** - 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="79d26-233">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="DeployDACPowerShell"></a> <span data-ttu-id="79d26-234">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="79d26-234">Using PowerShell</span></span>  
 <span data-ttu-id="79d26-235">**在 PowerShell 指令碼中使用 Install() 方法部署 DAC**</span><span class="sxs-lookup"><span data-stu-id="79d26-235">**To deploy a DAC using the Install() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="79d26-236">建立 SMO Server 物件，並將它設為您要部署 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="79d26-236">Create a SMO Server object and set it to the instance to which you want to deploy the DAC.</span></span>  
  
2.  <span data-ttu-id="79d26-237">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="79d26-237">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="79d26-238">使用 `System.IO.File` 以載入 DAC 封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="79d26-238">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="79d26-239">您可以使用 `add_DacActionStarted` 和 `add_DacActionFinished` 訂閱 DAC 部署事件。</span><span class="sxs-lookup"><span data-stu-id="79d26-239">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC deployment events.</span></span>  
  
5.  <span data-ttu-id="79d26-240">設定 `DatabaseDeploymentProperties`。</span><span class="sxs-lookup"><span data-stu-id="79d26-240">Set the `DatabaseDeploymentProperties`.</span></span>  
  
6.  <span data-ttu-id="79d26-241">您可以使用 `DacStore.Install` 方法來部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-241">Use the `DacStore.Install` method to deploy the DAC.</span></span>  
  
7.  <span data-ttu-id="79d26-242">關閉用來讀取 DAC 封裝檔案的檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="79d26-242">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="79d26-243">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="79d26-243">Example (PowerShell)</span></span>  
 <span data-ttu-id="79d26-244">下列範例使用 MyApplication.dacpac 封裝中 DAC 定義來部署 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之預設執行個體上名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="79d26-244">The following example deploys a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a DAC definition from a MyApplication.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC deployment events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Deploy the DAC and create the database.  
$dacName  = "MyApplication"  
$evaluateTSPolicy = $true  
$deployProperties = New-Object Microsoft.SqlServer.Management.Dac.DatabaseDeploymentProperties($serverconnection,$dacName)  
$dacstore.Install($dacType, $deployProperties, $evaluateTSPolicy)  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="79d26-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79d26-245">See Also</span></span>  
 <span data-ttu-id="79d26-246">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="79d26-246">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="79d26-247">[從資料庫中擷取 DAC](extract-a-dac-from-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="79d26-247">[Extract a DAC From a Database](extract-a-dac-from-a-database.md) </span></span>  
 [<span data-ttu-id="79d26-248">資料庫識別碼</span><span class="sxs-lookup"><span data-stu-id="79d26-248">Database Identifiers</span></span>](../databases/database-identifiers.md)  
