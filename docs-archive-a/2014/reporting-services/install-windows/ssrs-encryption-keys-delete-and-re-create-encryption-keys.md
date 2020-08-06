---
title: 刪除和重新建立加密金鑰 (SSRS 設定管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- re-creating encryption keys
- encryption keys [Reporting Services]
- deleting encryption keys
- symmetric keys [Reporting Services]
- removing encryption keys
- resetting encryption keys
ms.assetid: 201afe5f-acc9-4a37-b5ec-121dc7df2a61
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8fa5138e4bbb84395bad79a272d2bde31389396b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710294"
---
# <a name="delete-and-re-create-encryption-keys--ssrs-configuration-manager"></a><span data-ttu-id="a31c7-102">刪除和重新建立加密金鑰 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="a31c7-102">Delete and Re-create Encryption Keys  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="a31c7-103">刪除和重新建立加密金鑰是例行加密金鑰維護範圍之外的活動。</span><span class="sxs-lookup"><span data-stu-id="a31c7-103">Deleting and re-creating encryption keys are activities that fall outside of routine encryption key maintenance.</span></span> <span data-ttu-id="a31c7-104">執行這些工作是為了因應報表伺服器所受的特定威脅，或者當您無法存取報表伺服器資料庫時的最後手段。</span><span class="sxs-lookup"><span data-stu-id="a31c7-104">You perform these tasks in response to a specific threat to your report server, or as a last resort when you can no longer access a report server database.</span></span>  
  
-   <span data-ttu-id="a31c7-105">您認為現有的對稱金鑰被洩漏時，請重新建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-105">Re-create the symmetric key when you believe the existing symmetric key is compromised.</span></span> <span data-ttu-id="a31c7-106">也可以當成最佳安全性作法，定期重新建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-106">You can also re-create the key on a regular basis as a security best practice.</span></span>  
  
-   <span data-ttu-id="a31c7-107">當您無法還原對稱金鑰時，請刪除現有的加密金鑰和無法使用的加密內容。</span><span class="sxs-lookup"><span data-stu-id="a31c7-107">Delete existing encryption keys and unusable encrypted content when you cannot restore the symmetric key.</span></span>  
  
## <a name="re-creating-encryption-keys"></a><span data-ttu-id="a31c7-108">重新建立加密金鑰</span><span class="sxs-lookup"><span data-stu-id="a31c7-108">Re-creating Encryption Keys</span></span>  
 <span data-ttu-id="a31c7-109">如果有證據顯示未授權使用者已獲悉對稱金鑰，或者您的報表伺服器已遭到攻擊，而您想要重設對稱金鑰做為預防，您就可以重新建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-109">If you have evidence that the symmetric key is known to unauthorized users, or if your report server has been under attack and you want to reset the symmetric key as a precaution, you can re-create the symmetric key.</span></span> <span data-ttu-id="a31c7-110">重新建立對稱金鑰時，所有加密值都會使用新值重新加密。</span><span class="sxs-lookup"><span data-stu-id="a31c7-110">When you re-create the symmetric key, all encrypted values will be re-encrypted using the new value.</span></span> <span data-ttu-id="a31c7-111">如果您是在向外延展部署中執行多個報表伺服器，對稱金鑰的所有副本都會更新為新值。</span><span class="sxs-lookup"><span data-stu-id="a31c7-111">If you are running multiple report servers in a scale-out deployment, all copies of the symmetric key will be updated to the new value.</span></span> <span data-ttu-id="a31c7-112">報表伺服器使用它能使用的公開金鑰，來更新部署中每個伺服器的對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-112">The report server uses the public keys available to it to update the symmetric key for each server in the deployment.</span></span>  
  
 <span data-ttu-id="a31c7-113">唯有報表伺服器處於工作狀態時，您才能重新建立對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-113">You can only re-create the symmetric key when the report server is in a working state.</span></span> <span data-ttu-id="a31c7-114">重新建立加密金鑰和重新加密內容會中斷伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-114">Re-creating the encryption keys and re-encrypting content disrupts server operations.</span></span> <span data-ttu-id="a31c7-115">進行重新加密時，必須將伺服器離線。</span><span class="sxs-lookup"><span data-stu-id="a31c7-115">You must take the server offline while re-encryption is underway.</span></span> <span data-ttu-id="a31c7-116">重新加密過程中，不應該對報表伺服器提出任何要求。</span><span class="sxs-lookup"><span data-stu-id="a31c7-116">There should be no requests made to the report server during re-encryption.</span></span>  
  
 <span data-ttu-id="a31c7-117">您可以使用 Reporting Services 組態工具或 **rskeymgmt** 公用程式，來重設對稱金鑰和加密資料。</span><span class="sxs-lookup"><span data-stu-id="a31c7-117">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to reset the symmetric key and encrypted data.</span></span> <span data-ttu-id="a31c7-118">如需如何建立對稱金鑰的詳細資訊，請參閱[初始化報表伺服器 &#40;SSRS 設定管理員&#41;](ssrs-encryption-keys-initialize-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a31c7-118">For more information about how the symmetric key is created, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="a31c7-119">如何重新建立加密金鑰 (Reporting Services 組態工具)</span><span class="sxs-lookup"><span data-stu-id="a31c7-119">How to re-create encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="a31c7-120">透過在 rsreportserver.config 檔案中修改 `IsWebServiceEnabled` 屬性，停用報表伺服器 Web 服務和 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="a31c7-120">Disable the Report Server Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="a31c7-121">此步驟會讓驗證要求暫時停止送給報表伺服器，而不會完全關閉伺服器。</span><span class="sxs-lookup"><span data-stu-id="a31c7-121">This step temporarily stops authentication requests from being sent to the report server without completely shutting down the server.</span></span> <span data-ttu-id="a31c7-122">您必須有最少的服務，好讓您可以重新建立金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-122">You must have minimal service so that you can recreate the keys.</span></span>  
  
     <span data-ttu-id="a31c7-123">如果您是重新建立報表伺服器向外延展部署的加密金鑰，請針對部署中的所有執行個體停用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="a31c7-123">If you are recreating encryption keys for a report server scale-out deployment, disable this property on all instances in the deployment.</span></span>  
  
    1.  <span data-ttu-id="a31c7-124">開啟 Windows 檔案總管並巡覽至 *drive*:\Program Files\Microsoft SQL Server\\<報表伺服器執行個體>\*\* \Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="a31c7-124">Open Windows Explorer and navigate to *drive*:\Program Files\Microsoft SQL Server\\*report_server_instance*\Reporting Services.</span></span> <span data-ttu-id="a31c7-125">將 *drive* 取代成磁碟機代號並將 <報表伺服器執行個體>\*\* 取代成對應至您想要停用 Web 服務和 HTTP 存取之報表伺服器執行個體的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="a31c7-125">Replace *drive* with your drive letter and *report_server_instance* with the folder name that corresponds to the report server instance for which you want to disable the Web service and HTTP access.</span></span> <span data-ttu-id="a31c7-126">例如，C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services。</span><span class="sxs-lookup"><span data-stu-id="a31c7-126">For example, C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services.</span></span>  
  
    2.  <span data-ttu-id="a31c7-127">開啟 rsreportserver.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="a31c7-127">Open the rsreportserver.config file.</span></span>  
  
    3.  <span data-ttu-id="a31c7-128">針對 `IsWebServiceEnabled` 屬性，指定 `False`，然後儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="a31c7-128">For the `IsWebServiceEnabled` property, specify `False`, and then save your changes.</span></span>  
  
2.  <span data-ttu-id="a31c7-129">啟動 Reporting Services 組態工具，然後連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a31c7-129">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
3.  <span data-ttu-id="a31c7-130">在 [加密金鑰] 頁面上，按一下 **[變更]**。</span><span class="sxs-lookup"><span data-stu-id="a31c7-130">On the Encryption Keys page, click **Change**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="a31c7-131">重新啟動報表伺服器 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="a31c7-131">Restart the Report Server Windows service.</span></span> <span data-ttu-id="a31c7-132">如果是重新建立向外延展部署的加密金鑰，請重新啟動所有執行個體上的服務。</span><span class="sxs-lookup"><span data-stu-id="a31c7-132">If you are recreating encryption keys for a scale-out deployment, restart the service on all instances.</span></span>  
  
5.  <span data-ttu-id="a31c7-133">透過在 rsreportserver.config 檔案中修改 `IsWebServiceEnabled` 屬性，重新啟用 Web 服務和 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="a31c7-133">Re-enable the Web service and HTTP access by modifying the `IsWebServiceEnabled` property in the rsreportserver.config file.</span></span> <span data-ttu-id="a31c7-134">如果是處理向外延展部署，請為所有執行個體執行此作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-134">Do this for all instances if you are working with a scale out deployment.</span></span>  
  
#### <a name="how-to-re-create-encryption-keys-rskeymgmt"></a><span data-ttu-id="a31c7-135">如何重新建立加密金鑰 (rskeymgmt)</span><span class="sxs-lookup"><span data-stu-id="a31c7-135">How to re-create encryption keys (rskeymgmt)</span></span>  
  
1.  <span data-ttu-id="a31c7-136">停用報表伺服器 Web 服務和 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="a31c7-136">Disable the Report Server Web service and HTTP access.</span></span> <span data-ttu-id="a31c7-137">使用前面程序中的指示來停止 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-137">Use the instructions in the previous procedure to stop Web service operations.</span></span>  
  
2.  <span data-ttu-id="a31c7-138">在主控報表伺服器的本機電腦上，執行 **[rskeymgmt.exe]** 。</span><span class="sxs-lookup"><span data-stu-id="a31c7-138">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="a31c7-139">使用 `-s` 引數來重設對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="a31c7-139">Use the `-s` argument to reset the symmetric key.</span></span> <span data-ttu-id="a31c7-140">不需要其他引數：</span><span class="sxs-lookup"><span data-stu-id="a31c7-140">No other arguments are required:</span></span>  
  
    ```  
    rskeymgmt -s  
    ```  
  
3.  <span data-ttu-id="a31c7-141">重新啟動 Windows 服務，並啟用 Web 服務作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-141">Restart the Windows service and enable Web service operations.</span></span>  
  
## <a name="deleting-unusable-encrypted-content"></a><span data-ttu-id="a31c7-142">刪除無法使用的加密內容</span><span class="sxs-lookup"><span data-stu-id="a31c7-142">Deleting Unusable Encrypted Content</span></span>  
 <span data-ttu-id="a31c7-143">如果因故無法還原加密金鑰，報表伺服器將無法解密及使用以該金鑰加密的任何資料。</span><span class="sxs-lookup"><span data-stu-id="a31c7-143">If for some reason you cannot restore the encryption key, the report server will never be able to decrypt and use any data that is encrypted with that key.</span></span> <span data-ttu-id="a31c7-144">若要使報表伺服器回到工作狀態，必須刪除目前儲存在報表伺服器資料庫中的加密值，然後手動重新指定您需要的值。</span><span class="sxs-lookup"><span data-stu-id="a31c7-144">To return the report server to a working state, you must delete the encrypted values that are currently stored in the report server database and then manually re-specify the values you need.</span></span>  
  
 <span data-ttu-id="a31c7-145">刪除加密金鑰會從報表伺服器資料庫移除所有對稱金鑰資訊，並刪除任何加密內容。</span><span class="sxs-lookup"><span data-stu-id="a31c7-145">Deleting the encryption keys removes all symmetric key information from the report server database and deletes any encrypted content.</span></span> <span data-ttu-id="a31c7-146">所有未加密資料都不受影響；只會移除加密的內容。</span><span class="sxs-lookup"><span data-stu-id="a31c7-146">All unencrypted data is left intact; only encrypted content is removed.</span></span> <span data-ttu-id="a31c7-147">刪除加密金鑰時，報表伺服器會加入新的對稱金鑰，自動將其本身重新初始化。</span><span class="sxs-lookup"><span data-stu-id="a31c7-147">When you delete the encryption keys, the report server re-initializes itself automatically by adding a new symmetric key.</span></span> <span data-ttu-id="a31c7-148">刪除加密內容時會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="a31c7-148">The following occurs when you delete encrypted content:</span></span>  
  
-   <span data-ttu-id="a31c7-149">刪除共用資料來源中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="a31c7-149">Connection strings in shared data sources are deleted.</span></span> <span data-ttu-id="a31c7-150">執行報表的使用者會收到「尚未初始化 ConnectionString 屬性」錯誤。</span><span class="sxs-lookup"><span data-stu-id="a31c7-150">Users who run reports get the error "The ConnectionString property has not been initialized."</span></span>  
  
-   <span data-ttu-id="a31c7-151">刪除預存認證。</span><span class="sxs-lookup"><span data-stu-id="a31c7-151">Stored credentials are deleted.</span></span> <span data-ttu-id="a31c7-152">報表與共用資料來源會重新設定成使用提示的認證。</span><span class="sxs-lookup"><span data-stu-id="a31c7-152">Reports and shared data sources are reconfigured to use prompted credentials.</span></span>  
  
-   <span data-ttu-id="a31c7-153">以模型為基礎的報表 (而且需要以預存認證或無認證設定共用資料來源) 將不會執行。</span><span class="sxs-lookup"><span data-stu-id="a31c7-153">Reports that are based on models (and require shared data sources configured with stored or no credentials) will not run.</span></span>  
  
-   <span data-ttu-id="a31c7-154">停用訂閱。</span><span class="sxs-lookup"><span data-stu-id="a31c7-154">Subscriptions are deactivated.</span></span>  
  
 <span data-ttu-id="a31c7-155">一旦刪除加密內容，就無法再復原內容。</span><span class="sxs-lookup"><span data-stu-id="a31c7-155">Once you delete encrypted content, you cannot recover it.</span></span> <span data-ttu-id="a31c7-156">您必須重新指定連接字串和預存認證，也必須啟動訂閱。</span><span class="sxs-lookup"><span data-stu-id="a31c7-156">You must re-specify connection strings and stored credentials, and you must activate subscriptions.</span></span>  
  
 <span data-ttu-id="a31c7-157">您可以使用 Reporting Services 組態工具或 **rskeymgmt** 公用程式來移除值。</span><span class="sxs-lookup"><span data-stu-id="a31c7-157">You can use the Reporting Services Configuration tool or the **rskeymgmt** utility to remove the values.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-reporting-services-configuration-tool"></a><span data-ttu-id="a31c7-158">如何刪除加密金鑰 (Reporting Services 組態工具)</span><span class="sxs-lookup"><span data-stu-id="a31c7-158">How to delete encryption keys (Reporting Services Configuration Tool)</span></span>  
  
1.  <span data-ttu-id="a31c7-159">啟動 Reporting Services 組態工具，然後連接到您要設定的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a31c7-159">Start the Reporting Services Configuration tool, and then connect to the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="a31c7-160">按一下 **[加密金鑰]**，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="a31c7-160">Click **Encryption Keys**, and then click **Delete**.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="a31c7-161">重新啟動報表伺服器 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="a31c7-161">Restart the Report Server Windows service.</span></span> <span data-ttu-id="a31c7-162">針對向外延展部署，為所有報表伺服器執行個體執行此作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-162">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-delete-encryption-keys-rskeymmgt"></a><span data-ttu-id="a31c7-163">如何刪除加密金鑰 (rskeymmgt)</span><span class="sxs-lookup"><span data-stu-id="a31c7-163">How to delete encryption keys (rskeymmgt)</span></span>  
  
1.  <span data-ttu-id="a31c7-164">在主控報表伺服器的本機電腦上，執行 **[rskeymgmt.exe]** 。</span><span class="sxs-lookup"><span data-stu-id="a31c7-164">Run **rskeymgmt.exe** locally on the computer that hosts the report server.</span></span> <span data-ttu-id="a31c7-165">您必須使用 **-d** 套用引數。</span><span class="sxs-lookup"><span data-stu-id="a31c7-165">You must use the **-d** apply argument.</span></span> <span data-ttu-id="a31c7-166">下列範例說明您必須指定的引數：</span><span class="sxs-lookup"><span data-stu-id="a31c7-166">The following example illustrates the argument you must specify:</span></span>  
  
    ```  
    rskeymgmt -d  
    ```  
  
2.  <span data-ttu-id="a31c7-167">重新啟動報表伺服器 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="a31c7-167">Restart the Report Server Windows service.</span></span> <span data-ttu-id="a31c7-168">針對向外延展部署，為所有報表伺服器執行個體執行此作業。</span><span class="sxs-lookup"><span data-stu-id="a31c7-168">For a scale-out deployment, do this on all report server instances.</span></span>  
  
#### <a name="how-to-re-specify-encrypted-values"></a><span data-ttu-id="a31c7-169">如何重新指定加密值</span><span class="sxs-lookup"><span data-stu-id="a31c7-169">How to re-specify encrypted values</span></span>  
  
1.  <span data-ttu-id="a31c7-170">針對每個共用資料來源，您必須重新輸入連接字串。</span><span class="sxs-lookup"><span data-stu-id="a31c7-170">For each shared data source, you must retype the connection string.</span></span>  
  
2.  <span data-ttu-id="a31c7-171">針對使用預存認證的每個報表與共用資料來源，您必須重新輸入使用者名稱與密碼，然後儲存。</span><span class="sxs-lookup"><span data-stu-id="a31c7-171">For each report and shared data source that uses stored credentials, you must retype the user name and password, and then save.</span></span> <span data-ttu-id="a31c7-172">如需詳細資訊，請參閱《 [線上叢書》中的](../../integration-services/connection-manager/data-sources.md) 指定報表資料來源的認證和連接資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a31c7-172">For more information, see [Specify Credential and Connection Information for Report Data Sources](../../integration-services/connection-manager/data-sources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
3.  <span data-ttu-id="a31c7-173">針對每個資料驅動訂閱，開啟每個訂閱，並重新輸入訂閱資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="a31c7-173">For each data-driven subscription, open each subscription and retype the credentials to the subscription database.</span></span>  
  
4.  <span data-ttu-id="a31c7-174">針對使用加密資料的訂閱 (這包括使用加密的檔案共用傳遞延伸模組和協力廠商傳遞延伸模組)，開啟每個訂閱並重新輸入認證。</span><span class="sxs-lookup"><span data-stu-id="a31c7-174">For subscriptions that use encrypted data (this includes the File Share delivery extension and any third-party delivery extension that uses encryption), open each subscription and retype credentials.</span></span> <span data-ttu-id="a31c7-175">使用報表伺服器電子郵件傳遞的訂閱並不使用加密資料，因此不受金鑰變更的影響。</span><span class="sxs-lookup"><span data-stu-id="a31c7-175">Subscriptions that use Report Server e-mail delivery do not use encrypted data and are unaffected by the key change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31c7-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a31c7-176">See Also</span></span>  
 <span data-ttu-id="a31c7-177">[設定和管理 &#40;SSRS Configuration Manager 的加密金鑰&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="a31c7-177">[Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;](ssrs-encryption-keys-manage-encryption-keys.md) </span></span>  
 [<span data-ttu-id="a31c7-178">儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="a31c7-178">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
