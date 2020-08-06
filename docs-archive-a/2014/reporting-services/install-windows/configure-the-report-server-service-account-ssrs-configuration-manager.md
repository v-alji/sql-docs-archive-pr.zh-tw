---
title: 設定報表伺服器服務帳戶 (SSRS 設定管理員) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: ''
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: b860a9c916f7dd9c1bdef4f5218845c66239ebe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687521"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a><span data-ttu-id="bda3d-102">設定報表伺服器服務帳戶 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="bda3d-102">Configure the Report Server Service Account (SSRS Configuration Manager)</span></span>

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="bda3d-103">會實作成單一服務，其中包含報表伺服器 Web 服務、報表管理員，以及用於排程報表處理和訂閱傳遞的背景處理應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda3d-103">is implemented as a single service that contains a Report Server Web service, Report Manager, and a background processing application that is used for scheduled report processing and subscription delivery.</span></span> <span data-ttu-id="bda3d-104">本主題將說明如何在一開始設定服務帳戶，以及如何使用 Reporting Services 組態工具來修改此帳戶或密碼。</span><span class="sxs-lookup"><span data-stu-id="bda3d-104">This topic explains how the service account is initially configured and how to modify the account or password using the Reporting Services Configuration tool.</span></span>  
  
## <a name="initial-configuration"></a><span data-ttu-id="bda3d-105">初始組態</span><span class="sxs-lookup"><span data-stu-id="bda3d-105">Initial Configuration</span></span>

 <span data-ttu-id="bda3d-106">報表伺服器服務帳戶是在安裝期間所定義。</span><span class="sxs-lookup"><span data-stu-id="bda3d-106">The Report Server service account is defined during Setup.</span></span> <span data-ttu-id="bda3d-107">您可以在網域使用者帳戶或內建帳戶 (如 `NetworkService` 帳戶) 之下執行此服務。</span><span class="sxs-lookup"><span data-stu-id="bda3d-107">You can run the service under a domain user account or a built-in such as `NetworkService` account.</span></span> <span data-ttu-id="bda3d-108">沒有預設帳戶;您在安裝精靈的 [[伺服器設定-服務帳戶](../../sql-server/install/server-configuration-service-accounts.md)] 頁面中指定的任何帳戶都會成為報表伺服器服務的初始帳戶。</span><span class="sxs-lookup"><span data-stu-id="bda3d-108">There is no default account; whatever account you specify in the [Server Configuration - Service Accounts](../../sql-server/install/server-configuration-service-accounts.md) page of the Installation Wizard becomes the initial account of the Report Server service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bda3d-109">雖然報表伺服器 Web 服務和報表管理員為 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 應用程式，但是它們不會在 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="bda3d-109">Although the Report Server Web service and Report Manager are [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications, they do not run under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] account.</span></span> <span data-ttu-id="bda3d-110">單一服務架構會在相同的報表伺服器處理序識別內執行這兩個 ASP.NET 應用程式，</span><span class="sxs-lookup"><span data-stu-id="bda3d-110">The single service architecture runs both ASP.NET applications within the same Report Server process identity.</span></span> <span data-ttu-id="bda3d-111">這是與舊版不同的重大變更，在舊版中，報表伺服器 Web 服務和報表管理員都是在 IIS 內指定的 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 工作處理序識別內執行。</span><span class="sxs-lookup"><span data-stu-id="bda3d-111">This is an important change from previous releases, where both the Report Server Web service and Report Manager ran under the [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] worker process identity specified in IIS.</span></span>
  
## <a name="changing-the-service-account"></a><span data-ttu-id="bda3d-112">變更服務帳戶</span><span class="sxs-lookup"><span data-stu-id="bda3d-112">Changing the Service Account</span></span>

 <span data-ttu-id="bda3d-113">若要檢視及重新設定服務帳戶資訊，請務必使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具。</span><span class="sxs-lookup"><span data-stu-id="bda3d-113">To view and reconfigure service account information, always use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span> <span data-ttu-id="bda3d-114">服務識別資訊會儲存在內部的多個位置。</span><span class="sxs-lookup"><span data-stu-id="bda3d-114">Service identity information is stored internally in multiple locations.</span></span> <span data-ttu-id="bda3d-115">使用此工具可確保每當您變更帳戶或密碼時，所有的參考也會隨著更新。</span><span class="sxs-lookup"><span data-stu-id="bda3d-115">Using the tool ensures that all references are updated accordingly whenever you change the account or password.</span></span> <span data-ttu-id="bda3d-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具會執行下列其他步驟，以確保報表伺服器保持可用：</span><span class="sxs-lookup"><span data-stu-id="bda3d-116">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool performs the following additional steps to ensure the report server remains available:</span></span>  
  
- <span data-ttu-id="bda3d-117">自動將新帳戶加入本機電腦上所建立的報表伺服器群組中。</span><span class="sxs-lookup"><span data-stu-id="bda3d-117">Automatically adds the new account to the report server group created on the local computer.</span></span> <span data-ttu-id="bda3d-118">此群組是在保護 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 檔案安全的存取控制清單 (ACL) 中指定。</span><span class="sxs-lookup"><span data-stu-id="bda3d-118">This group is specified in the access control lists (ACLs) that secure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] files.</span></span>  
  
- <span data-ttu-id="bda3d-119">自動更新用來裝載報表伺服器資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體登入權限。</span><span class="sxs-lookup"><span data-stu-id="bda3d-119">Automatically updates the login permissions on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database.</span></span> <span data-ttu-id="bda3d-120">新的帳戶會加入至 **RSExecRole**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-120">The new account will be added to the **RSExecRole**.</span></span>  
  
     <span data-ttu-id="bda3d-121">舊帳戶的資料庫登入將不會自動移除。</span><span class="sxs-lookup"><span data-stu-id="bda3d-121">The database login for the old account will not be removed automatically.</span></span> <span data-ttu-id="bda3d-122">請務必移除不再使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="bda3d-122">Be sure to remove accounts that are no longer in use.</span></span> <span data-ttu-id="bda3d-123">如需詳細資訊，請參閱《SQL Server 線上叢書》中的[管理報表伺服器資料庫 &#40;SSRS 原生模式&#41;](../report-server/report-server-database-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-123">For more information, see [Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) in SQL Server Books Online.</span></span>  
  
     <span data-ttu-id="bda3d-124">只有在一開始設定報表伺服器資料庫連接使用新的服務帳戶，才能將資料庫權限授與給這個服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="bda3d-124">Granting database permissions to new service account only occurs if you configured the report server database connection to use the service account in the first place.</span></span> <span data-ttu-id="bda3d-125">如果您設定報表伺服器資料庫連接使用網域使用者帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫登入，則連接資訊將不會受到服務帳戶更新的影響。</span><span class="sxs-lookup"><span data-stu-id="bda3d-125">If you configured the report server database connection to use a domain user account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database login, the connection information is not affected by the service account update.</span></span>  
  
- <span data-ttu-id="bda3d-126">自動更新加密金鑰，加入新帳戶的設定檔資訊。</span><span class="sxs-lookup"><span data-stu-id="bda3d-126">Automatically updates the encryption key to include the profile information of the new account.</span></span>  
  
    > [!NOTE]  
    > <span data-ttu-id="bda3d-127">如果報表伺服器是向外延展部署的一部分，則只有您更新的報表伺服器會受到影響。</span><span class="sxs-lookup"><span data-stu-id="bda3d-127">If the report server is part of the scale-out deployment, only the report server that you are updating is affected.</span></span> <span data-ttu-id="bda3d-128">部署中其他報表伺服器的加密金鑰，不會受到服務帳戶變更的影響。</span><span class="sxs-lookup"><span data-stu-id="bda3d-128">The encryption keys for other report servers in the deployment are unaffected by the service account change.</span></span>  
  
 <span data-ttu-id="bda3d-129">如需如何設定帳戶的指示，請參閱[Configure a Service account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-129">For instructions on how to set the account, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
## <a name="choosing-an-account"></a><span data-ttu-id="bda3d-130">選擇帳戶</span><span class="sxs-lookup"><span data-stu-id="bda3d-130">Choosing an Account</span></span>

 <span data-ttu-id="bda3d-131">您可以將報表伺服器服務設定為在以下任何一種帳戶類型下執行：</span><span class="sxs-lookup"><span data-stu-id="bda3d-131">You can configure the Report Server service to run under any of these account types:</span></span>  
  
- <span data-ttu-id="bda3d-132">最低權限的 Windows 使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="bda3d-132">Least-privileged Windows user account</span></span>  
  
- <span data-ttu-id="bda3d-133">NetworkService</span><span class="sxs-lookup"><span data-stu-id="bda3d-133">NetworkService</span></span>  
  
- <span data-ttu-id="bda3d-134">LocalSystem</span><span class="sxs-lookup"><span data-stu-id="bda3d-134">LocalSystem</span></span>  
  
- <span data-ttu-id="bda3d-135">LocalService</span><span class="sxs-lookup"><span data-stu-id="bda3d-135">LocalService</span></span>  
  
 <span data-ttu-id="bda3d-136">在選擇帳戶類型時，並沒有單一的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="bda3d-136">There is no single best approach for choosing an account type.</span></span> <span data-ttu-id="bda3d-137">每個帳戶都有您必須考量的優點和缺點。</span><span class="sxs-lookup"><span data-stu-id="bda3d-137">Each account has advantages and disadvantages that you must consider.</span></span> <span data-ttu-id="bda3d-138">如果要在實際伺服器上部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，最佳做法建議您設定此服務在網域使用者帳戶下執行，好讓您可以在惡意使用者危害共用帳戶時，避免損害擴大。</span><span class="sxs-lookup"><span data-stu-id="bda3d-138">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a production server, best practices suggest that you configure the service to run under a domain user account so that you can avoid widespread damage if a shared account is compromised by a malicious user.</span></span> <span data-ttu-id="bda3d-139">此外，您也可以更輕鬆地為此帳戶稽核登入活動。</span><span class="sxs-lookup"><span data-stu-id="bda3d-139">It also makes it easier to audit the logon activity for this account.</span></span> <span data-ttu-id="bda3d-140">在以下狀況中，您要考慮使用 Windows 使用者帳戶的取捨：如果您在使用 Kerberos 驗證的網路中部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，您就必須使用此使用者帳戶註冊服務。</span><span class="sxs-lookup"><span data-stu-id="bda3d-140">A trade-off to using a Windows user account is that if you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses Kerberos authentication, you must register the service with the user account.</span></span> <span data-ttu-id="bda3d-141">如需詳細資訊，請參閱[為報表伺服器註冊服務主體名稱 &#40;SPN&#41;](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-141">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
 <span data-ttu-id="bda3d-142">本節中的下列指導方針和連結可以協助您決定最適合用於您的部署的方法。</span><span class="sxs-lookup"><span data-stu-id="bda3d-142">The following guidelines and links in this section can help you decide on an approach that is best for your deployment.</span></span>  
  
- <span data-ttu-id="bda3d-143">[服務帳戶 &#40;SSRS 原生模式&#41;](../../sql-server/install/service-account-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-143">[Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md).</span></span>  
  
- <span data-ttu-id="bda3d-144">《SQL Server 線上叢書》中的[設定 Windows 服務帳戶與權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) 。</span><span class="sxs-lookup"><span data-stu-id="bda3d-144">[Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) in SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="bda3d-145">[The Services and Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733) (服務和服務帳戶安全性規劃指南)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-145">[The Services and Service Accounts Security Planning Guide](http://usergroup.doubletake.com/file_cabinet/download/0x000021733).</span></span>  
  
## <a name="updating-an-expired-password"></a><span data-ttu-id="bda3d-146">更新已過期的密碼</span><span class="sxs-lookup"><span data-stu-id="bda3d-146">Updating an Expired Password</span></span>

 <span data-ttu-id="bda3d-147">如果報表伺服器服務是以網域帳戶執行，而且在您可以於 Reporting Services 組態工具內更新密碼以前，密碼就已經過期，則要先指定新的密碼，才能啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="bda3d-147">If the Report Server service runs under a domain account and the password expires before you can update it in the Reporting Services Configuration tool, the service will not start until you specify a new password.</span></span> <span data-ttu-id="bda3d-148">如果此服務無法啟動，您就無法使用 Reporting Services 組態工具連接該伺服器來更新帳戶。</span><span class="sxs-lookup"><span data-stu-id="bda3d-148">If the service cannot be started, you cannot use the Reporting Services Configuration tool to connect to that server to update the account.</span></span> <span data-ttu-id="bda3d-149">在此情況下，您必須使用一些工具的組合，才能讓伺服器重新在線上工作。</span><span class="sxs-lookup"><span data-stu-id="bda3d-149">In this case, you must use a combination of tools to bring the server back online.</span></span>  
  
 <span data-ttu-id="bda3d-150">若要重設密碼，請執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="bda3d-150">To reset the password, do the following:</span></span>  
  
1. <span data-ttu-id="bda3d-151">在 **[開始]** 功能表上，依序指向 **[控制台]**、 **[系統管理工具]**，再按一下 **[服務]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-151">On the **Start** menu, point to **Control Panel**, point to **Administrator Tools**, and click **Services**.</span></span>  
  
2. <span data-ttu-id="bda3d-152">以滑鼠右鍵按一下 **[SQL Server Reporting Services]**，然後選取 **[內容]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-152">Right-click **SQL Server Reporting Services**, select **Properties**.</span></span>  
  
3. <span data-ttu-id="bda3d-153">按一下 **[登入]**，並輸入新的密碼。</span><span class="sxs-lookup"><span data-stu-id="bda3d-153">Click **Log On**, and type the new password.</span></span>  
  
4. <span data-ttu-id="bda3d-154">在更新密碼之後，請啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並在 [服務帳戶] 頁面中更新密碼。</span><span class="sxs-lookup"><span data-stu-id="bda3d-154">After you update the password, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and update the password in the Service Account page.</span></span> <span data-ttu-id="bda3d-155">對於更新報表伺服器儲存於內部的帳戶資訊而言，這個額外步驟是必要的。</span><span class="sxs-lookup"><span data-stu-id="bda3d-155">This additional step is necessary to update the account information that is stored internally by the report server.</span></span>  
  
 <span data-ttu-id="bda3d-156">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務帳戶密碼已過期，則當您嘗試連接至報表伺服器時便會發生 `rsReportServerDatabaseUnavailable` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="bda3d-156">If the service account password for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] expires, the `rsReportServerDatabaseUnavailable` error occurs when you try to connect to the report server.</span></span> <span data-ttu-id="bda3d-157">重設密碼即可解決此錯誤。</span><span class="sxs-lookup"><span data-stu-id="bda3d-157">Resetting the password resolves this error.</span></span>  
  
## <a name="configuring-the-report-server-service-for-a-sharepoint-integrated-report-server"></a><span data-ttu-id="bda3d-158">為 SharePoint 整合報表伺服器設定報表伺服器服務</span><span class="sxs-lookup"><span data-stu-id="bda3d-158">Configuring the Report Server Service for a SharePoint Integrated Report Server</span></span>

 <span data-ttu-id="bda3d-159">如果您是以 SharePoint 整合模式執行報表伺服器，當下列其中一個條件成立時，您必須更新儲存於 SharePoint 組態資料庫中的服務帳戶資訊：</span><span class="sxs-lookup"><span data-stu-id="bda3d-159">If you are running a report server in SharePoint integrated mode, you must update the service account information that is stored in the SharePoint configuration database if either of the following conditions are true:</span></span>  
  
- <span data-ttu-id="bda3d-160">修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務帳戶 (例如，從 NetworkService 切換到網域使用者帳戶)。</span><span class="sxs-lookup"><span data-stu-id="bda3d-160">Modifying the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account (for example, switching from NetworkService to a domain user account).</span></span>  
  
- <span data-ttu-id="bda3d-161">擴充 SharePoint 伺服陣列，使其包含其他 SharePoint Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda3d-161">Extending a SharePoint farm to include an additional SharePoint Web application.</span></span> <span data-ttu-id="bda3d-162">如果設定伺服器陣列進行報表伺服器整合，而且新加入的應用程式所設定要執行的使用者帳戶，與伺服器陣列中的其他應用程式不同，您就必須更新資料庫存取資訊。</span><span class="sxs-lookup"><span data-stu-id="bda3d-162">If the server farm is configured for report server integration, and newly added application is configured to run under a different user account than other applications in the farm, you must update the database access information.</span></span>  
  
 <span data-ttu-id="bda3d-163">在重設資料庫存取資訊之後，您應該要重新啟動 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 服務，以確保不再使用舊的連接。</span><span class="sxs-lookup"><span data-stu-id="bda3d-163">After you reset the database access information, you should then restart the [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] service to ensure that the old connection is no longer used.</span></span>  
  
1. <span data-ttu-id="bda3d-164">在 **[系統管理工具]** 中，按一下 **[SharePoint 2010 管理中心]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-164">In **Administrative Tools**, click **SharePoint 2010 Central Administration**.</span></span>  
  
2. <span data-ttu-id="bda3d-165">按一下 **[應用程式管理]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-165">Click **Application Management**.</span></span>  
  
3. <span data-ttu-id="bda3d-166">在 [Reporting Services] 區段中按一下 **[授與資料庫存取權]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-166">In the Reporting Services section, click **Grant Database Access**.</span></span>  
  
4. <span data-ttu-id="bda3d-167">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bda3d-167">Click **OK**.</span></span> <span data-ttu-id="bda3d-168">[輸入認證] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="bda3d-168">The Enter Credentials dialog box appears.</span></span>  
  
5. <span data-ttu-id="bda3d-169">輸入使用者屬於裝載報表伺服器之電腦上的本機系統管理員群組成員的認證。</span><span class="sxs-lookup"><span data-stu-id="bda3d-169">Enter the credentials of a user who is a member of the Local Administrator's group on the computer that hosts the report server.</span></span> <span data-ttu-id="bda3d-170">這些認證將針對擷取服務帳戶資訊的目的，用於報表伺服器電腦的一次連接。</span><span class="sxs-lookup"><span data-stu-id="bda3d-170">The credentials will be used for a one-time connection to the report server computer for the purpose of retrieving service account information.</span></span> <span data-ttu-id="bda3d-171">為每個服務帳戶所建立的資料庫登入將會在 SharePoint 資料庫中更新。</span><span class="sxs-lookup"><span data-stu-id="bda3d-171">The database login that is created for each service account will be updated in SharePoint databases.</span></span>  
  
6. <span data-ttu-id="bda3d-172">若要重新啟動此服務，請按一下 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-172">To restart the service, click **Operations**.</span></span>  
  
7. <span data-ttu-id="bda3d-173">在 [拓撲與服務] 中，按一下 **[伺服器上的服務]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-173">In Topology and Services, click **Services on Server**.</span></span>  
  
8. <span data-ttu-id="bda3d-174">如果是 Windows SharePoint Services Web 應用程式，請按一下 **[停止]**。</span><span class="sxs-lookup"><span data-stu-id="bda3d-174">For Windows SharePoint Services Web Application, click **Stop**.</span></span>  
  
9. <span data-ttu-id="bda3d-175">等候此服務停止。</span><span class="sxs-lookup"><span data-stu-id="bda3d-175">Wait for the service stop.</span></span>  
  
10. <span data-ttu-id="bda3d-176">按一下 [啟動]。</span><span class="sxs-lookup"><span data-stu-id="bda3d-176">Click **Start**.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="bda3d-177">SharePoint 產品與技術需要網域帳戶來處理類似 Reporting Services SharePoint 模式的服務組態。</span><span class="sxs-lookup"><span data-stu-id="bda3d-177">SharePoint products and technologies require domain accounts for service configuration like reporting services SharePoint mode.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bda3d-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bda3d-178">Next Steps</span></span>

 <span data-ttu-id="bda3d-179">[設定服務帳戶 &#40;ssrs Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [服務帳戶 &#40;Ssrs 原生模式&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [設定報表伺服器 url &#40;Ssrs Configuration Manager](configure-report-server-urls-ssrs-configuration-manager.md)&#41;Reporting Services 組態管理員 &#40;[原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="bda3d-179">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) [Service Account &#40;SSRS Native Mode&#41;](../../sql-server/install/service-account-ssrs-native-mode.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span></span>
