---
title: 設定報表伺服器上的基本驗證 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07f860a67e02c3eb29c5af4f480d3817c55c507f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593268"
---
# <a name="configure-basic-authentication-on-the-report-server"></a><span data-ttu-id="c94b5-102">設定報表伺服器的基本驗證</span><span class="sxs-lookup"><span data-stu-id="c94b5-102">Configure Basic Authentication on the Report Server</span></span>
  <span data-ttu-id="c94b5-103">根據預設，Reporting Services 會接受可指定交涉式驗證或 NTLM 驗證的要求。</span><span class="sxs-lookup"><span data-stu-id="c94b5-103">By default, Reporting Services accepts requests that specify Negotiate and NTLM authentication.</span></span> <span data-ttu-id="c94b5-104">如果您的部署包含了使用基本驗證的用戶端應用程式或瀏覽器，您必須將基本驗證加入支援的類型清單中。</span><span class="sxs-lookup"><span data-stu-id="c94b5-104">If your deployment includes client applications or browsers that use Basic authentication, you must add Basic authentication to the list of supported types.</span></span> <span data-ttu-id="c94b5-105">此外，如果您要使用報表產生器，必須啟用對報表產生器檔案的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="c94b5-105">In addition, if you want to use Report Builder, you must enable Anonymous access to the Report Builder files.</span></span>  
  
 <span data-ttu-id="c94b5-106">若要在報表伺服器上設定基本驗證，請編輯 RSReportServer.config 檔案中的 XML 元素和值。</span><span class="sxs-lookup"><span data-stu-id="c94b5-106">To configure Basic authentication on the report server, you edit XML elements and values in the RSReportServer.config file.</span></span> <span data-ttu-id="c94b5-107">您可以複製及貼上本主題的範例，以取代預設值。</span><span class="sxs-lookup"><span data-stu-id="c94b5-107">You can copy and paste the examples in this topic to replace the default values.</span></span>  
  
 <span data-ttu-id="c94b5-108">在您啟用基本驗證之前，請確認您的安全性基礎結構有支援它。</span><span class="sxs-lookup"><span data-stu-id="c94b5-108">Before you enable Basic authentication, verify that your security infrastructure supports it.</span></span> <span data-ttu-id="c94b5-109">使用基本驗證時，報表伺服器 Web 服務會將認證傳遞給本機安全性授權。</span><span class="sxs-lookup"><span data-stu-id="c94b5-109">Under Basic authentication, the Report Server Web service will pass credentials to the local security authority.</span></span> <span data-ttu-id="c94b5-110">如果認證指定本機使用者帳戶，報表伺服器電腦上的本機安全性授權將會驗證這位使用者，而此使用者將會取得對於本機資源有效的安全性 Token。</span><span class="sxs-lookup"><span data-stu-id="c94b5-110">If the credentials specify a local user account, the user is authenticated by the local security authority on the report server computer and the user will get a security token that is valid for local resources.</span></span> <span data-ttu-id="c94b5-111">網域使用者帳戶的認證會轉送給網域控制站，並由網域控制站加以驗證。</span><span class="sxs-lookup"><span data-stu-id="c94b5-111">Credentials for domain user accounts are forwarded to and authenticated by a domain controller.</span></span> <span data-ttu-id="c94b5-112">產生的票證對於網路資源而言是有效的。</span><span class="sxs-lookup"><span data-stu-id="c94b5-112">The resulting ticket is valid for network resources.</span></span>  
  
 <span data-ttu-id="c94b5-113">如果您希望在認證傳給網路中的網域控制站的過程中，能夠減低認證被攔截的風險，就需要通道加密，例如安全通訊端層 (SSL)。</span><span class="sxs-lookup"><span data-stu-id="c94b5-113">Channel encryption, such as Secure Sockets Layer (SSL), is required if you want to mitigate the risk of having credentials intercepted while in transit to a domain controller in your network.</span></span> <span data-ttu-id="c94b5-114">基本驗證本身會使用純文字格式傳輸使用者名稱，並使用 base64 編碼方式傳輸密碼。</span><span class="sxs-lookup"><span data-stu-id="c94b5-114">By itself, Basic authentication transmits the user name in clear text and the password in base-64 encoding.</span></span> <span data-ttu-id="c94b5-115">加入通道加密會讓封包無法讀取。</span><span class="sxs-lookup"><span data-stu-id="c94b5-115">Adding channel encryption makes the packet unreadable.</span></span> <span data-ttu-id="c94b5-116">如需詳細資訊，請參閱[在原生模式報表伺服器上設定 SSL 連線](configure-ssl-connections-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c94b5-116">For more information, see [Configure SSL Connections on a Native Mode Report Server](configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="c94b5-117">當您啟用基本驗證之後，請注意在使用者設定外部資料來源的連線屬性，而此資料來源會提供資料給報表時，就無法選取 [Windows 整合式安全性]  選項。</span><span class="sxs-lookup"><span data-stu-id="c94b5-117">After you enable Basic authentication, be aware that users cannot select the **Windows integrated security** option when setting connection properties to an external data source that provides data to a report.</span></span> <span data-ttu-id="c94b5-118">資料來源屬性頁上的這個選項將會呈現灰色。</span><span class="sxs-lookup"><span data-stu-id="c94b5-118">The option will be grayed out in the data source property pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c94b5-119">下列指示用於原生模式報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="c94b5-119">The following instructions are intended for a native mode report server.</span></span> <span data-ttu-id="c94b5-120">如果您在 SharePoint 整合模式下部署報表伺服器，您必須使用可指定 Windows 整合式安全性的預設驗證設定。</span><span class="sxs-lookup"><span data-stu-id="c94b5-120">If the report server is deployed in SharePoint integrated mode, you must use the default authentication settings that specify Windows integrated security.</span></span> <span data-ttu-id="c94b5-121">報表伺服器會使用預設 Windows 驗證延伸模組中的內部功能來支援 SharePoint 整合模式下的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="c94b5-121">The report server uses internal features in the default Windows Authentication extension to support report server in SharePoint integrated mode.</span></span>  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a><span data-ttu-id="c94b5-122">設定報表伺服器使用基本驗證</span><span class="sxs-lookup"><span data-stu-id="c94b5-122">To configure a report server to use Basic authentication</span></span>  
  
1.  <span data-ttu-id="c94b5-123">在文字編輯器中開啟 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="c94b5-123">Open RSReportServer.config in a text editor.</span></span>  
  
     <span data-ttu-id="c94b5-124">檔案位於\* \<drive> ：\* \Program Files\Microsoft SQL Server\MSRS12。MSSQLSERVER\Reporting Services\reportserver。</span><span class="sxs-lookup"><span data-stu-id="c94b5-124">The file is located at *\<drive>:* \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer.</span></span>  
  
2.  <span data-ttu-id="c94b5-125">尋找 <`Authentication`>。</span><span class="sxs-lookup"><span data-stu-id="c94b5-125">Find <`Authentication`>.</span></span>  
  
3.  <span data-ttu-id="c94b5-126">複製下列其中一個最符合您需要的 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="c94b5-126">Copy one of the following XML structures that best fits your needs.</span></span> <span data-ttu-id="c94b5-127">第一個 XML 結構會提供指定所有元素的預留位置，下一節會加以描述：</span><span class="sxs-lookup"><span data-stu-id="c94b5-127">The first XML structure provides placeholders for specifying all of the elements, which are described in the next section:</span></span>  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     <span data-ttu-id="c94b5-128">如果您使用預設值，可以複製最小元素結構：</span><span class="sxs-lookup"><span data-stu-id="c94b5-128">If you are using default values, you can copy the minimum element structure:</span></span>  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  <span data-ttu-id="c94b5-129">將它貼到 <> 的現有專案上 `Authentication` 。</span><span class="sxs-lookup"><span data-stu-id="c94b5-129">Paste it over the existing entries for <`Authentication`>.</span></span>  
  
     <span data-ttu-id="c94b5-130">如果您使用多個驗證類型，請只加入 `RSWindowsBasic` 元素，而不要刪除 `RSWindowsNegotiate`、`RSWindowsNTLM` 或 `RSWindowsKerberos` 的項目。</span><span class="sxs-lookup"><span data-stu-id="c94b5-130">If you are using multiple authentication types, add just the `RSWindowsBasic` element but do not delete the entries for `RSWindowsNegotiate`, `RSWindowsNTLM`, or `RSWindowsKerberos`.</span></span>  
  
     <span data-ttu-id="c94b5-131">若要支援 Safari 瀏覽器，您無法設定報表伺服器使用多個驗證類型。</span><span class="sxs-lookup"><span data-stu-id="c94b5-131">To support the Safari browser, you cannot configure the report server to use multiple authentication types.</span></span> <span data-ttu-id="c94b5-132">您只能指定 `RSWindowsBasic` 並刪除其他項目。</span><span class="sxs-lookup"><span data-stu-id="c94b5-132">You must specify only `RSWindowsBasic` and delete the other entries.</span></span>  
  
     <span data-ttu-id="c94b5-133">請注意，您無法搭配其他驗證類型使用 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-133">Note that you cannot use `Custom` with other authentication types.</span></span>  
  
5.  <span data-ttu-id="c94b5-134">以適用 `Realm` 于您環境的值取代 <> 或 <> 的空白值 `DefaultDomain` 。</span><span class="sxs-lookup"><span data-stu-id="c94b5-134">Replace empty values for <`Realm`> or <`DefaultDomain`> with values that are valid for your environment.</span></span>  
  
6.  <span data-ttu-id="c94b5-135">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c94b5-135">Save the file.</span></span>  
  
7.  <span data-ttu-id="c94b5-136">如果您設定了向外延展部署，請針對部署中的其他報表伺服器重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="c94b5-136">If you configured a scale-out deployment, repeat these steps for other report servers in the deployment.</span></span>  
  
8.  <span data-ttu-id="c94b5-137">重新啟動報表伺服器，清除目前開啟的任何工作階段。</span><span class="sxs-lookup"><span data-stu-id="c94b5-137">Restart the report server to clear any sessions that are currently open.</span></span>  
  
## <a name="rswindowsbasic-reference"></a><span data-ttu-id="c94b5-138">RSWindowsBasic 參考</span><span class="sxs-lookup"><span data-stu-id="c94b5-138">RSWindowsBasic Reference</span></span>  
 <span data-ttu-id="c94b5-139">當您設定基本驗證時，可以指定下列元素。</span><span class="sxs-lookup"><span data-stu-id="c94b5-139">The following elements can be specified when configuring Basic authentication.</span></span>  
  
|<span data-ttu-id="c94b5-140">元素</span><span class="sxs-lookup"><span data-stu-id="c94b5-140">Element</span></span>|<span data-ttu-id="c94b5-141">必要</span><span class="sxs-lookup"><span data-stu-id="c94b5-141">Required</span></span>|<span data-ttu-id="c94b5-142">有效的值</span><span class="sxs-lookup"><span data-stu-id="c94b5-142">Valid Values</span></span>|  
|-------------|--------------|------------------|  
|<span data-ttu-id="c94b5-143">LogonMethod</span><span class="sxs-lookup"><span data-stu-id="c94b5-143">LogonMethod</span></span>|<span data-ttu-id="c94b5-144">是</span><span class="sxs-lookup"><span data-stu-id="c94b5-144">Yes</span></span><br /><br /> <span data-ttu-id="c94b5-145">如果您未指定值，將會使用 3。</span><span class="sxs-lookup"><span data-stu-id="c94b5-145">If you do not specify a value, 3 will be used.</span></span>|<span data-ttu-id="c94b5-146">`2` = 網路登入，用於驗證純文字密碼的高效能伺服器。</span><span class="sxs-lookup"><span data-stu-id="c94b5-146">`2` = Network logon, intended for high performance servers to authenticate plain text passwords.</span></span><br /><br /> <span data-ttu-id="c94b5-147">`3` = 純文字登入，可將登入認證保存在隨著每個 HTTP 要求傳送的驗證封裝中，以便在連接至網路中的其他伺服器時，允許伺服器模擬使用者。</span><span class="sxs-lookup"><span data-stu-id="c94b5-147">`3` = Cleartext logon, which preserves logon credentials in the authentication package that is sent with each HTTP request, allowing the server to impersonate the user when connecting to other servers in the network.</span></span> <span data-ttu-id="c94b5-148">(預設值)</span><span class="sxs-lookup"><span data-stu-id="c94b5-148">(Default)</span></span><br /><br /> <span data-ttu-id="c94b5-149">注意:[!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 中不支援值 0 (用於互動式登入) 和 1 (用於批次登入)。</span><span class="sxs-lookup"><span data-stu-id="c94b5-149">Note: Values 0 (for interactive logon) and 1 (for batch logon) are not supported in [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>|  
|<span data-ttu-id="c94b5-150">Realm</span><span class="sxs-lookup"><span data-stu-id="c94b5-150">Realm</span></span>|<span data-ttu-id="c94b5-151">選用</span><span class="sxs-lookup"><span data-stu-id="c94b5-151">Optional</span></span>|<span data-ttu-id="c94b5-152">指定資源分割區，其中包含用於控制組織中受保護資源之存取權的授權和驗證功能。</span><span class="sxs-lookup"><span data-stu-id="c94b5-152">Specifies a resource partition that includes authorization and authentication features used to control access to protected resources in your organization.</span></span>|  
|<span data-ttu-id="c94b5-153">DefaultDomain</span><span class="sxs-lookup"><span data-stu-id="c94b5-153">DefaultDomain</span></span>|<span data-ttu-id="c94b5-154">選用</span><span class="sxs-lookup"><span data-stu-id="c94b5-154">Optional</span></span>|<span data-ttu-id="c94b5-155">指定伺服器用以驗證使用者的網域。</span><span class="sxs-lookup"><span data-stu-id="c94b5-155">Specifies the domain used by the server to authenticate the user.</span></span> <span data-ttu-id="c94b5-156">雖然這個值是選擇性的，但是如果您省略它，報表伺服器將使用電腦名稱當做網域。</span><span class="sxs-lookup"><span data-stu-id="c94b5-156">This value is optional, but if you omit it the report server will use the computer name as the domain.</span></span> <span data-ttu-id="c94b5-157">如果電腦是網域的成員，該網域就是預設網域。</span><span class="sxs-lookup"><span data-stu-id="c94b5-157">If the computer is a member of domain, that domain is the default domain.</span></span> <span data-ttu-id="c94b5-158">如果您在網域控制站上安裝了報表伺服器，則使用的網域就是電腦所控制的網域。</span><span class="sxs-lookup"><span data-stu-id="c94b5-158">If you installed the report server on a domain controller, the domain used is the one controlled by the computer.</span></span>|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a><span data-ttu-id="c94b5-159">啟用對報表產生器應用程式檔案的匿名存取</span><span class="sxs-lookup"><span data-stu-id="c94b5-159">Enabling Anonymous Access to Report Builder Application Files</span></span>  
 <span data-ttu-id="c94b5-160">報表產生器會使用 ClickOnce 技術，將應用程式檔案下載及安裝到用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="c94b5-160">Report Builder uses ClickOnce technology to download and install application files on the client computer.</span></span> <span data-ttu-id="c94b5-161">當它在用戶端電腦上啟動時，ClickOnce 應用程式啟動器將會針對報表伺服器電腦上的其他應用程式檔案發出要求。</span><span class="sxs-lookup"><span data-stu-id="c94b5-161">When it starts on the client computer, the ClickOnce application launcher will make a request for additional application files on the report server computer.</span></span> <span data-ttu-id="c94b5-162">如果報表伺服器有設定基本驗證，ClickOnce 應用程式啟動器將無法通過驗證檢查，因為它不支援基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c94b5-162">If the report server is configured for Basic authentication, the ClickOnce application launcher will fail the authentication check because it does not support Basic authentication.</span></span>  
  
 <span data-ttu-id="c94b5-163">為了解決此問題，您可以設定對報表產生器程式檔案的匿名存取。</span><span class="sxs-lookup"><span data-stu-id="c94b5-163">To work around this issue, you can configure Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="c94b5-164">這樣做會讓 ClickOnce 在擷取它的檔案時略過驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="c94b5-164">Doing so allows ClickOnce to bypass the authentication check when retrieving its files.</span></span> <span data-ttu-id="c94b5-165">若要啟用匿名存取，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c94b5-165">Enable Anonymous access by doing the following:</span></span>  
  
-   <span data-ttu-id="c94b5-166">確認報表伺服器已設定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c94b5-166">Verify that the report server is configured for Basic authentication.</span></span>  
  
-   <span data-ttu-id="c94b5-167">在 ReportBuilder 之下建立 bin 資料夾，並將四個組件複製到此資料夾。</span><span class="sxs-lookup"><span data-stu-id="c94b5-167">Create a bin folder under ReportBuilder and copy four assemblies to the folder.</span></span>  
  
-   <span data-ttu-id="c94b5-168">將 `IsReportBuilderAnonymousAccessEnabled` 元素加入到 RSReportServer.config，並將它設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-168">Add the `IsReportBuilderAnonymousAccessEnabled` element to the RSReportServer.config and set it to `True`.</span></span> <span data-ttu-id="c94b5-169">當您儲存檔案之後，報表伺服器會建立報表產生器的新端點。</span><span class="sxs-lookup"><span data-stu-id="c94b5-169">After you save the file, the report server creates a new endpoint to Report Builder.</span></span> <span data-ttu-id="c94b5-170">端點用於內部存取程式檔案，而且在程式碼內不會有可使用的程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="c94b5-170">The endpoint is used internally to access program files and does not have a programmatic interface that you can use in code.</span></span> <span data-ttu-id="c94b5-171">擁有個別的端點可讓報表產生器在報表伺服器服務處理序界限下，於它自己的應用程式定義域內執行。</span><span class="sxs-lookup"><span data-stu-id="c94b5-171">Having a separate endpoint allows Report Builder to run in its own application domain within the Report Server service process boundary.</span></span>  
  
-   <span data-ttu-id="c94b5-172">您可以選擇指定最低權限帳戶，在與報表伺服器不同的安全性內容之下處理要求。</span><span class="sxs-lookup"><span data-stu-id="c94b5-172">Optionally, you can specify a least-privilege account to process requests under a security context that is different from the report server.</span></span> <span data-ttu-id="c94b5-173">這個帳戶會變成匿名帳戶，以便在報表伺服器上存取報表產生器檔案。</span><span class="sxs-lookup"><span data-stu-id="c94b5-173">This account becomes the anonymous account for accessing Report Builder files on a report server.</span></span> <span data-ttu-id="c94b5-174">此帳戶會設定 ASP.NET 工作處理序內執行緒的識別。</span><span class="sxs-lookup"><span data-stu-id="c94b5-174">The account sets the identity of the thread in the ASP.NET worker process.</span></span> <span data-ttu-id="c94b5-175">該執行緒內執行的要求會傳遞給報表伺服器，而不需執行驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="c94b5-175">Requests that run in that thread are passed to the report server without an authentication check.</span></span> <span data-ttu-id="c94b5-176">此帳戶相當於 \<machine> Internet Information Services (IIS) 中的 IUSR_ 帳戶，這是在啟用匿名存取和模擬時，用來設定 ASP.NET 工作者進程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c94b5-176">This account is equivalent to the IUSR_\<machine> account in Internet Information Services (IIS), which is used to set the security context for ASP.NET worker processes when Anonymous access and impersonation are enabled.</span></span> <span data-ttu-id="c94b5-177">若要指定此帳戶，請將它加入報表產生器 Web.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="c94b5-177">To specify the account, you add it to a Report Builder Web.config file.</span></span>  
  
 <span data-ttu-id="c94b5-178">如果您想要啟用對報表產生器程式檔案的匿名存取，報表伺服器必須設定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c94b5-178">The report server must be configured for Basic authentication if you want to enable Anonymous access to the Report Builder program files.</span></span> <span data-ttu-id="c94b5-179">如果報表伺服器沒有設定成基本驗證，嘗試啟用匿名存取時，會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="c94b5-179">If the report server is not configured for Basic authentication, you will get an error when you attempt to enable Anonymous access.</span></span>  
  
 <span data-ttu-id="c94b5-180">如需驗證問題和報表產生器的詳細資訊，請參閱[設定報表產生器存取](../report-server/configure-report-builder-access.md)。</span><span class="sxs-lookup"><span data-stu-id="c94b5-180">For more information about authentication issues and Report Builder, see [Configure Report Builder Access](../report-server/configure-report-builder-access.md).</span></span>  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a><span data-ttu-id="c94b5-181">在有設定基本驗證的報表伺服器上設定報表產生器存取</span><span class="sxs-lookup"><span data-stu-id="c94b5-181">To configure Report Builder access on a report server configured for Basic authentication</span></span>  
  
1.  <span data-ttu-id="c94b5-182">請檢查 RSReportServer.config 檔案中的驗證設定，以確認報表伺服器有設定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c94b5-182">Verify the report server is configured for Basic authentication by checking the authentication settings in the RSReportServer.config file.</span></span>  
  
2.  <span data-ttu-id="c94b5-183">在 ReportBuilder 資料夾下建立 BIN 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c94b5-183">Create a BIN folder under the ReportBuilder folder.</span></span> <span data-ttu-id="c94b5-184">根據預設，此資料夾位於 \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder。</span><span class="sxs-lookup"><span data-stu-id="c94b5-184">By default, this folder is located at \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.</span></span>  
  
3.  <span data-ttu-id="c94b5-185">將下列組件從 ReportServer\Bin 資料夾複製到 ReportBuilder\BIN 資料夾：</span><span class="sxs-lookup"><span data-stu-id="c94b5-185">Copy the following assemblies from the ReportServer\Bin folder to the ReportBuilder\BIN folder:</span></span>  
  
     <span data-ttu-id="c94b5-186">Microsoft.ReportingServices.Diagnostics.dll</span><span class="sxs-lookup"><span data-stu-id="c94b5-186">Microsoft.ReportingServices.Diagnostics.dll</span></span>  
  
     <span data-ttu-id="c94b5-187">Microsoft.ReportingServices.Interfaces.dll</span><span class="sxs-lookup"><span data-stu-id="c94b5-187">Microsoft.ReportingServices.Interfaces.dll</span></span>  
  
     <span data-ttu-id="c94b5-188">ReportingServicesAppDomainManager.dll</span><span class="sxs-lookup"><span data-stu-id="c94b5-188">ReportingServicesAppDomainManager.dll</span></span>  
  
     <span data-ttu-id="c94b5-189">RSHttpRuntime.dll</span><span class="sxs-lookup"><span data-stu-id="c94b5-189">RSHttpRuntime.dll</span></span>  
  
4.  <span data-ttu-id="c94b5-190">您可以選擇在匿名帳戶之下，建立 Web.config 檔來處理報表產生器要求：</span><span class="sxs-lookup"><span data-stu-id="c94b5-190">Optionally, create a Web.config file to process Report Builder requests under an Anonymous account:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     <span data-ttu-id="c94b5-191">若您包含 Web.config 檔，則驗證模式必須設定為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-191">Authentication mode must be set to `Windows` if you include a Web.config file.</span></span>  
  
     <span data-ttu-id="c94b5-192">`Identity impersonate` 可以是 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-192">`Identity impersonate` can be `True` or `False`.</span></span>  
  
    -   <span data-ttu-id="c94b5-193">如果您不希望 ASP.NET 讀取安全性 Token，請將它設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-193">Set it to `False` if you do not want ASP.NET to read the security token.</span></span> <span data-ttu-id="c94b5-194">此要求將會在報表伺服器服務的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="c94b5-194">The request will run in the security context of the Report Server service.</span></span>  
  
    -   <span data-ttu-id="c94b5-195">如果您希望 ASP.NET 從主機層級讀取安全性 Token，請將它設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="c94b5-195">Set it to `True` if you want ASP.NET to read the security token from the host layer.</span></span> <span data-ttu-id="c94b5-196">如果您將它設定為 `True`，也必須指定 `userName` 和 `password` 來指派匿名帳戶。</span><span class="sxs-lookup"><span data-stu-id="c94b5-196">If you set it to `True`, you must also specify `userName` and `password` to designate an Anonymous account.</span></span> <span data-ttu-id="c94b5-197">您所指定的認證將會決定要求發出所在的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c94b5-197">The credentials you specify will determine the security context under which the request is issued.</span></span>  
  
5.  <span data-ttu-id="c94b5-198">將 Web.config 檔儲存到 ReportBuilder\bin 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c94b5-198">Save the Web.config file to the ReportBuilder\bin folder.</span></span>  
  
6.  <span data-ttu-id="c94b5-199">開啟 RSReportServer.config 檔案，並在 Services 區段中尋找 `IsReportManagerEnabled`，然後在它的下方加入以下設定：</span><span class="sxs-lookup"><span data-stu-id="c94b5-199">Open RSReportServer.config file, in the Services section, find `IsReportManagerEnabled` and add the following setting below it:</span></span>  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  <span data-ttu-id="c94b5-200">儲存 RSReportServer.config 並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="c94b5-200">Save RSReportServer.config and close the file.</span></span>  
  
8.  <span data-ttu-id="c94b5-201">重新啟動報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="c94b5-201">Restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94b5-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c94b5-202">See Also</span></span>  
 <span data-ttu-id="c94b5-203">[報表伺服器應用程式的應用程式網域](../report-server/application-domains-for-report-server-applications.md) </span><span class="sxs-lookup"><span data-stu-id="c94b5-203">[Application Domains for Report Server Applications](../report-server/application-domains-for-report-server-applications.md) </span></span>  
 [<span data-ttu-id="c94b5-204">Reporting Services 安全性與保護</span><span class="sxs-lookup"><span data-stu-id="c94b5-204">Reporting Services Security and Protection</span></span>](reporting-services-security-and-protection.md)  
  
  
