---
title: 將資料庫註冊為 DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4e8061362d013dbfbd6cbaba47d0f2cb4d8e83b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606883"
---
# <a name="register-a-database-as-a-dac"></a><span data-ttu-id="ee566-102">將資料庫註冊為 DAC</span><span class="sxs-lookup"><span data-stu-id="ee566-102">Register a Database As a DAC</span></span>
  <span data-ttu-id="ee566-103">使用 [**註冊資料層應用程式嚮導]** 或 Windows PowerShell 腳本來建立資料層應用程式 (DAC) 定義，以描述現有資料庫中的物件，並 `msdb` 在) 的系統 (資料庫中註冊 dac 定義**master** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee566-103">Use either the **Register Data-tier Application Wizard** or a Windows PowerShell script to build a data-tier application (DAC) definition that describes the objects in an existing database, and register the DAC definition in the `msdb` system database (**master** in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]).</span></span>  
  
-   <span data-ttu-id="ee566-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ee566-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ee566-105">**若要升級 DAC，請使用下列方式：** [註冊資料層應用程式精靈](#UsingRegisterDACWizard)、[PowerShell](#RegisterDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="ee566-105">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ee566-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="ee566-106">Before You Begin</span></span>  
 <span data-ttu-id="ee566-107">註冊程序會建立 DAC 定義，以定義資料庫中的物件。</span><span class="sxs-lookup"><span data-stu-id="ee566-107">The registration process creates a DAC definition that defines the objects in the database.</span></span> <span data-ttu-id="ee566-108">DAC 定義和資料庫的組合會形成 DAC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee566-108">The combination of the DAC definition and the database form a DAC instance.</span></span> <span data-ttu-id="ee566-109">如果將資料庫註冊為 Database Engine 之受管理的執行個體上的 DAC，下次從執行個體將公用程式收集組傳送到公用程式控制點時，註冊的 DAC 將會合併到 SQL Server 公用程式中。</span><span class="sxs-lookup"><span data-stu-id="ee566-109">If you register a database as a DAC on a managed instance of the Database Engine, the registered DAC will be incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the Utility Control Point.</span></span> <span data-ttu-id="ee566-110">然後 DAC 會出現在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] [公用程式總管] 的 [部署的資料層應用程式] 節點中，並在 [部署的資料層應用程式] 詳細資料頁面中報告。</span><span class="sxs-lookup"><span data-stu-id="ee566-110">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ee566-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="ee566-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ee566-112">DAC 註冊只能在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更新版本的資料庫上執行。</span><span class="sxs-lookup"><span data-stu-id="ee566-112">DAC registration can only be performed on a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="ee566-113">如果已經針對資料庫註冊 DAC，將無法執行 DAC 註冊。</span><span class="sxs-lookup"><span data-stu-id="ee566-113">DAC registration cannot be performed if a DAC is already registered for the database.</span></span> <span data-ttu-id="ee566-114">例如，如果資料庫是藉由部署 DAC 所建立，您將無法執行 [註冊資料層應用程式精靈]。</span><span class="sxs-lookup"><span data-stu-id="ee566-114">For example, if the database was created by deploying a DAC, you cannot run the **Register Data-tier Application Wizard**.</span></span>  
  
 <span data-ttu-id="ee566-115">如果 DAC 或包含的使用者中不支援資料庫中的物件，則無法註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-115">You cannot register a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="ee566-116">如需有關 DAC 中支援之物件類型的詳細資訊，請參閱＜ [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ee566-116">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ee566-117">權限</span><span class="sxs-lookup"><span data-stu-id="ee566-117">Permissions</span></span>  
 <span data-ttu-id="ee566-118">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體中註冊 DAC 至少需要 ALTER ANY LOGIN 和資料庫範圍 VIEW DEFINITION 權限、 **sys.sql_expression_dependencies**的 SELECT 權限，以及 **dbcreator** 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ee566-118">Registering a DAC in an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, SELECT permissions on **sys.sql_expression_dependencies**, and membership in the **dbcreator** fixed server role.</span></span> <span data-ttu-id="ee566-119">**系統管理員** 固定伺服器角色的成員或是內建 SQL Server 系統管理員帳戶 **sa** 也可以註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-119">Members of the **sysadmin** fixed server role or the built-in SQL Server system administrator account named **sa** can also register a DAC.</span></span> <span data-ttu-id="ee566-120">在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中註冊不包含登入的 DAC，需要 **dbmanager** 或 **serveradmin** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ee566-120">Registering a DAC that does not contain logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **dbmanager** or **serveradmin** roles.</span></span> <span data-ttu-id="ee566-121">在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 中註冊包含登入的 DAC，需要 **loginmanager** 或 **serveradmin** 角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="ee566-121">Registering a DAC that contains logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **loginmanager** or **serveradmin** roles.</span></span>  
  
##  <a name="using-the-register-data-tier-application-wizard"></a><a name="UsingRegisterDACWizard"></a> <span data-ttu-id="ee566-122">使用註冊資料層應用程式精靈</span><span class="sxs-lookup"><span data-stu-id="ee566-122">Using the Register Data-tier Application Wizard</span></span>  
 <span data-ttu-id="ee566-123">**使用精靈註冊 DAC**</span><span class="sxs-lookup"><span data-stu-id="ee566-123">**To Register a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="ee566-124">在 **[物件總管]** 中，展開含有要註冊為 DAC 的資料庫之執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="ee566-124">In **Object Explorer**, expand the node for the instance containing the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="ee566-125">展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ee566-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="ee566-126">以滑鼠右鍵按一下要註冊的資料庫，指向 [工作]，然後選取 [註冊為資料層應用程式…]</span><span class="sxs-lookup"><span data-stu-id="ee566-126">Right-click the database to be registered, point to **Tasks**, and then select **Register As Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="ee566-127">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="ee566-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="ee566-128">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="ee566-129">設定屬性頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-129">Set Properties Page</span></span>](#Set_properties)  
  
    3.  [<span data-ttu-id="ee566-130">驗證與摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-130">Validation and Summary Page</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="ee566-131">註冊 DAC 頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-131">Register DAC Page</span></span>](#Register)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="ee566-132">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-132">Introduction Page</span></span>  
 <span data-ttu-id="ee566-133">此頁面描述註冊資料層應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="ee566-133">This page describes the steps for registering a data-tier application.</span></span>  
  
 <span data-ttu-id="ee566-134">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="ee566-134">**Do not show this page again.**</span></span> <span data-ttu-id="ee566-135">- 按一下此核取方塊，之後就不會再顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="ee566-135">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="ee566-136">**下一步 >** - 繼續進行 [設定屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ee566-136">**Next >** - Proceeds to the **Set Properties** page.</span></span>  
  
 <span data-ttu-id="ee566-137">**取消** - 結束精靈，而不註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-137">**Cancel** - Terminates the wizard without registering a DAC.</span></span>  
  
##  <a name="set-properties-page"></a><a name="Set_properties"></a> <span data-ttu-id="ee566-138">設定屬性頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-138">Set Properties Page</span></span>  
 <span data-ttu-id="ee566-139">使用此頁面來指定 DAC 層級屬性，例如應用程式名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="ee566-139">Use this page to specify DAC-level properties such as the application name and version.</span></span>  
  
 <span data-ttu-id="ee566-140">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="ee566-140">**Application name.**</span></span> <span data-ttu-id="ee566-141">- 字串，用來識別 DAC 定義的名稱，此欄位已經填入資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ee566-141">- A string that specifies the name used to identify the DAC definition, the field is been populated with the database name.</span></span>  
  
 <span data-ttu-id="ee566-142">**版本。**</span><span class="sxs-lookup"><span data-stu-id="ee566-142">**Version.**</span></span> <span data-ttu-id="ee566-143">- 可識別 DAC 版本的數值。</span><span class="sxs-lookup"><span data-stu-id="ee566-143">- A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="ee566-144">DAC 版本會用於 Visual Studio 中，以便識別開發人員正在處理的 DAC 版本。</span><span class="sxs-lookup"><span data-stu-id="ee566-144">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="ee566-145">部署 DAC 時，版本會儲存在資料庫中， `msdb` 並可于稍後在的 [**資料層應用程式**] 節點下查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee566-145">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="ee566-146">**描述**</span><span class="sxs-lookup"><span data-stu-id="ee566-146">**Description.**</span></span> <span data-ttu-id="ee566-147">- 選擇性。</span><span class="sxs-lookup"><span data-stu-id="ee566-147">- Optional.</span></span> <span data-ttu-id="ee566-148">說明 DAC 用途的文字。</span><span class="sxs-lookup"><span data-stu-id="ee566-148">Text that explains the purpose of the DAC.</span></span> <span data-ttu-id="ee566-149">部署 DAC 時，此描述會儲存在資料庫中， `msdb` 並可于稍後在的 [**資料層應用程式**] 節點下查看 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ee566-149">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="ee566-150">\*\* \< 上一步**-將您返回 [**簡介\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ee566-150">**\< Previous** - Returns you to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="ee566-151">**下一步 >** - 確認 DAC 可以從資料庫的物件建立而來，並在 [驗證與摘要] 頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ee566-151">**Next >** - Verifies that a DAC can be built from the objects in the database, and displays the results in the **Validation and Summary** page.</span></span>  
  
 <span data-ttu-id="ee566-152">**取消** - 結束精靈，而不註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-152">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="validation-and-summary-page"></a><a name="Summary"></a> <span data-ttu-id="ee566-153">驗證與摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-153">Validation and Summary Page</span></span>  
 <span data-ttu-id="ee566-154">使用此頁面來檢閱註冊 DAC 時，精靈將會採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ee566-154">Use this page to review the actions the wizard will take when registering the DAC.</span></span> <span data-ttu-id="ee566-155">當精靈驗證可以從資料庫中的物件建立 DAC 時，此頁面會在三種狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="ee566-155">The page transitions through three states as it verifies that a DAC can be built from the objects in the database.</span></span>  
  
### <a name="retrieving-objects"></a><span data-ttu-id="ee566-156">擷取物件</span><span class="sxs-lookup"><span data-stu-id="ee566-156">Retrieving Objects</span></span>  
 <span data-ttu-id="ee566-157">**擷取資料庫與伺服器物件。**</span><span class="sxs-lookup"><span data-stu-id="ee566-157">**Retrieving database and server objects.**</span></span> <span data-ttu-id="ee566-158">- 當精靈從資料庫及 Database Engine 執行個體擷取所有必要的物件時，將會顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="ee566-158">- Displays a progress bar as the wizard retrieves all of the required objects from the database and the instance of the Database Engine.</span></span>  
  
 <span data-ttu-id="ee566-159">\*\* \< 上一步**-返回 [**設定屬性\*\*] 頁面來變更您的專案。</span><span class="sxs-lookup"><span data-stu-id="ee566-159">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="ee566-160">**下一步 >** - 註冊 DAC，並在 [註冊 DAC] 頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ee566-160">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="ee566-161">**取消** - 結束精靈，而不註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-161">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="validating-objects"></a><span data-ttu-id="ee566-162">驗證物件</span><span class="sxs-lookup"><span data-stu-id="ee566-162">Validating Objects</span></span>  
 <span data-ttu-id="ee566-163">**檢查**_SchemaName_ **.**</span><span class="sxs-lookup"><span data-stu-id="ee566-163">**Checking**  _SchemaName_ **.**</span></span> <span data-ttu-id="ee566-164">_ObjectName_ **。**</span><span class="sxs-lookup"><span data-stu-id="ee566-164">_ObjectName_ **.**</span></span> <span data-ttu-id="ee566-165">- 當精靈驗證擷取之物件的相依性，並驗證這些對於 DAC 都是有效的物件時，將會顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="ee566-165">- Displays a progress bar as the wizard verifies the dependencies of the retrieved objects, and verifies that they are all valid objects for a DAC.</span></span> <span data-ttu-id="ee566-166">_SchemaName_ **.** _ObjectName_ 識別目前正在驗證哪一個物件。</span><span class="sxs-lookup"><span data-stu-id="ee566-166">_SchemaName_**.**_ObjectName_ identify which object is currently being verified.</span></span>  
  
 <span data-ttu-id="ee566-167">\*\* \< 上一步**-返回 [**設定屬性\*\*] 頁面來變更您的專案。</span><span class="sxs-lookup"><span data-stu-id="ee566-167">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="ee566-168">**下一步 >** - 註冊 DAC，並在 [註冊 DAC] 頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ee566-168">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="ee566-169">**取消** - 結束精靈，而不註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-169">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="summary"></a><span data-ttu-id="ee566-170">摘要</span><span class="sxs-lookup"><span data-stu-id="ee566-170">Summary</span></span>  
 <span data-ttu-id="ee566-171">**下列設定將用來註冊 DAC。**</span><span class="sxs-lookup"><span data-stu-id="ee566-171">**The following setting will be used to register your DAC.**</span></span> <span data-ttu-id="ee566-172">- 顯示將包含在 DAC 中的屬性和物件的報表。</span><span class="sxs-lookup"><span data-stu-id="ee566-172">- Displays a report of the properties and objects that will be included in the DAC.</span></span>  
  
 <span data-ttu-id="ee566-173">**儲存報表** - 選取此按鈕可以將驗證報告複本儲存到 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee566-173">**Save Report** - Select this button to save a copy of the validation report to an HTML file.</span></span> <span data-ttu-id="ee566-174">預設資料夾為 Windows 帳戶之 [文件] 資料夾中的 **SQL Server Management Studio\DAC Packages** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ee566-174">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="ee566-175">\*\* \< 上一步**-返回 [**設定屬性\*\*] 頁面來變更您的專案。</span><span class="sxs-lookup"><span data-stu-id="ee566-175">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="ee566-176">**下一步 >** - 註冊 DAC，並在 [註冊 DAC] 頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ee566-176">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="ee566-177">**取消** - 結束精靈，而不註冊 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-177">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="register-dac-page"></a><a name="Register"></a> <span data-ttu-id="ee566-178">註冊 DAC 頁面</span><span class="sxs-lookup"><span data-stu-id="ee566-178">Register DAC Page</span></span>  
 <span data-ttu-id="ee566-179">此頁面會報告註冊作業成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ee566-179">This page reports the success or failure of the registration.</span></span>  
  
 <span data-ttu-id="ee566-180">**註冊 DAC** - 報告為了註冊 DAC 所採取的每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ee566-180">**Registering the DAC** - Reports the success or failure of each action taken to register the DAC.</span></span> <span data-ttu-id="ee566-181">檢閱資訊以判斷每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ee566-181">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="ee566-182">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="ee566-182">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="ee566-183">選取連結來檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="ee566-183">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="ee566-184">**儲存報表** - 選取此按鈕可以將註冊報告儲存到 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee566-184">**Save Report** - Select this button to save the registration report to an HTML file.</span></span> <span data-ttu-id="ee566-185">此檔案會報告每個動作的狀態，包括所有動作所產生的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ee566-185">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="ee566-186">預設資料夾為 Windows 帳戶之 [文件] 資料夾中的 **SQL Server Management Studio\DAC Packages** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ee566-186">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span> <span data-ttu-id="ee566-187">檔案名稱格式為 \<DACPackageName>_RegisterDACReport_yyyymmdd.html，其中 \<*DACPackageName*> 是要部署之套件的名稱、*yyyy* = 目前的年份、*mm* = 目前的月份，而 *dd* = 目前的日期。</span><span class="sxs-lookup"><span data-stu-id="ee566-187">The file name is in the format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, where \<*DACPackageName*> is the name of the package being deployed, *yyyy* = the current year, *mm* = the current month, and *dd* = the current day.</span></span>  
  
 <span data-ttu-id="ee566-188">**完成** - 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="ee566-188">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="register-a-dac-using-powershell"></a><a name="RegisterDACPowerShell"></a> <span data-ttu-id="ee566-189">使用 PowerShell 註冊 DAC</span><span class="sxs-lookup"><span data-stu-id="ee566-189">Register a DAC Using PowerShell</span></span>  
 <span data-ttu-id="ee566-190">**若要在 PowerShell 指令碼中使用 Register() 方法，將資料庫註冊為 DAC**</span><span class="sxs-lookup"><span data-stu-id="ee566-190">**To register a database as a DAC using the Register() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="ee566-191">建立 SMO Server 物件，並將它設定為包含要註冊為 DAC 之資料庫的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ee566-191">Create a SMO Server object and set it to the instance that contains the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="ee566-192">加入可指定資料庫名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="ee566-192">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="ee566-193">指定 DAC 的中繼資料，例如 DAC 名稱、版本及描述。</span><span class="sxs-lookup"><span data-stu-id="ee566-193">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="ee566-194">使用上述指定的資訊執行 Register 方法。</span><span class="sxs-lookup"><span data-stu-id="ee566-194">Run the Register method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="ee566-195">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ee566-195">Example (PowerShell)</span></span>  
 <span data-ttu-id="ee566-196">下列範例會將名稱為 MyDB 的資料庫註冊為 DAC。</span><span class="sxs-lookup"><span data-stu-id="ee566-196">The following example registers a database named MyDB as a DAC.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee566-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee566-197">See Also</span></span>  
 [<span data-ttu-id="ee566-198">資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="ee566-198">Data-tier Applications</span></span>](data-tier-applications.md)  
