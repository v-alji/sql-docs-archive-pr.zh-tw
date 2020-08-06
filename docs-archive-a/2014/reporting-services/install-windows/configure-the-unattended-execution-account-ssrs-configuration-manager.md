---
title: 設定自動執行帳戶 (SSRS 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- security [Reporting Services], unattended report processing
- unattended report processing [Reporting Services]
- credentials [Reporting Services]
- external data sources [Reporting Services]
- accounts [Reporting Services]
- reports [Reporting Services], processing
ms.assetid: 4e50733e-bd8c-4bf6-8379-98b1531bb9ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 437b28b57bc304d079acea3123983bed389341ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700852"
---
# <a name="configure-the-unattended-execution-account-ssrs-configuration-manager"></a><span data-ttu-id="0cfd9-102">設定自動執行帳戶 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="0cfd9-102">Configure the Unattended Execution Account (SSRS Configuration Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0cfd9-103">提供了一個特殊帳戶，它是用於自動報表處理和透過網路傳送連接要求。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-103">provides a special account that is used for unattended report processing and for sending connection requests across the network.</span></span> <span data-ttu-id="0cfd9-104">以下是使用此帳戶的方式：</span><span class="sxs-lookup"><span data-stu-id="0cfd9-104">The account is used in the following ways:</span></span>  
  
-   <span data-ttu-id="0cfd9-105">透過網路針對使用資料庫驗證的報表傳送連接要求，或是連接到不需要或不使用驗證的外部報表資料來源。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-105">Send connection requests over the network for reports that use database authentication, or connect to external report data sources that do not require or use authentication.</span></span> <span data-ttu-id="0cfd9-106">如需詳細資訊，請參閱《SQL Server 線上叢書》中的 [指定報表資料來源的認證和連接資訊](../../integration-services/connection-manager/data-sources.md) 。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-106">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in SQL Server Books Online.</span></span>  
  
-   <span data-ttu-id="0cfd9-107">擷取報表中使用的外部影像檔。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-107">Retrieve external image files that are used in report.</span></span> <span data-ttu-id="0cfd9-108">如果想要使用影像檔而該檔案無法透過匿名存取來存取，則您可以設定自動報表處理帳戶，並授與該帳戶存取檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-108">If you want to use an image file and the file cannot be accessed through Anonymous access, you can configure the unattended report processing account and grant the account permission to access the file.</span></span>  
  
 <span data-ttu-id="0cfd9-109">自動報表處理是指由事件觸發 (不論是排程驅動事件或資料重新整理事件)，而非由使用者要求觸發的任何報表執行處理。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-109">Unattended report processing refers to any report execution process that is triggered by an event (either a schedule-driven event or data refresh event) rather than a user request.</span></span> <span data-ttu-id="0cfd9-110">報表伺服器使用自動報表處理帳戶，來登入主控外部資料來源的電腦。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-110">The report server uses the unattended report processing account to log on to the computer that hosts the external data source.</span></span> <span data-ttu-id="0cfd9-111">因為報表伺服器服務帳戶的認證絕不會用來連接到其他電腦，所以需要此帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-111">This account is necessary because the credentials of the Report Server service account are never used to connect to other computers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0cfd9-112">設定此帳戶是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-112">Configuring the account is optional.</span></span> <span data-ttu-id="0cfd9-113">不過，如果沒有加以設定，您就可能無法連接到某些資料來源，而且可能無法從遠端電腦擷取影像檔。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-113">However, if you do not configure it, you will limit your options for connecting to some data sources, and you might not be able to retrieve image files from remote computers.</span></span> <span data-ttu-id="0cfd9-114">如果您真的設定帳戶，就必須讓它保持最新狀態。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-114">If you do configure the account, you must keep it up to date.</span></span> <span data-ttu-id="0cfd9-115">特別是如果您讓密碼過期或者 Active Directory 中的帳戶資訊變更，則下次在處理報表時，您將遇到下列的錯誤訊息：「登入失敗 (rsLogonFailed) 登入失敗：未知的使用者名稱或密碼錯誤。」</span><span class="sxs-lookup"><span data-stu-id="0cfd9-115">Specifically, if you allow a password to expire or the account information is changed in Active Directory, you will encounter the following error the next time a report is processed: "Logon failed (rsLogonFailed) Logon failure: unknown user name or bad password."</span></span> <span data-ttu-id="0cfd9-116">正確維護自動報表處理帳戶是很重要的，即使您從未擷取外部影像或傳送對外部電腦的連接要求也是如此。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-116">Proper maintenance of the unattended report processing account is essential, even if you never retrieve external images or send connection requests to external computers.</span></span> <span data-ttu-id="0cfd9-117">如果在設定帳戶之後發現並未使用該帳戶，可以將其刪除，這樣就不需經常進行帳戶維護工作。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-117">If you configure the account but then find that you are not using it, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
## <a name="how-to-configure-the-account"></a><span data-ttu-id="0cfd9-118">如何設定帳戶</span><span class="sxs-lookup"><span data-stu-id="0cfd9-118">How to Configure the Account</span></span>  
 <span data-ttu-id="0cfd9-119">您必須使用網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-119">You must use a domain user account.</span></span> <span data-ttu-id="0cfd9-120">為了提供原先預期的用途，此帳戶應該與用來執行報表伺服器服務的帳戶不同。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-120">To serve its intended purpose, this account should be different than the one used to run the Report Server service.</span></span> <span data-ttu-id="0cfd9-121">請務必使用符合下列條件的帳戶：擁有最小權限 (具有網路連接的唯讀存取權限就足夠)，而且僅擁有提供資料來源和資源給報表伺服器之電腦的有限存取權。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-121">Be sure to use an account that has minimum permissions (read-only access with network connection permissions is sufficient) and limited access to just those computers that provide data sources and resources to the report server.</span></span> <span data-ttu-id="0cfd9-122">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-122">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
 <span data-ttu-id="0cfd9-123">若要指定此帳戶，您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具或 **rsconfig** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-123">To specify the account, you can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool or the **rsconfig** utility.</span></span> <span data-ttu-id="0cfd9-124">設定自動執行帳戶的最簡單方法，是執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並在 [執行帳戶] 頁面中指定認證。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-124">The easiest way to configure the unattended execution account is to run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and specify credentials in the Execution Account page.</span></span>  
  
1.  <span data-ttu-id="0cfd9-125">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-125">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span> <span data-ttu-id="0cfd9-126">如需指示，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-126">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="0cfd9-127">在 [執行帳戶] 頁面上，選取 [指定執行帳戶]  。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-127">On the Execution Account page, select **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="0cfd9-128">鍵入帳戶和密碼，重新鍵入密碼，然後按一下 [套用]  。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-128">Type the account and password, retype the password, and then click **Apply**.</span></span>  
  
### <a name="using-rsconfig-utility"></a><span data-ttu-id="0cfd9-129">使用 RSCONFIG 公用程式</span><span class="sxs-lookup"><span data-stu-id="0cfd9-129">Using RSCONFIG Utility</span></span>  
 <span data-ttu-id="0cfd9-130">設定此帳戶的另一個方法是使用 **rsconfig** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-130">Another way to set the account is to use the **rsconfig** utility.</span></span> <span data-ttu-id="0cfd9-131">若要指定帳戶，請使用 **rsconfig** 的 **-e**引數。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-131">To specify the account, use the **-e** argument of **rsconfig**.</span></span> <span data-ttu-id="0cfd9-132">指定 **rsconfig** 的 **-e** 引數，會引導公用程式將帳戶資訊寫入組態檔。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-132">Specifying the **-e** argument for **rsconfig** directs the utility to write the account information to the configuration file.</span></span> <span data-ttu-id="0cfd9-133">您不需要指定 RSreportserver.config 的路徑。請遵循這些步驟來設定帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-133">You do not need to specify a path to RSreportserver.config. Follow these steps to configure the account.</span></span>  
  
1.  <span data-ttu-id="0cfd9-134">建立或選取網域帳戶，該帳戶擁有提供資料或服務給報表伺服器之電腦和伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-134">Create or select a domain account that has access to computers and servers that provide data or services to a report server.</span></span> <span data-ttu-id="0cfd9-135">您應使用擁有較小權限的帳戶 (例如唯讀權限)。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-135">You should use an account that has reduced permissions (for example, read-only permissions).</span></span>  
  
2.  <span data-ttu-id="0cfd9-136">開啟命令提示字元：在 [開始]  功能表上，按一下 [執行]  ，鍵入 **cmd**，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-136">Open a command prompt: On the **Start** menu, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0cfd9-137">輸入下列命令，即可在本機報表伺服器執行個體上設定帳戶：</span><span class="sxs-lookup"><span data-stu-id="0cfd9-137">Type the following command to configure the account on a local report server instance:</span></span>  
  
     <span data-ttu-id="0cfd9-138">**rsconfig-e-u \<domain/username> -p\<password>**</span><span class="sxs-lookup"><span data-stu-id="0cfd9-138">**rsconfig -e -u\<domain/username> -p\<password>**</span></span>  
  
 <span data-ttu-id="0cfd9-139">**rsconfig -e** 可支援其他引數。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-139">**rsconfig -e** supports additional arguments.</span></span> <span data-ttu-id="0cfd9-140">如需語法的詳細資訊以及若要檢視命令範例，請參閱《SQL Server 線上叢書》中的 [rsconfig 公用程式 &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-140">For more information about syntax and to view command examples, see [rsconfig Utility &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) in SQL Server Books Online.</span></span>  
  
### <a name="how-account-information-is-stored"></a><span data-ttu-id="0cfd9-141">如何儲存帳戶資訊</span><span class="sxs-lookup"><span data-stu-id="0cfd9-141">How Account Information is Stored</span></span>  
 <span data-ttu-id="0cfd9-142">當您設定此帳戶時，下列設定會當做加密的值指定於本機或遠端報表伺服器執行個體上的 RSreportserver.config 檔案中：</span><span class="sxs-lookup"><span data-stu-id="0cfd9-142">When you set the account, the following settings are specified as encrypted values in the RSreportserver.config file on a local or remote report server instance:</span></span>  
  
```  
<UnattendedExecutionAccount>  
     <UserName></UserName>  
     <Password></Password>  
     <Domain></Domain>  
</UnattendedExecutionAccount>  
```  
  
 <span data-ttu-id="0cfd9-143">您設定了值之後，就不能將值解密，以純文字檢視這些值。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-143">Once you set the values, you cannot decrypt them to view the values in plain text.</span></span> <span data-ttu-id="0cfd9-144">如果您輸入錯誤的值，或者忘記自己指定的值，就必須使用 Reporting Services 組態工具，或執行 **rsconfig -e** 以重新開始。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-144">If you mistype the values or forget the values you specified, you must use the Reporting Services Configuration tool or run **rsconfig -e** to start over.</span></span>  
  
## <a name="how-to-use-the-unattended-report-processing-account"></a><span data-ttu-id="0cfd9-145">如何使用自動報表處理帳戶</span><span class="sxs-lookup"><span data-stu-id="0cfd9-145">How to Use the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="0cfd9-146">為了擷取影像檔，報表伺服器會自動使用此帳戶，而且您不需要採取特定的動作。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-146">To retrieve image files, the report server uses the account automatically and no specific action is required on your part.</span></span> <span data-ttu-id="0cfd9-147">若要使用此帳戶連線到提供資料給報表的外部資料來源，您必須在報表資料來源或共用資料來源的資料來源屬性頁面上指定 [認證類型]  選項：</span><span class="sxs-lookup"><span data-stu-id="0cfd9-147">To use the account to connect to external data sources that provide data to reports, you must specify a **Credential Type** option in the data source properties page of the report data source or shared data source:</span></span>  
  
-   <span data-ttu-id="0cfd9-148">在報表管理員或 SharePoint 網站上，選取 [**不需要認證**] 選項。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-148">In Report Manager or on a SharePoint site, select the **Credentials are not required** option.</span></span>  
  
 <span data-ttu-id="0cfd9-149">自動報表處理帳戶主要是用來連接外部伺服器，而不是登入資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-149">The unattended report processing account is used primarily to connect to external servers, and not as a login to database servers.</span></span> <span data-ttu-id="0cfd9-150">如果您想要使用此帳戶認證來登入資料庫，就必須在連接字串中指定認證。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-150">If you want to use the account credentials to log in to a database, you must specify credentials in the connection string.</span></span> <span data-ttu-id="0cfd9-151">如果資料庫伺服器支援 Windows 整合式安全性，而且自動報表處理所使用的帳戶擁有讀取資料庫的權限，您就可以指定 **Integrated Security=SSPI** 。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-151">You can specify **Integrated Security=SSPI** if the database server supports Windows integrated security and the account used for unattended report processing has permission to read the database.</span></span> <span data-ttu-id="0cfd9-152">否則，您必須在連接字串中輸入使用者名稱和密碼，而此連接字串會以純文字格式顯示給有權編輯資料來源連接屬性的任何使用者查看。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-152">Otherwise, you must enter the user name and password in the connection string, where it appears in clear text to any user who has permission to edit data source connection properties.</span></span>  
  
 <span data-ttu-id="0cfd9-153">雖然系統不會禁止您在建立連接之後使用自動報表處理帳戶來擷取資料，但是我們不建議您這樣做。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-153">Although you are not prevented from using the unattended report processing account to retrieve data after the connection is made, doing so is not recommended.</span></span> <span data-ttu-id="0cfd9-154">您應該針對非常特定的功能使用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-154">The account is supposed to be used for very specific functions.</span></span> <span data-ttu-id="0cfd9-155">如果您用它來擷取資料，就會破壞它原本設計的用途。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-155">If you use it to retrieve data, you undermine the purpose for which it is intended.</span></span>  
  
## <a name="how-to-maintain-the-unattended-report-processing-account"></a><span data-ttu-id="0cfd9-156">如何維護自動報表處理帳戶</span><span class="sxs-lookup"><span data-stu-id="0cfd9-156">How to Maintain the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="0cfd9-157">一旦定義此帳戶後，就必須確保帳戶和密碼都保持最新狀態。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-157">Once you define the account, you must ensure that the account and password are kept up to date.</span></span> <span data-ttu-id="0cfd9-158">您可以使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具來更新儲存此帳戶之相關資訊的組態設定。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-158">You can use the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool to update the configuration settings that store information about this account.</span></span>  
  
1.  <span data-ttu-id="0cfd9-159">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-159">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="0cfd9-160">在 [執行帳戶] 頁面上，確認已經選取 [指定執行帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-160">On the Execution Account page, verify that **Specify an execution account** is selected.</span></span>  
  
3.  <span data-ttu-id="0cfd9-161">鍵入新帳戶和密碼，重新鍵入密碼，然後按一下 [套用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-161">Type the new account or password, retype the password, and then click **Apply**.</span></span>  
  
## <a name="how-to-delete-the-unattended-report-processing-account"></a><span data-ttu-id="0cfd9-162">如何刪除自動報表處理帳戶</span><span class="sxs-lookup"><span data-stu-id="0cfd9-162">How to Delete the Unattended Report Processing Account</span></span>  
 <span data-ttu-id="0cfd9-163">如果沒有使用此帳戶，可以將其刪除，這樣就不需經常進行帳戶維護工作。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-163">If you are not using the account, you can delete it to avoid routine account maintenance tasks.</span></span>  
  
1.  <span data-ttu-id="0cfd9-164">啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-164">Start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="0cfd9-165">在 [執行帳戶] 頁面上，清除 [指定執行帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-165">On the Execution Account page, clear **Specify an execution account**.</span></span>  
  
3.  <span data-ttu-id="0cfd9-166">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-166">Click **Apply**.</span></span>  
  
 <span data-ttu-id="0cfd9-167">帳戶資訊會隨即從 RSReportServer.config 檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="0cfd9-167">The account information is removed from the RSReportServer.config file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cfd9-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cfd9-168">See Also</span></span>  
 [<span data-ttu-id="0cfd9-169">Reporting Services 組態管理員 &#40;del&#41;</span><span class="sxs-lookup"><span data-stu-id="0cfd9-169">Reporting Services Configuration Manager &#40;del&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
