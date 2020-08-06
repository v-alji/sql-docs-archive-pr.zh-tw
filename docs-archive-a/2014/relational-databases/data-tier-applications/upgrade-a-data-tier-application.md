---
title: 升級資料層應用程式 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.upgradedacwizard.reviewpolicy.f1
- sql12.swb.upgradedacwizard.selectoptions.f1
- sql12.swb.upgradedacwizard.selectpackage.f1
- sql12.swb.upgradedacwizard.reviewplan.f1
- sql12.swb.upgradedacwizard.checkdrift.f1
- sql12.swb.upgradedacwizard.summary.f1
- sql12.swb.upgradedacwizard.upgradedac.f1
- sql12.swb.upgradedacwizard.introduction.f1
helpviewer_keywords:
- upgrade DAC
- data-tier application [SQL Server], upgrade
- wizard [DAC], upgrade
- How to [DAC], upgrade
ms.assetid: c117df94-f02b-403f-9383-ec5b3ac3763c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e597d02af28a16539b50ff76503059278ef7a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606369"
---
# <a name="upgrade-a-data-tier-application"></a><span data-ttu-id="ff70b-102">升級資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="ff70b-102">Upgrade a Data-tier Application</span></span>
  <span data-ttu-id="ff70b-103">您可以使用升級資料層應用程式精靈或 Windows PowerShell 指令碼，將目前部署之資料層應用程式 (DAC) 的結構描述和屬性變更為符合新版 DAC 中所定義的結構描述和屬性。</span><span class="sxs-lookup"><span data-stu-id="ff70b-103">Use either the Upgrade Data-tier Application Wizard or a Windows PowerShell script to change the schema and properties of a currently deployed data-tier application (DAC) to match the schema and properties defined in a new version of the DAC.</span></span>  
  
-   <span data-ttu-id="ff70b-104">**開始之前：** [選擇 DAC 升級選項](#ChoseDACUpgOptions)、[限制事項](#LimitationsRestrictions)、[必要條件](#Prerequisites)、[安全性](#Security)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ff70b-104">**Before you begin:**  [Choosing DAC Upgrade Options](#ChoseDACUpgOptions), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ff70b-105">**若要升級 DAC，請使用下列方式：** [升級資料層應用程式精靈](#UsingDACUpgradeWizard)、[PowerShell](#UpgradeDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="ff70b-105">**To upgrade a DAC, using:**  [The Upgrade Data-tier Application Wizard](#UsingDACUpgradeWizard), [PowerShell](#UpgradeDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ff70b-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="ff70b-106">Before You Begin</span></span>  
 <span data-ttu-id="ff70b-107">DAC 升級是一種就地升級程序，可改變現有資料庫的結構描述，以符合新版 DAC 中所定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ff70b-107">A DAC upgrade is an in-place process that alters the schema of the existing database to match the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="ff70b-108">在 DAC 封裝檔案中，會套用新版 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-108">The new version of the DAC is supplied in a DAC package file.</span></span> <span data-ttu-id="ff70b-109">如需建立 DAC 封裝的詳細資訊，請參閱 [資料層應用程式](data-tier-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ff70b-109">For more information about creating a DAC package, see [Data-tier Applications](data-tier-applications.md).</span></span>  
  
###  <a name="choosing-dac-upgrade-options"></a><a name="ChoseDACUpgOptions"></a> <span data-ttu-id="ff70b-110">選擇 DAC 升級選項</span><span class="sxs-lookup"><span data-stu-id="ff70b-110">Choosing DAC Upgrade Options</span></span>  
 <span data-ttu-id="ff70b-111">就地升級有四個升級選項：</span><span class="sxs-lookup"><span data-stu-id="ff70b-111">There are four upgrade options for an in-place upgrade:</span></span>  
  
-   <span data-ttu-id="ff70b-112">**忽略資料遺失**-如果為 `True` ，即使某些作業導致資料遺失，升級仍會繼續。</span><span class="sxs-lookup"><span data-stu-id="ff70b-112">**Ignore Data Loss** - If `True`, the upgrade will proceed even if some of the operations result in the loss of data.</span></span> <span data-ttu-id="ff70b-113">若為 `False`，這些作業將會結束升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-113">If `False`, these operations will terminate the upgrade.</span></span> <span data-ttu-id="ff70b-114">例如，如果目前資料庫中的資料表不在新 DAC 的結構描述中，則會在指定 `True` 時卸除資料表。</span><span class="sxs-lookup"><span data-stu-id="ff70b-114">For example, if a table in the current database is not present in the schema of the new DAC, the table will be dropped if `True` is specified.</span></span> <span data-ttu-id="ff70b-115">預設設定是 `True`。</span><span class="sxs-lookup"><span data-stu-id="ff70b-115">The default setting is `True`.</span></span>  
  
-   <span data-ttu-id="ff70b-116">**變更時封鎖**-如果 `True` ，如果資料庫架構與先前 DAC 中定義的不同，則會終止升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-116">**Block on Changes** - If `True`, the upgrade is terminated if the database schema is different than that defined in the previous DAC.</span></span> <span data-ttu-id="ff70b-117">若為 `False`，即使偵測到變更，升級仍會繼續。</span><span class="sxs-lookup"><span data-stu-id="ff70b-117">If `False`, the upgrade continues even if changes are detected.</span></span> <span data-ttu-id="ff70b-118">預設設定是 `False`。</span><span class="sxs-lookup"><span data-stu-id="ff70b-118">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="ff70b-119">**失敗時回復**-如果 `True` ，升級會包含在交易中，而且如果發生錯誤，則會嘗試回復。</span><span class="sxs-lookup"><span data-stu-id="ff70b-119">**Rollback on Failure** - If `True`, the upgrade is enclosed in a transaction, and if errors are encountered a rollback will be attempted.</span></span> <span data-ttu-id="ff70b-120">若為 `False`，將會認可所有變更，而如果發生錯誤，您可能必須還原資料庫的先前備份。</span><span class="sxs-lookup"><span data-stu-id="ff70b-120">If `False`, all changes are committed as they are made and if errors occur you may have to restore a previous backup of the database.</span></span> <span data-ttu-id="ff70b-121">預設設定是 `False`。</span><span class="sxs-lookup"><span data-stu-id="ff70b-121">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="ff70b-122">**略過原則驗證**-如果為 `True` ，則不會評估 DAC 伺服器選取原則。</span><span class="sxs-lookup"><span data-stu-id="ff70b-122">**Skip Policy Validation** - If `True`, the DAC server selection policy is not evaluated.</span></span> <span data-ttu-id="ff70b-123">若為 `False`，則會評估原則，而如果發生驗證錯誤，則會結束升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-123">If `False`, the policy is evaluated and the upgrade terminates if there is a validation error.</span></span> <span data-ttu-id="ff70b-124">預設設定是 `False`。</span><span class="sxs-lookup"><span data-stu-id="ff70b-124">The default setting is `False`.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ff70b-125">限制事項</span><span class="sxs-lookup"><span data-stu-id="ff70b-125">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ff70b-126">DAC 升級只能在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更新版本中執行。</span><span class="sxs-lookup"><span data-stu-id="ff70b-126">DAC uprades can only be performed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ff70b-127">必要條件</span><span class="sxs-lookup"><span data-stu-id="ff70b-127">Prerequisites</span></span>  
 <span data-ttu-id="ff70b-128">您必須在開始升級之前，進行完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="ff70b-128">It is prudent to take a full database backup before starting the upgrade.</span></span> <span data-ttu-id="ff70b-129">如果升級時發生錯誤而無法回復其所有變更，您可能需要還原備份。</span><span class="sxs-lookup"><span data-stu-id="ff70b-129">If an upgrade encounters an error and cannot roll back all of its changes, you may need to restore the backup.</span></span>  
  
 <span data-ttu-id="ff70b-130">開始升級之前，有幾個您在驗證 DAC 封裝以及升級動作時應該採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ff70b-130">Before starting the upgrade, there are several actions that you should take to validate the DAC package and the upgrade actions.</span></span> <span data-ttu-id="ff70b-131">如需有關如何執行這些檢查的詳細資訊，請參閱＜ [Validate a DAC Package](validate-a-dac-package.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ff70b-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="ff70b-132">建議您不要使用來源不明或來源不受信任的 DAC 封裝來升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-132">We recommend that you do not upgrade by using a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="ff70b-133">這類封裝可能包含惡意程式碼，因此可能會執行非預期的 Transact-SQL 程式碼，或是修改結構描述而造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="ff70b-133">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="ff70b-134">在您使用來源不明或來源不受信任的封裝之前，請解除封裝 DAC 並檢查程式碼，例如預存程序或其他使用者定義程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff70b-134">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
-   <span data-ttu-id="ff70b-135">若您在部署最新版 DAC 之後變更目前的資料庫，某些變更可能會使升級無法成功完成，或因為升級而遭到移除。</span><span class="sxs-lookup"><span data-stu-id="ff70b-135">If changes have been made to the current database after the last version of the DAC was deployed, some of the changes may prevent the successful completion of the upgrade, or be removed by the upgrade.</span></span> <span data-ttu-id="ff70b-136">您應該先產生並檢閱包含對資料庫所做之任何這類變更的報表。</span><span class="sxs-lookup"><span data-stu-id="ff70b-136">You should first generate and review a report of any such changes made in the database.</span></span>  
  
-   <span data-ttu-id="ff70b-137">您必須產生要執行升級之結構描述變更的清單，並檢閱清單中是否有任何問題。</span><span class="sxs-lookup"><span data-stu-id="ff70b-137">It is prudent to generate a list of the schema changes the upgrade will perform, and review the list for any problems.</span></span>  
  
 <span data-ttu-id="ff70b-138">DAC 封裝中的應用程式名稱必須符合目前部署之 DAC 的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="ff70b-138">The application name in the DAC package must match the application name of the currently deployed DAC.</span></span> <span data-ttu-id="ff70b-139">例如，如果目前的 DAC 具有應用程式名稱 **GeneralLedger**，您只能使用同樣具有應用程式名稱 **GeneralLedger**的 DAC 封裝來升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-139">For example, if the current DAC has an application name of **GeneralLedger**, you can only upgrade by using a DAC package that also has an application name of **GeneralLedger**.</span></span>  
  
 <span data-ttu-id="ff70b-140">確定交易記錄空間足以記錄所有修改。</span><span class="sxs-lookup"><span data-stu-id="ff70b-140">Ensure there is enough transaction log space available to log all of the modifications.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ff70b-141">Security</span><span class="sxs-lookup"><span data-stu-id="ff70b-141">Security</span></span>  
 <span data-ttu-id="ff70b-142">為了提高安全性，SQL Server 驗證登入會儲存在 DAC 封裝中，而且沒有密碼。</span><span class="sxs-lookup"><span data-stu-id="ff70b-142">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="ff70b-143">當您部署或升級此封裝時，此登入會建立為停用的登入，而且會產生密碼。</span><span class="sxs-lookup"><span data-stu-id="ff70b-143">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="ff70b-144">若要啟用登入，請使用具有 ALTER ANY LOGIN 權限的登入進行登入，並使用 ALTER LOGIN 來啟用登入，然後指派可以傳達給使用者的新密碼。</span><span class="sxs-lookup"><span data-stu-id="ff70b-144">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="ff70b-145">Windows 驗證登入不需要這項處理，因為這類登入的密碼不是由 SQL Server 所管理。</span><span class="sxs-lookup"><span data-stu-id="ff70b-145">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ff70b-146">權限</span><span class="sxs-lookup"><span data-stu-id="ff70b-146">Permissions</span></span>  
 <span data-ttu-id="ff70b-147">DAC 只能由 **sysadmin** 或 **serveradmin** 固定伺服器角色的成員，或是具有 **dbcreator** 固定伺服器角色及擁有 ALTER ANY LOGIN 權限的登入進行升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-147">A DAC can only be upgraded by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="ff70b-148">登入必須是現有資料庫的擁有者。</span><span class="sxs-lookup"><span data-stu-id="ff70b-148">The login must be the owner of the existing database.</span></span> <span data-ttu-id="ff70b-149">內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶 (名稱為 **sa** ) 也可以升級 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-149">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also upgrade a DAC.</span></span>  
  
##  <a name="using-the-upgrade-data-tier-application-wizard"></a><a name="UsingDACUpgradeWizard"></a> <span data-ttu-id="ff70b-150">使用升級資料層應用程式精靈</span><span class="sxs-lookup"><span data-stu-id="ff70b-150">Using the Upgrade Data-tier Application Wizard</span></span>  
 <span data-ttu-id="ff70b-151">**使用精靈升級 DAC**</span><span class="sxs-lookup"><span data-stu-id="ff70b-151">**To Upgrade a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="ff70b-152">在 **[物件總管]** 中，展開含有要升級 DAC 之執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="ff70b-152">In **Object Explorer**, expand the node for the instance containing the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="ff70b-153">展開 [管理]  節點，然後展開 [資料層應用程式]  節點。</span><span class="sxs-lookup"><span data-stu-id="ff70b-153">Expand the **Management** node, and then expand the **Data-tier Applications** node.</span></span>  
  
3.  <span data-ttu-id="ff70b-154">以滑鼠右鍵按一下要升級之 DAC 的節點，然後選取 [升級資料層應用程式...] </span><span class="sxs-lookup"><span data-stu-id="ff70b-154">Right-click the node for the DAC to be upgraded, and then select **Upgrade Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="ff70b-155">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="ff70b-155">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="ff70b-156">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-156">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="ff70b-157">選取封裝頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-157">Select Package Page</span></span>](#Select_dac_package)  
  
    3.  [<span data-ttu-id="ff70b-158">檢閱原則頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-158">Review Policy Page</span></span>](#Review_policy)  
  
    4.  [<span data-ttu-id="ff70b-159">偵測變更頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-159">Detect Change Page</span></span>](#Detect_change)  
  
    5.  [<span data-ttu-id="ff70b-160">檢閱升級計畫</span><span class="sxs-lookup"><span data-stu-id="ff70b-160">Review the Upgrade Plan</span></span>](#ReviewUpgPlan)  
  
    6.  [<span data-ttu-id="ff70b-161">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-161">Summary Page</span></span>](#Summary)  
  
    7.  [<span data-ttu-id="ff70b-162">升級 DAC 頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-162">Upgrade DAC Page</span></span>](#Upgrade)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="ff70b-163">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-163">Introduction Page</span></span>  
 <span data-ttu-id="ff70b-164">此頁面描述升級資料層應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="ff70b-164">This page describes the steps for upgrading a data-tier application.</span></span>  
  
 <span data-ttu-id="ff70b-165">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="ff70b-165">**Do not show this page again.**</span></span> <span data-ttu-id="ff70b-166">- 按一下此核取方塊，之後就不會再顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-166">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="ff70b-167">**下一步 >** - 繼續進行 [選取封裝]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-167">**Next >** - Proceeds to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="ff70b-168">**取消** - 結束精靈，而不升級 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-168">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="select-package-page"></a><a name="Select_dac_package"></a> <span data-ttu-id="ff70b-169">選取封裝頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-169">Select Package Page</span></span>  
 <span data-ttu-id="ff70b-170">使用此頁面來指定包含新版資料層應用程式的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="ff70b-170">Use this page to specify the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="ff70b-171">此頁面會在兩種狀態之間轉換。</span><span class="sxs-lookup"><span data-stu-id="ff70b-171">The page transitions through two states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="ff70b-172">選取 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="ff70b-172">Select the DAC Package</span></span>  
 <span data-ttu-id="ff70b-173">使用此頁面的初始狀態來選擇要部署的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="ff70b-173">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="ff70b-174">DAC 封裝必須是有效的 DAC 封裝檔案，而且必須有 .dacpac 副檔名。</span><span class="sxs-lookup"><span data-stu-id="ff70b-174">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span> <span data-ttu-id="ff70b-175">DAC 封裝中的 DAC 應用程式名稱必須與目前 DAC 的應用程式名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ff70b-175">The DAC application name in the DAC package must be the same as the application name of the current DAC.</span></span>  
  
 <span data-ttu-id="ff70b-176">**DAC 封裝** - 指定包含新版資料層應用程式之 DAC 封裝的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ff70b-176">**DAC Package** - Specify the path and file name of the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="ff70b-177">您可以選取方塊右邊的 **[瀏覽]** 按鈕，瀏覽到 DAC 封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="ff70b-177">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="ff70b-178">**應用程式名稱** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示指派之 DAC 應用程式名稱的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="ff70b-178">**Application Name** - A read-only box that displays the DAC application name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="ff70b-179">**版本** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示指派之版本的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="ff70b-179">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="ff70b-180">**描述** - 當撰寫 DAC 或是從資料庫擷取 DAC 時，顯示撰寫之描述的唯讀方塊。</span><span class="sxs-lookup"><span data-stu-id="ff70b-180">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="ff70b-181">\*\* \< 上一步**-返回 [**簡介\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-181">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="ff70b-182">**下一步 >** - 將進度列顯示為確認選定檔案為有效 DAC 封裝的精靈。</span><span class="sxs-lookup"><span data-stu-id="ff70b-182">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="ff70b-183">**取消** - 結束精靈，而不升級 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-183">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="ff70b-184">驗證 DAC 封裝</span><span class="sxs-lookup"><span data-stu-id="ff70b-184">Validating the DAC Package</span></span>  
 <span data-ttu-id="ff70b-185">將進度列顯示為確認選定檔案為有效 DAC 封裝的精靈。</span><span class="sxs-lookup"><span data-stu-id="ff70b-185">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="ff70b-186">如果 DAC 封裝已經驗證，此精靈會繼續前往 **[檢閱原則]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-186">If the DAC package is validated, the wizard proceeds to the **Review Policy** page.</span></span> <span data-ttu-id="ff70b-187">如果檔案不是有效的 DAC 封裝，則精靈會停留在 **[選取 DAC 封裝]** 頁面上。</span><span class="sxs-lookup"><span data-stu-id="ff70b-187">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package** page.</span></span> <span data-ttu-id="ff70b-188">請選取另一個有效的 DAC 封裝，或是取消精靈並產生新的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="ff70b-188">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="ff70b-189">**正在驗證 DAC 的內容** - 報告驗證程序之目前狀態的進度列。</span><span class="sxs-lookup"><span data-stu-id="ff70b-189">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="ff70b-190">\*\* \< 上一步**-回到 [**選取封裝\*\*] 頁面的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="ff70b-190">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="ff70b-191">**下一步 >** - 繼續進行最終版本的 [選取封裝]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-191">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="ff70b-192">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-192">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a> <span data-ttu-id="ff70b-193">檢閱原則頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-193">Review Policy Page</span></span>  
 <span data-ttu-id="ff70b-194">使用此頁面來檢閱評估 DAC 伺服器選取原則的結果 (如果 DAC 有原則的話)。</span><span class="sxs-lookup"><span data-stu-id="ff70b-194">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="ff70b-195">DAC 伺服器選取原則為選擇性，而且當它在 Microsoft Visual Studio 中撰寫時會指派給 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-195">The DAC server selection policy is optional, and is assigned to a DAC authored in Microsoft Visual Studio.</span></span> <span data-ttu-id="ff70b-196">此原則會使用伺服器選取原則 Facet 來指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體主控 DAC 所應該符合的條件。</span><span class="sxs-lookup"><span data-stu-id="ff70b-196">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="ff70b-197">**原則條件的評估結果** - 唯讀報表，顯示 DAC 伺服器選取原則中的條件評估是否成功。</span><span class="sxs-lookup"><span data-stu-id="ff70b-197">**Evaluation results of policy conditions** - A read-only report showing whether the evaluations of the conditions in the DAC server selection policy succeeded.</span></span> <span data-ttu-id="ff70b-198">評估每個條件的結果會在個別行上報告。</span><span class="sxs-lookup"><span data-stu-id="ff70b-198">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="ff70b-199">**忽略違反原則** - 使用這個核取方塊可在一個或多個原則條件失敗時繼續升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-199">**Ignore policy violations** - Use this check box to proceed with the upgrade if one or more of the policy conditions failed.</span></span> <span data-ttu-id="ff70b-200">只有當您確定所有失敗的條件都不會阻礙 DAC 作業的成功時，才選取此選項。</span><span class="sxs-lookup"><span data-stu-id="ff70b-200">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="ff70b-201">\*\* \< 上一步**-回到 [**選取封裝\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-201">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="ff70b-202">**下一步 >** - 繼續進行 [偵測變更]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-202">**Next >** - Proceeds to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="ff70b-203">**取消** - 結束精靈，而不升級 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-203">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="detect-change-page"></a><a name="Detect_change"></a> <span data-ttu-id="ff70b-204">偵測變更頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-204">Detect Change Page</span></span>  
 <span data-ttu-id="ff70b-205">您可以使用此頁面報告此精靈檢查資料庫變更的結果，此結果會讓它的結構描述與 **msdb**中 DAC 中繼資料內儲存的結構描述定義不同。</span><span class="sxs-lookup"><span data-stu-id="ff70b-205">Use this page reports the results of the wizards check for changes made to the database that make it's schema different than the schema definition stored in the DAC metadata in **msdb**.</span></span> <span data-ttu-id="ff70b-206">例如，如果一開始部署 DAC 之後，已經使用 CREATE、ALTER 或 DROP 陳述式來從資料庫中加入、變更或移除物件。</span><span class="sxs-lookup"><span data-stu-id="ff70b-206">For example, if CREATE, ALTER, or DROP statements have been used to add, change, or remove objects from the database after the DAC was originally deployed.</span></span> <span data-ttu-id="ff70b-207">此頁面會先顯示進度列，然後報告分析的結果。</span><span class="sxs-lookup"><span data-stu-id="ff70b-207">The page first displays a progress bar, and then reports the results of the analysis.</span></span>  
  
 <span data-ttu-id="ff70b-208">**正在偵測變更。這可能需要幾分鐘時間** - 當精靈檢查目前的資料庫結構描述與 DAC 定義中的物件之間是否有差異時，將會顯示一個進度列。</span><span class="sxs-lookup"><span data-stu-id="ff70b-208">**Detecting change, this may take a few minutes** - Displays a progress bar as the wizard checks for differences between the current schema of the database and the objects in the DAC definition.</span></span>  
  
 <span data-ttu-id="ff70b-209">**變更偵測結果:** - 表示分析已完成，並在底下報告結果。</span><span class="sxs-lookup"><span data-stu-id="ff70b-209">**Change detection results:** - Indicates that the analysis has completed and the results are reported below.</span></span>  
  
 <span data-ttu-id="ff70b-210">**資料庫 DatabaseName 尚未變更** - 此精靈在資料庫內定義的物件與其在 DAC 定義內的對應物件之間並未偵測到任何差異。</span><span class="sxs-lookup"><span data-stu-id="ff70b-210">**The database DatabaseName has not changed** - The wizard detected no differences in the objects defined in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="ff70b-211">**資料庫 DatabaseName 已變更** - 此精靈在資料庫內的物件與其在 DAC 定義內的對應物件之間偵測到變更。</span><span class="sxs-lookup"><span data-stu-id="ff70b-211">**The database DatabaseName has changed** - The wizard detected changes between the objects in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="ff70b-212">**儘管變更可能遺失，還是繼續進行** - 指定您了解目前資料庫中的某些物件或資料將不會出現在新的資料庫中，但是您仍然願意繼續升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-212">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="ff70b-213">只有當您已經分析變更報表，並了解手動傳送新資料庫中所需之任何物件或資料所必須執行的步驟時，才應該選取這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff70b-213">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="ff70b-214">如果您不確定，請按一下 **[儲存報表]** 按鈕儲存變更報表，然後按一下 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="ff70b-214">If you are not sure, click the **Save Report** button to save the change report, then click **Cancel**.</span></span> <span data-ttu-id="ff70b-215">分析報表、規劃如何在升級完成之後傳送任何必要的物件和資料，然後重新啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="ff70b-215">Analyze the report, plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="ff70b-216">**儲存報表** - 按一下此按鈕，可儲存精靈在資料庫內的物件與其在 DAC 定義內的對應物件之間偵測到之變更的報表。</span><span class="sxs-lookup"><span data-stu-id="ff70b-216">**Save Report** - Click the button to save a report of the changes the wizard detected between the objects in the database and their counterparts in the DAC definition.</span></span> <span data-ttu-id="ff70b-217">然後您可以檢閱報表，以決定升級完成之後是否需要採取動作，將報表中列出的某些物件或所有物件併入新的資料庫內。</span><span class="sxs-lookup"><span data-stu-id="ff70b-217">You can then review the report to determine if you need to take actions after the upgrade completes to incorporate some or all of the objects listed in the report into the new database.</span></span>  
  
 <span data-ttu-id="ff70b-218">\*\* \< 上一步**-回到 [**選取 DAC 封裝\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-218">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="ff70b-219">**下一步 >** - 繼續進行 [選項]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-219">**Next >** - Proceeds to the **Options** page.</span></span>  
  
 <span data-ttu-id="ff70b-220">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-220">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
## <a name="options-page"></a><span data-ttu-id="ff70b-221">選項頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-221">Options Page</span></span>  
 <span data-ttu-id="ff70b-222">您可以使用此頁面針對升級選取失敗時回復選項。</span><span class="sxs-lookup"><span data-stu-id="ff70b-222">Use this page to select the rollback on failure option for the upgrade.</span></span>  
  
 <span data-ttu-id="ff70b-223">**失敗時回復** - 選取此選項，可將升級併入精靈在發生錯誤時嘗試回復的交易。</span><span class="sxs-lookup"><span data-stu-id="ff70b-223">**Rollback on failure** - Select this option to enclose the upgrade in a transaction which the wizard can attempt to roll back if errors occur.</span></span> <span data-ttu-id="ff70b-224">如需有關此選項的詳細資訊，請參閱＜ [選擇 DAC 升級選項](#ChoseDACUpgOptions)＞。</span><span class="sxs-lookup"><span data-stu-id="ff70b-224">For more information about the option, see [Choosing DAC Upgrade Options](#ChoseDACUpgOptions).</span></span>  
  
 <span data-ttu-id="ff70b-225">**還原預設值** - 將此選項還原為其預設值 false。</span><span class="sxs-lookup"><span data-stu-id="ff70b-225">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="ff70b-226">\*\* \< 上一步**-回到 [偵測**變更\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-226">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="ff70b-227">**下一步 >** - 繼續進行 [檢閱升級計畫]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-227">**Next >** - Proceeds to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="ff70b-228">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-228">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-the-upgrade-plan-page"></a><a name="ReviewUpgPlan"></a> <span data-ttu-id="ff70b-229">檢閱升級計畫頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-229">Review the Upgrade Plan Page</span></span>  
 <span data-ttu-id="ff70b-230">您可以使用此頁面檢閱升級程序所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ff70b-230">Use this page to do review the actions that will be taken by the upgrade process.</span></span> <span data-ttu-id="ff70b-231">只有當您確定升級不會產生問題時，才應該繼續進行。</span><span class="sxs-lookup"><span data-stu-id="ff70b-231">Only proceed when you are confident the upgrade will not create problems.</span></span>  
  
 <span data-ttu-id="ff70b-232">**將使用以下動作升級 DAC。**</span><span class="sxs-lookup"><span data-stu-id="ff70b-232">**The following actions will be used to upgrade the DAC.**</span></span> <span data-ttu-id="ff70b-233">- 檢閱顯示的資訊，以確保採取的動作將會是正確的。</span><span class="sxs-lookup"><span data-stu-id="ff70b-233">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="ff70b-234">[動作]  欄會顯示針對升級所執行的動作，例如 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ff70b-234">The **Action** column displays the actions, such as Transact-SQL statements, that will be run to perform the upgrade.</span></span> <span data-ttu-id="ff70b-235">如果相關聯的動作可能會刪除資料， **[資料遺失]** 欄就會包含警告。</span><span class="sxs-lookup"><span data-stu-id="ff70b-235">The **Data Loss** column will contain a warning if the associated action could delete data.</span></span>  
  
 <span data-ttu-id="ff70b-236">**重新整理** - 重新整理動作清單。</span><span class="sxs-lookup"><span data-stu-id="ff70b-236">**Refresh** - refreshes the action list.</span></span>  
  
 <span data-ttu-id="ff70b-237">**儲存動作報表** - 將動作視窗的內容儲存至 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff70b-237">**Save Action Report** - saves the contents of the action window to an HTML file.</span></span>  
  
 <span data-ttu-id="ff70b-238">**儘管變更可能遺失，還是繼續進行** - 指定您了解目前資料庫中的某些物件或資料將不會出現在新的資料庫中，但是您仍然願意繼續升級。</span><span class="sxs-lookup"><span data-stu-id="ff70b-238">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="ff70b-239">只有當您已經分析變更報表，並了解手動傳送新資料庫中所需之任何物件或資料所必須執行的步驟時，才應該選取這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="ff70b-239">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="ff70b-240">如果您不確定，請按一下 [儲存動作報告]  按鈕儲存變更報表並按一下 [儲存指令碼]  按鈕儲存 Transact-SQL 指令碼，然後按一下 [取消]  。</span><span class="sxs-lookup"><span data-stu-id="ff70b-240">If you are not sure, click the **Save Action Report** button to save the change report and the **Save Scripts** button to save the Transact-SQL script, then click **Cancel**.</span></span> <span data-ttu-id="ff70b-241">分析報表和指令碼、規劃如何在升級完成之後傳送任何必要的物件和資料，然後重新啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="ff70b-241">Analyze the report and script, and then plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="ff70b-242">**儲存指令碼** - 將用來執行升級的 Transact-SQL 陳述式儲存至文字檔。</span><span class="sxs-lookup"><span data-stu-id="ff70b-242">**Save Scripts** - saves the Transact-SQL statements that will be used to perform the upgrade to a text file.</span></span>  
  
 <span data-ttu-id="ff70b-243">**還原預設值** - 將此選項還原為其預設值 false。</span><span class="sxs-lookup"><span data-stu-id="ff70b-243">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="ff70b-244">\*\* \< 上一步**-回到 [偵測**變更\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-244">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="ff70b-245">**下一步 >** - 繼續進行 [摘要]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-245">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="ff70b-246">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-246">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="ff70b-247">摘要頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-247">Summary Page</span></span>  
 <span data-ttu-id="ff70b-248">您可以使用此頁面針對精靈在升級 DAC 時所採取動作進行最終檢閱。</span><span class="sxs-lookup"><span data-stu-id="ff70b-248">Use this page to do a final review of the actions the wizard will take when upgrading the DAC.</span></span>  
  
 <span data-ttu-id="ff70b-249">**將使用以下設定升級您的 DAC**</span><span class="sxs-lookup"><span data-stu-id="ff70b-249">**The following settings will be used to upgrade your DAC.**</span></span> <span data-ttu-id="ff70b-250">- 檢閱顯示的資訊，以確保採取的動作將會是正確的。</span><span class="sxs-lookup"><span data-stu-id="ff70b-250">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="ff70b-251">此視窗會顯示您選取要進行升級的 DAC，以及包含新版 DAC 的 DAC 封裝。</span><span class="sxs-lookup"><span data-stu-id="ff70b-251">The window displays the DAC you selected to be upgraded, and the DAC package containing the new version of the DAC.</span></span> <span data-ttu-id="ff70b-252">此視窗也會顯示目前的資料庫版本是否與目前的 DAC 定義相同，或資料庫是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="ff70b-252">The window also displays whether the current version of the database is the same as the current DAC definition, or if the database has changed.</span></span>  
  
 <span data-ttu-id="ff70b-253">\*\* \< 上一步**-返回 [**審核升級計畫\*\*] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff70b-253">**\< Previous** - Returns you to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="ff70b-254">**下一步 >** - 部署 DAC，並在 [升級 DAC]  頁面中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="ff70b-254">**Next >** - Deploys the DAC and displays the results in the **Upgrade DAC** page.</span></span>  
  
 <span data-ttu-id="ff70b-255">**取消** - 結束精靈，不部署 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-255">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="upgrade-dac-page"></a><a name="Upgrade"></a> <span data-ttu-id="ff70b-256">升級 DAC 頁面</span><span class="sxs-lookup"><span data-stu-id="ff70b-256">Upgrade DAC Page</span></span>  
 <span data-ttu-id="ff70b-257">此頁面會報告升級作業成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ff70b-257">This page reports the success or failure of the upgrade operation.</span></span>  
  
 <span data-ttu-id="ff70b-258">**正在升級 DAC** - 報告為了升級 DAC 所採取的每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ff70b-258">**Upgrading the DAC** - Reports the success or failure of each action taken to upgrade the DAC.</span></span> <span data-ttu-id="ff70b-259">檢閱資訊以判斷每個動作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="ff70b-259">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="ff70b-260">發生錯誤的所有動作在 **[結果]** 資料行中都會有一個連結。</span><span class="sxs-lookup"><span data-stu-id="ff70b-260">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="ff70b-261">選取連結來檢視該動作的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="ff70b-261">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="ff70b-262">**儲存報表** - 選取此按鈕可將升級報表儲存到 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ff70b-262">**Save Report** - Select this button to save the upgrade report to an HTML file.</span></span> <span data-ttu-id="ff70b-263">此檔案會報告每個動作的狀態，包括所有動作所產生的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ff70b-263">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="ff70b-264">預設資料夾為 Windows 帳戶之文件資料夾中的 SQL Server Management Studio\DAC Packages 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff70b-264">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="ff70b-265">**完成** - 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="ff70b-265">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="UpgradeDACPowerShell"></a> <span data-ttu-id="ff70b-266">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff70b-266">Using PowerShell</span></span>  
 <span data-ttu-id="ff70b-267">**在 PowerShell 指令碼中使用 IncrementalUpgrade() 方法升級 DAC**</span><span class="sxs-lookup"><span data-stu-id="ff70b-267">**To upgrade a DAC using the IncrementalUpgrade() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="ff70b-268">建立 SMO Server 物件，並將它設為包含要升級之 DAC 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff70b-268">Create a SMO Server object and set it to the instance that contains the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="ff70b-269">開啟 `ServerConnection` 物件，並連接到相同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ff70b-269">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="ff70b-270">使用 `System.IO.File` 以載入 DAC 封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="ff70b-270">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="ff70b-271">使用 `add_DacActionStarted` 和 `add_DacActionFinished` 訂閱 DAC 升級事件。</span><span class="sxs-lookup"><span data-stu-id="ff70b-271">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
5.  <span data-ttu-id="ff70b-272">設定 `DacUpgradeOptions`。</span><span class="sxs-lookup"><span data-stu-id="ff70b-272">Set the `DacUpgradeOptions`.</span></span>  
  
6.  <span data-ttu-id="ff70b-273">您可以使用 `IncrementalUpgrade` 方法來升級 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-273">Use the `IncrementalUpgrade` method to upgrade the DAC.</span></span>  
  
7.  <span data-ttu-id="ff70b-274">關閉用來讀取 DAC 封裝檔案的檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="ff70b-274">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="ff70b-275">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ff70b-275">Example (PowerShell)</span></span>  
 <span data-ttu-id="ff70b-276">下列範例使用 MyApplicationVNext.dacpac 封裝中的新 DAC 版本來升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)]預設執行個體上名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="ff70b-276">The following example upgrades a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a new DAC version in a MyApplicationVNext.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC upgrade events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Upgrade the DAC and close the package.  
$dacName  = "MyApplication"  
  
## Set the upgrade options.  
$upgradeProperties = New-Object Microsoft.SqlServer.Management.Dac.DacUpgradeOptions  
$upgradeProperties.blockonchanges = $true  
$upgradeProperties.ignoredataloss = $false  
$upgradeProperties.rollbackonfailure = $true  
$ upgradeProperties.skippolicyvalidation = $false  
  
## Upgrade the DAC  
$dacstore.IncrementalUpgrade($dacName, $dacType, $upgradeProperties)  
## Close the package file.  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff70b-277">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff70b-277">See Also</span></span>  
 <span data-ttu-id="ff70b-278">[資料層應用程式](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ff70b-278">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="ff70b-279">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff70b-279">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)  
