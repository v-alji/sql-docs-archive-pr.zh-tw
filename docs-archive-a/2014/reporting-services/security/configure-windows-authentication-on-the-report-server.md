---
title: 設定報表伺服器上的 Windows 驗證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [Reporting Services]
- Reporting Services, configuration
ms.assetid: 4de9c3dd-0ee7-49b3-88bb-209465ca9d86
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 879c036977f9a34528dbf38e42fa080e72617a14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699304"
---
# <a name="configure-windows-authentication-on-the-report-server"></a><span data-ttu-id="9b003-102">設定報表伺服器上的 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="9b003-102">Configure Windows Authentication on the Report Server</span></span>
  <span data-ttu-id="9b003-103">依預設， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 會接受可指定交涉驗證或 NTLM 驗證的要求。</span><span class="sxs-lookup"><span data-stu-id="9b003-103">By default, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] accepts requests that specify Negotiate or NTLM authentication.</span></span> <span data-ttu-id="9b003-104">如果您的部署包括了使用這些安全性提供者的用戶端應用程式和瀏覽器，您可以使用預設值，而不需要進行額外的組態設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-104">If your deployment includes client applications and browsers that use these security providers, you can use the default values without additional configuration.</span></span> <span data-ttu-id="9b003-105">如果您想要針對 Windows 整合式安全性使用不同的安全性提供者 (例如，如果您想要直接使用 Kerberos)，或是您修改了預設值而且想要還原原始設定，您可以使用本主題的資訊來指定報表伺服器上的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-105">If you want to use a different security provider for Windows integrated security (for example, if you want to use Kerberos directly), or if you modified the default values and want to restore the original settings, you can use the information in this topic to specify authentication settings on the report server.</span></span>  
  
 <span data-ttu-id="9b003-106">若要使用 Windows 整合式安全性，每一個需要存取報表伺服器的使用者都必須擁有有效的 Windows 本機或網域使用者帳戶，或者必須是 Windows 本機或網域群組帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="9b003-106">To use Windows integrated security, each user who requires access to a report server must have a valid Windows local or domain user account or be a member of a Windows local or domain group account.</span></span> <span data-ttu-id="9b003-107">您可以將其他信任網域中的帳戶包括在內。</span><span class="sxs-lookup"><span data-stu-id="9b003-107">You can include accounts from other domains as long as those domains are trusted.</span></span> <span data-ttu-id="9b003-108">這些帳戶必須對報表伺服器電腦擁有存取權，且必須接著指派給角色，以取得特定報表伺服器作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="9b003-108">The accounts must have access to the report server computer, and must be subsequently assigned to roles in order to gain access to specific report server operations.</span></span>  
  
 <span data-ttu-id="9b003-109">也必須符合下列其他需求：</span><span class="sxs-lookup"><span data-stu-id="9b003-109">The following additional requirements must also be met:</span></span>  
  
-   <span data-ttu-id="9b003-110">RSeportServer.config 檔案必須將 `AuthenticationType` 設定為 `RSWindowsNegotiate`、`RSWindowsKerberos` 或 `RSWindowsNTLM`。</span><span class="sxs-lookup"><span data-stu-id="9b003-110">The RSeportServer.config files must have `AuthenticationType` set to `RSWindowsNegotiate`, `RSWindowsKerberos`, or `RSWindowsNTLM`.</span></span> <span data-ttu-id="9b003-111">根據預設，如果報表伺服器服務帳戶是 NetworkService 或 LocalSystem，RSReportServer.config 檔就會包含 `RSWindowsNegotiate` 設定。否則，就會使用 `RSWindowsNTLM` 設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-111">By default, the RSReportServer.config file includes the `RSWindowsNegotiate` setting if the Report Server service account is either NetworkService or LocalSystem; otherwise, the `RSWindowsNTLM` setting is used.</span></span> <span data-ttu-id="9b003-112">如果您的應用程式只使用 Kerberos 驗證，您可以加入 `RSWindowsKerberos`。</span><span class="sxs-lookup"><span data-stu-id="9b003-112">You can add `RSWindowsKerberos` if you have applications that only use Kerberos authentication.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9b003-113">如果您設定報表伺服器服務使用網域使用者帳戶執行，而且您並未針對此帳戶註冊服務主要名稱 (SPN)，則使用 `RSWindowsNegotiate` 將會產生 Kerberos 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b003-113">Using `RSWindowsNegotiate` will result in a Kerberos authentication error if you configured the Report Server service to run under a domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span> <span data-ttu-id="9b003-114">如需詳細資訊，請參閱本主題的 [在連接報表伺服器時解決 Kerberos 驗證錯誤](#proxyfirewallRSWindowsNegotiate) 。</span><span class="sxs-lookup"><span data-stu-id="9b003-114">For more information, see [Resolving Kerberos Authentication Errors When Connecting to a report server](#proxyfirewallRSWindowsNegotiate) in this topic.</span></span>  
  
-   [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="9b003-115">必須設定 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9b003-115">must be configured for Windows Authentication.</span></span> <span data-ttu-id="9b003-116">根據預設，報表伺服器 Web 服務和報表管理員的 Web.config 檔案包含 \<authentication mode="Windows"> 設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-116">By default, the Web.config files for the Report Server Web service and Report Manager include the \<authentication mode="Windows"> setting.</span></span> <span data-ttu-id="9b003-117">如果您將它變更為 \<authentication mode="Forms"> ，則的 Windows 驗證 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9b003-117">If you change it to \<authentication mode="Forms">, the Windows Authentication for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] will fail.</span></span>  
  
-   <span data-ttu-id="9b003-118">報表伺服器 Web 服務和報表管理員的 Web.config 檔必須具有 \<identity impersonate= "true" /> 。</span><span class="sxs-lookup"><span data-stu-id="9b003-118">The Web.config files for the Report Server Web service and Report Manager must have \<identity impersonate= "true" />.</span></span>  
  
-   <span data-ttu-id="9b003-119">用戶端應用程式或瀏覽器必須支援 Windows 整合式安全性。</span><span class="sxs-lookup"><span data-stu-id="9b003-119">The client application or browser must support Windows integrated security.</span></span>  
  
 <span data-ttu-id="9b003-120">若要變更報表伺服器驗證設定，請編輯 RSReportServer.config 檔案中的 XML 元素和值。</span><span class="sxs-lookup"><span data-stu-id="9b003-120">To change the report server authentication settings, edit the XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="9b003-121">您可以複製及貼上本主題的範例，以實作特定的組合。</span><span class="sxs-lookup"><span data-stu-id="9b003-121">You can copy and paste the examples in this topic to implement specific combinations.</span></span>  
  
 <span data-ttu-id="9b003-122">如果所有的用戶端和伺服器電腦全都位於相同網域或信任網域，或是公司防火牆後方已部署報表伺服器供內部網路存取使用，預設值便可達到最佳的效果。</span><span class="sxs-lookup"><span data-stu-id="9b003-122">The default settings work best if all client and server computers are in the same domain or in a trusted domain and the report server is deployed for intranet access behind a corporate firewall.</span></span> <span data-ttu-id="9b003-123">若要傳遞 Windows 認證，網域必須是受信任的網域或單一網域。</span><span class="sxs-lookup"><span data-stu-id="9b003-123">Trusted and single domains are a requirement for passing Windows credentials.</span></span> <span data-ttu-id="9b003-124">伺服器必須啟用 Kerberos 第 5 版通訊協定，才能多次傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="9b003-124">Credentials can be passed more than one time if you enable the Kerberos version 5 protocol for your servers.</span></span> <span data-ttu-id="9b003-125">否則，認證在逾期前僅能傳遞一次。</span><span class="sxs-lookup"><span data-stu-id="9b003-125">Otherwise, credentials can be passed only one time before they expire.</span></span> <span data-ttu-id="9b003-126">如需設定多個電腦連接之認證的詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="9b003-126">For more information about configuring credentials for multiple computer connections, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="9b003-127">下列指示用於原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b003-127">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="9b003-128">如果您在 SharePoint 整合模式下部署報表伺服器，您必須使用可指定 Windows 整合式安全性的預設驗證設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-128">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="9b003-129">報表伺服器會使用預設 Windows 驗證延伸模組中的內部功能來支援 SharePoint 整合模式下的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b003-129">The report server uses internal features in the default Windows Authentication extension to support report servers in SharePoint integrated mode.</span></span>  
  
## <a name="extended-protection-for-authentication"></a><span data-ttu-id="9b003-130">驗證擴充保護</span><span class="sxs-lookup"><span data-stu-id="9b003-130">Extended Protection for Authentication</span></span>  
 <span data-ttu-id="9b003-131">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]開始，就有驗證擴充保護的支援可以使用。</span><span class="sxs-lookup"><span data-stu-id="9b003-131">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], support for Extended Protection for Authentication is available.</span></span> <span data-ttu-id="9b003-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能可支援使用通道繫結和服務繫結，以增強驗證的保護。</span><span class="sxs-lookup"><span data-stu-id="9b003-132">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] feature supports the use of channel binding and service binding to enhance protection of authentication.</span></span> <span data-ttu-id="9b003-133">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能需要搭配支援擴充保護的作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="9b003-133">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features need to be used with an operating system that supports Extended Protection.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9b003-134">擴充保護的組態是由 RSReportServer.config 檔案中的設定所決定。</span><span class="sxs-lookup"><span data-stu-id="9b003-134">configuration for extended protection is determined by settings in the RSReportServer.config file.</span></span> <span data-ttu-id="9b003-135">若要更新這個檔案，您可以編輯檔案或使用 WMI API。</span><span class="sxs-lookup"><span data-stu-id="9b003-135">The file can be updated by either editing the file or using WMI APIs.</span></span> <span data-ttu-id="9b003-136">如需詳細資訊，請參閱 [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9b003-136">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md).</span></span>  
  
### <a name="to-configure-a-report-server-to-use-windows-integrated-security"></a><span data-ttu-id="9b003-137">若要設定報表伺服器使用 Windows 整合式安全性</span><span class="sxs-lookup"><span data-stu-id="9b003-137">To configure a report server to use Windows integrated security</span></span>  
  
1.  <span data-ttu-id="9b003-138">在文字編輯器中開啟 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="9b003-138">Open RSReportServer.config in a text editor.</span></span>  
  
2.  <span data-ttu-id="9b003-139">尋找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="9b003-139">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="9b003-140">複製下列其中一個最符合您需要的 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="9b003-140">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="9b003-141">您可以依照任何順序來指定 `RSWindowsNegotiate`、`RSWindowsNTLM` 和 `RSWindowsKerberos`。</span><span class="sxs-lookup"><span data-stu-id="9b003-141">You can specify `RSWindowsNegotiate`, `RSWindowsNTLM`, and `RSWindowsKerberos` in any order.</span></span> <span data-ttu-id="9b003-142">如果您想要驗證連接而不是每一個個別要求，則應該啟用驗證持續性。</span><span class="sxs-lookup"><span data-stu-id="9b003-142">You should enable authentication persistence if you want to authenticate the connection rather than each individual request.</span></span> <span data-ttu-id="9b003-143">在驗證持續性之下，將會在連接的持續時間內允許要求驗證的所有要求。</span><span class="sxs-lookup"><span data-stu-id="9b003-143">Under authentication persistence, all requests that require authentication will be allowed for the duration of the connection.</span></span>  
  
     <span data-ttu-id="9b003-144">當報表伺服器服務帳戶是 NetworkService 或 LocalSystem 時，第一個 XML 結構是預設的組態：</span><span class="sxs-lookup"><span data-stu-id="9b003-144">The first XML structure is the default configuration when the Report Server service account is either NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="9b003-145">當報表伺服器服務帳戶不是 NetworkService 或 LocalSystem 時，第二個 XML 結構是預設的組態：</span><span class="sxs-lookup"><span data-stu-id="9b003-145">The second XML structure is the default configuration when the Report Server service account is not NetworkService or LocalSystem:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    ```  
  
     \</Authentication>  
  
     <span data-ttu-id="9b003-146">第三個 XML 結構會指定用於 Windows 整合式安全性的所有安全性封裝：</span><span class="sxs-lookup"><span data-stu-id="9b003-146">The third XML structure specifies all of the security packages that are used in Windows integrated security:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNegotiate />  
                 <RSWindowsKerberos />  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
     <span data-ttu-id="9b003-147">第四個 XML 結構只會針對不支援 Kerberos 的部署指定 NTLM，或是暫時解決 Kerberos 驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="9b003-147">The fourth XML structure specifies NTLM only for deployments that do not support Kerberos or to work around Kerberos authentication errors:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsNTLM />  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="9b003-148">將它貼到 <> 的現有專案上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="9b003-148">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="9b003-149">請注意，您不能搭配 `Custom` 型別使用 `RSWindows`。</span><span class="sxs-lookup"><span data-stu-id="9b003-149">Note that you cannot use `Custom` with the `RSWindows` types.</span></span>  
  
5.  <span data-ttu-id="9b003-150">修改為擴充保護的適當設定。</span><span class="sxs-lookup"><span data-stu-id="9b003-150">Modify as appropriate the settings for extended protection.</span></span> <span data-ttu-id="9b003-151">預設會停用擴充保護。</span><span class="sxs-lookup"><span data-stu-id="9b003-151">Extended protection is disabled by default.</span></span>  <span data-ttu-id="9b003-152">如果這些項目不存在，目前的電腦可能未執行支援擴充保護的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="9b003-152">If these entries are not present, the current computer may not be running a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] which supports extended protection.</span></span> <span data-ttu-id="9b003-153">如需詳細資訊，請參閱＜ [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)＞</span><span class="sxs-lookup"><span data-stu-id="9b003-153">For more information, see [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
    ```  
          <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>  
          <RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
    ```  
  
6.  <span data-ttu-id="9b003-154">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9b003-154">Save the file.</span></span>  
  
7.  <span data-ttu-id="9b003-155">如果您設定了向外延展部署，請針對部署中的其他報表伺服器重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9b003-155">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="9b003-156">重新啟動報表伺服器，清除目前開啟的任何工作階段。</span><span class="sxs-lookup"><span data-stu-id="9b003-156">Restart the report server to clear any sessions that are currently open.</span></span>  
  
##  <a name="resolving-kerberos-authentication-errors-when-connecting-to-a-report-server"></a><a name="proxyfirewallRSWindowsNegotiate"></a> <span data-ttu-id="9b003-157">連接到報表伺服器時解決 Kerberos 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="9b003-157">Resolving Kerberos Authentication Errors When Connecting to a Report Server</span></span>  
 <span data-ttu-id="9b003-158">在設定交涉式驗證或 Kerberos 驗證的報表伺服器上，如果發生 Kerberos 驗證錯誤，與報表伺服器的用戶端連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9b003-158">On a report server that is configured for Negotiate or Kerberos authentication, a client connection to the report server will fail if there is a Kerberos authentication error.</span></span> <span data-ttu-id="9b003-159">目前已知以下情況下會發生 Kerberos 驗證錯誤：</span><span class="sxs-lookup"><span data-stu-id="9b003-159">Kerberos authentication errors are known to occur when:</span></span>  
  
-   <span data-ttu-id="9b003-160">報表伺服器服務以 Windows 網域使用者帳戶的身分執行，而且您並未針對此帳戶註冊服務主要名稱 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="9b003-160">The Report Server service runs as a Windows domain user account and you did not register a Service Principal Name (SPN) for the account.</span></span>  
  
-   <span data-ttu-id="9b003-161">使用 `RSWindowsNegotiate` 設定來設定報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b003-161">The report server is configured with the `RSWindowsNegotiate` setting.</span></span>  
  
-   <span data-ttu-id="9b003-162">瀏覽器在它傳送給報表伺服器之要求的驗證標頭中優先選擇 Kerberos (勝於 NTLM)。</span><span class="sxs-lookup"><span data-stu-id="9b003-162">The browser chooses Kerberos over NTLM in the authentication header in the request it sends to the report server.</span></span>  
  
 <span data-ttu-id="9b003-163">如果您啟用 Kerberos 記錄，就可以偵測此錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b003-163">You can detect the error if you enabled Kerberos logging.</span></span> <span data-ttu-id="9b003-164">此錯誤的其他徵兆是系統會提示您輸入多次認證，然後您會看到空白瀏覽器視窗。</span><span class="sxs-lookup"><span data-stu-id="9b003-164">Another symptom of the error is that you are prompted for credentials multiple times and then see an empty browser window.</span></span>  
  
 <span data-ttu-id="9b003-165">您可以 `RSWindowsNegotiate` 從設定檔中移除 </> 並重新嘗試連線，以確認您遇到 Kerberos 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b003-165">You can confirm that you are encountering a Kerberos authentication error by removing < `RSWindowsNegotiate` /> from your configuration file and reattempting the connection.</span></span>  
  
 <span data-ttu-id="9b003-166">在您確認問題之後，可以透過以下方式來解決：</span><span class="sxs-lookup"><span data-stu-id="9b003-166">After you confirm the problem, you can address it in the following ways:</span></span>  
  
-   <span data-ttu-id="9b003-167">使用網域使用者帳戶為報表伺服器服務註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="9b003-167">Register an SPN for the Report Server service under the domain user account.</span></span> <span data-ttu-id="9b003-168">如需詳細資訊，請參閱[為報表伺服器註冊服務主體名稱 &#40;SPN&#41;](../report-server/register-a-service-principal-name-spn-for-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9b003-168">For more information, see [Register a Service Principal Name &#40;SPN&#41; for a Report Server](../report-server/register-a-service-principal-name-spn-for-a-report-server.md).</span></span>  
  
-   <span data-ttu-id="9b003-169">變更服務帳戶，以便在類似網路服務的內建帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="9b003-169">Change the service account to run under a built-in account such as Network Service.</span></span> <span data-ttu-id="9b003-170">內建帳戶會將 HTTP SPN 對應到主機 SPN (當您將電腦加入網路時會加以定義)。</span><span class="sxs-lookup"><span data-stu-id="9b003-170">Built-in accounts map HTTP SPN to the Host SPN, which is defined when you join a computer to your network.</span></span> <span data-ttu-id="9b003-171">如需詳細資訊，請參閱[設定服務帳戶 &#40;SSRS 設定管理員&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9b003-171">For more information, see [Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md).</span></span>  
  
-   <span data-ttu-id="9b003-172">使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="9b003-172">Use NTLM.</span></span> <span data-ttu-id="9b003-173">當 Kerberos 驗證失敗時，NTLM 通常會正常運作。</span><span class="sxs-lookup"><span data-stu-id="9b003-173">NTLM will generally work in cases where Kerberos authentication fails.</span></span> <span data-ttu-id="9b003-174">若要使用 NTLM，請從 RSReportServer.config 檔案中移除 `RSWindowsNegotiate`，並確認只有指定 `RSWindowsNTLM`。</span><span class="sxs-lookup"><span data-stu-id="9b003-174">To use NTLM, remove `RSWindowsNegotiate` from the RSReportServer.config file and verify that only `RSWindowsNTLM` is specified.</span></span> <span data-ttu-id="9b003-175">如果您選擇這個方法，您可以繼續針對報表伺服器服務使用網域使用者帳戶，即使您未針對此帳戶定義 SPN。</span><span class="sxs-lookup"><span data-stu-id="9b003-175">If you choose this approach, you can continue to use a domain user account for the Report Server service even if you do not define an SPN for it.</span></span>  
  
#### <a name="logging-information"></a><span data-ttu-id="9b003-176">記錄資訊</span><span class="sxs-lookup"><span data-stu-id="9b003-176">Logging information</span></span>  
 <span data-ttu-id="9b003-177">有幾個記錄資訊來源可幫助解決 Kerberos 相關問題。</span><span class="sxs-lookup"><span data-stu-id="9b003-177">There are several sources of logging information that can help resolve Kerberos related issues.</span></span>  
  
##### <a name="user-account-control-attribute"></a><span data-ttu-id="9b003-178">User-Account-Control 屬性</span><span class="sxs-lookup"><span data-stu-id="9b003-178">User-Account-Control Attribute</span></span>  
 <span data-ttu-id="9b003-179">判斷 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務帳戶是否在 Active Directory 中設定足夠的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b003-179">Determine if the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service account has the sufficient attribute set in Active Directory.</span></span> <span data-ttu-id="9b003-180">檢閱 Reporting Services 服務追蹤記錄檔，以尋找為 UserAccountControl 屬性記錄的值。</span><span class="sxs-lookup"><span data-stu-id="9b003-180">Review the reporting services service trace log file to find the value logged for the UserAccountControl attribute.</span></span> <span data-ttu-id="9b003-181">記錄的值是十進位格式。</span><span class="sxs-lookup"><span data-stu-id="9b003-181">The value logged is in decimal form.</span></span> <span data-ttu-id="9b003-182">您需要將此十進位值轉換成十六進位格式，然後在描述 User-Account-Control 屬性的 MSDN 主題中尋找該值。</span><span class="sxs-lookup"><span data-stu-id="9b003-182">You need to convert the decimal value to hexadecimal form and then find that value in the MSDN topic describing User-Account-Control Attribute.</span></span>  
  
-   <span data-ttu-id="9b003-183">Reporting Services 服務追蹤記錄項目將會尋找類似以下的項目：</span><span class="sxs-lookup"><span data-stu-id="9b003-183">The reporting services service trace log entry will look similar to the following:</span></span>  
  
    ```  
    appdomainmanager!DefaultDomain!8f8!01/14/2010-14:42:28:: i INFO: The UserAccountControl value for the service account is 590336  
    ```  
  
-   <span data-ttu-id="9b003-184">將此十進位值轉換成十六進位格式的一個選項是使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 計算機。</span><span class="sxs-lookup"><span data-stu-id="9b003-184">One option for converting the value Decimal value to hexadecimal form is to us the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Calculator.</span></span> <span data-ttu-id="9b003-185">Windows 計算機支援可顯示 'Dec' 選項和 'Hex' 選項的幾個模式。</span><span class="sxs-lookup"><span data-stu-id="9b003-185">Windows Calculator supports several modes that show the 'Dec' option and 'Hex' options.</span></span> <span data-ttu-id="9b003-186">選取 'Dec' 選項、貼上或輸入您在記錄檔中找到的十進位值，然後選取 'Hex' 選項。</span><span class="sxs-lookup"><span data-stu-id="9b003-186">Select the 'Dec' option, paste or type in the decimal value you found in the log file and then select the 'Hex' option.</span></span>  
  
-   <span data-ttu-id="9b003-187">然後參考 [User-Account-Control Attribute](https://go.microsoft.com/fwlink/?LinkId=183366) (User-Account-Control 屬性) 主題來衍生服務帳戶的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b003-187">Then refer to the topic [User-Account-Control Attribute](https://go.microsoft.com/fwlink/?LinkId=183366) to derive the attribute for the service account.</span></span>  
  
##### <a name="spns-configured-in-active-directory-for-the-reporting-services-service-account"></a><span data-ttu-id="9b003-188">Active Directory 中針對 ssRSnoversion 服務帳戶所設定的 SPN。</span><span class="sxs-lookup"><span data-stu-id="9b003-188">SPNs Configured in Active Directory for the Reporting Services service account.</span></span>  
 <span data-ttu-id="9b003-189">若要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務追蹤記錄檔中記錄 SPN，您可以暫時啟用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 擴充保護功能。</span><span class="sxs-lookup"><span data-stu-id="9b003-189">To log the SPNs in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service trace log file, you can enable the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Extended Protection feature temporarily.</span></span>  
  
-   <span data-ttu-id="9b003-190">設定以下項目來修改組態檔 `rsreportserver.config`：</span><span class="sxs-lookup"><span data-stu-id="9b003-190">Modify the configuration file `rsreportserver.config` by setting the following:</span></span>  
  
    ```  
    <RSWindowsExtendedProtectionLevel>Allow</RSWindowsExtendedProtectionLevel>   
    <RSWindowsExtendedProtectionScenario>Any</RSWindowsExtendedProtectionScenario>  
    ```  
  
-   <span data-ttu-id="9b003-191">重新啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="9b003-191">Restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service.</span></span>

 <span data-ttu-id="9b003-192">如果您不想要繼續使用擴充保護，請將組態值設回預設值，並重新啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="9b003-192">If you do not want continue using Extended Protection, then set the configuration values back to defaults and restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service account.</span></span>  
  
```  
<RSWindowsExtendedProtectionLevel>Off</RSWindowsExtendedProtectionLevel>  
<RSWindowsExtendedProtectionScenario>Proxy</RSWindowsExtendedProtectionScenario>  
```  
  
 <span data-ttu-id="9b003-193">如需詳細資訊，請參閱[使用 Reporting Services 驗證擴充保護](extended-protection-for-authentication-with-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="9b003-193">For more information see, [Extended Protection for Authentication with Reporting Services](extended-protection-for-authentication-with-reporting-services.md)</span></span>  
  
#### <a name="how-the-browser-chooses-negotiated-kerberos-or-negotiated-ntlm"></a><span data-ttu-id="9b003-194">瀏覽器如何選擇交涉式 Kerberos 或交涉式 NTLM</span><span class="sxs-lookup"><span data-stu-id="9b003-194">How the Browser Chooses Negotiated Kerberos or Negotiated NTLM</span></span>  
 <span data-ttu-id="9b003-195">當您使用 Internet Explorer 連接報表伺服器時，它會在驗證標頭上指定交涉式 Kerberos 或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="9b003-195">When you use Internet Explorer to connect to the report server, it specifies either Negotiated Kerberos or NTLM on the authentication header.</span></span> <span data-ttu-id="9b003-196">在以下情況下會使用 NTLM 取代 Kerberos：</span><span class="sxs-lookup"><span data-stu-id="9b003-196">NTLM is used instead of Kerberos when:</span></span>  
  
-   <span data-ttu-id="9b003-197">此要求會傳送給本機報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9b003-197">The request is sent to a local report server.</span></span>  
  
-   <span data-ttu-id="9b003-198">此要求會傳送到報表伺服器電腦的 IP 位址，而不是主機標頭或伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="9b003-198">The request is sent to an IP address of the report server computer rather than a host header or server name.</span></span>  
  
-   <span data-ttu-id="9b003-199">防火牆軟體會封鎖用於 Kerberos 驗證的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="9b003-199">Firewall software blocks ports used for Kerberos authentication.</span></span>  
  
-   <span data-ttu-id="9b003-200">特定伺服器的作業系統未啟用 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="9b003-200">The operating system of a particular server does not have Kerberos enabled.</span></span>  
  
-   <span data-ttu-id="9b003-201">網域包括舊版 Windows 用戶端和伺服器作業系統，這些版本不支援內建在新版作業系統中的 Kerberos 驗證功能。</span><span class="sxs-lookup"><span data-stu-id="9b003-201">The domain includes older versions of Windows client and server operating systems that do not support the Kerberos authentication feature built into newer versions of the operating system.</span></span>  
  
 <span data-ttu-id="9b003-202">此外，Internet Explorer 可能會選擇交涉式 Kerberos 或 NTLM (根據您設定 URL、LAN 和 Proxy 設定的方式而定)。</span><span class="sxs-lookup"><span data-stu-id="9b003-202">In addition, Internet Explorer might choose either Negotiated Kerberos or NTLM depending on how you configured URL, LAN, and proxy settings.</span></span>  
  
###### <a name="report-server-url"></a><span data-ttu-id="9b003-203">報表伺服器 URL</span><span class="sxs-lookup"><span data-stu-id="9b003-203">Report Server URL</span></span>  
 <span data-ttu-id="9b003-204">如果此 URL 包含完整網域名稱，Internet Explorer 會選取 NTLM。</span><span class="sxs-lookup"><span data-stu-id="9b003-204">If the URL includes a fully qualified domain name, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="9b003-205">如果此 URL 指定 localhost，Internet Explorer 會選取 NTLM。</span><span class="sxs-lookup"><span data-stu-id="9b003-205">If the URL specifies localhost, Internet Explorer selects NTLM.</span></span> <span data-ttu-id="9b003-206">如果此 URL 指定電腦的網路名稱，Internet Explorer 會選取交涉，這樣會根據報表伺服器服務帳戶是否有 SPN 存在而成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="9b003-206">If the URL specifies the network name of the computer, Internet Explorer selects Negotiate, which will succeed or fail depending on whether an SPN exists for the Report Server service account.</span></span>  
  
###### <a name="lan-and-proxy-settings-on-the-client"></a><span data-ttu-id="9b003-207">用戶端上的 LAN 和 Proxy 設定</span><span class="sxs-lookup"><span data-stu-id="9b003-207">LAN and Proxy Settings on the Client</span></span>  
 <span data-ttu-id="9b003-208">您在 Internet Explorer 中設定的 LAN 和 Proxy 設定可以決定是否優先選擇 NTLM (勝於 Kerberos)。</span><span class="sxs-lookup"><span data-stu-id="9b003-208">LAN and proxy settings that you set in Internet Explorer can determine whether NTLM is chosen over Kerberos.</span></span> <span data-ttu-id="9b003-209">但是，由於組織之間的 LAN 和 Proxy 設定會有所差異，所以無法精確判斷造成 Kerberos 驗證錯誤的確切設定為何。</span><span class="sxs-lookup"><span data-stu-id="9b003-209">However, because LAN and proxy settings vary across organizations, it is not possible to precisely determine the exact settings that contribute to Kerberos authentication errors.</span></span> <span data-ttu-id="9b003-210">例如，您的組織可能會強制 Proxy 設定，這些設定會將 URL 從內部網路 URL 轉換成完整網域名稱 URL (透過網際網路連接來解析)。</span><span class="sxs-lookup"><span data-stu-id="9b003-210">For example, your organization might enforce proxy settings that transform URLs from intranet URLs to fully-qualified domain name URLs that resolve over Internet connections.</span></span> <span data-ttu-id="9b003-211">如果將不同的驗證提供者用於不同類型的 URL，您可能會發現當您預期某些連接應該會失敗時，這些連接卻成功了。</span><span class="sxs-lookup"><span data-stu-id="9b003-211">If different authentication providers are used for different types of URLs, you might find that some connections succeed when you would have expected them to fail.</span></span>  
  
 <span data-ttu-id="9b003-212">如果您遇到連接錯誤，而您認為這些錯誤是因為驗證失敗而發生，您可以嘗試 LAN 和 Proxy 設定的不同組合來隔離問題。</span><span class="sxs-lookup"><span data-stu-id="9b003-212">If you encounter connection errors that you think are due to authentication failures, you can try different combinations of LAN and proxy settings to isolate the problem.</span></span> <span data-ttu-id="9b003-213">在 Internet Explorer 中，LAN 和 Proxy 設定位於 [區域網路 (LAN) 設定]\*\*\*\* 對話方塊上，您可以在 [網際網路選項]\*\*\*\* 的 [連線]\*\*\*\* 索引標籤上按一下 [區域網路設定]\*\*\*\* 來開啟此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b003-213">In Internet Explorer, LAN and proxy settings are on the **Local Area Network (LAN) Settings** dialog box, which you open by clicking **LAN settings** on the **Connection** tab of **Internet Options**.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9b003-214">外部資源</span><span class="sxs-lookup"><span data-stu-id="9b003-214">External resources</span></span>  
  
-   <span data-ttu-id="9b003-215">如需 Kerberos 和報表伺服器的其他資訊，請參閱 [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos](https://go.microsoft.com/fwlink/?LinkID=177751)(搭配 Kerberos 使用 SharePoint、Reporting Services 與 PerformancePoint 監控伺服器部署商業智慧方案)。</span><span class="sxs-lookup"><span data-stu-id="9b003-215">For additional information regarding Kerberos and report servers, see [Deploying a Business Intelligence Solution Using SharePoint, Reporting Services, and PerformancePoint Monitoring Server with Kerberos.](https://go.microsoft.com/fwlink/?LinkID=177751)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b003-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b003-216">See Also</span></span>  
 <span data-ttu-id="9b003-217">[使用報表伺服器驗證](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b003-217">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="9b003-218">[在原生模式報表伺服器上授與權限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b003-218">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="9b003-219">[Rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="9b003-219">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="9b003-220">[在報表伺服器上設定基本驗證](configure-basic-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b003-220">[Configure Basic Authentication on the Report Server](configure-basic-authentication-on-the-report-server.md) </span></span>  
 <span data-ttu-id="9b003-221">[在報表伺服器上設定自訂或表單驗證](configure-custom-or-forms-authentication-on-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="9b003-221">[Configure Custom or Forms Authentication on the Report Server](configure-custom-or-forms-authentication-on-the-report-server.md) </span></span>  
 [<span data-ttu-id="9b003-222">含有 Reporting Services 的驗證擴充保護</span><span class="sxs-lookup"><span data-stu-id="9b003-222">Extended Protection for Authentication with Reporting Services</span></span>](extended-protection-for-authentication-with-reporting-services.md)  
  
  
