---
title: Reporting Services 中的驗證 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], authentication
- forms-based authentication [Reporting Services]
- authentication [Reporting Services]
- custom authentication [Reporting Services]
ms.assetid: 103ce1f9-31d8-44bb-b540-2752e4dcf60b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59e97ba6ef849d8b4bfddfd6953c85826e351d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596527"
---
# <a name="authentication-in-reporting-services"></a><span data-ttu-id="8cb7e-102">Reporting Services 中的驗證</span><span class="sxs-lookup"><span data-stu-id="8cb7e-102">Authentication in Reporting Services</span></span>
  <span data-ttu-id="8cb7e-103">驗證是建立使用者對識別的權限之程序。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-103">Authentication is the process of establishing a user's right to an identity.</span></span> <span data-ttu-id="8cb7e-104">您可以使用許多技術來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-104">There are many techniques that you can use to authenticate a user.</span></span> <span data-ttu-id="8cb7e-105">最常見的方式是使用密碼。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-105">The most common way is to use passwords.</span></span> <span data-ttu-id="8cb7e-106">例如，當您實作表單驗證時，想要查詢使用者是否有認證 (通常是透過某個介面來要求登入名稱與密碼)，然後針對資料存放區來驗證使用者，例如資料庫資料表或是組態檔。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-106">When you implement Forms Authentication, for example, you want an implementation that queries users for credentials (usually by some interface that requests a login name and password) and then validates users against a data store, such as a database table or configuration file.</span></span> <span data-ttu-id="8cb7e-107">如果無法驗證認證，驗證程序會失敗，而且使用者將假設匿名識別。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-107">If the credentials can't be validated, the authentication process fails and the user will assume an anonymous identity.</span></span>  
  
## <a name="custom-authentication-in-reporting-services"></a><span data-ttu-id="8cb7e-108">Reporting Services 中的自訂驗證</span><span class="sxs-lookup"><span data-stu-id="8cb7e-108">Custom Authentication in Reporting Services</span></span>  
 <span data-ttu-id="8cb7e-109">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，Windows 作業系統會透過整合式安全性，或是透過使用者認證之明確接收與驗證，來處理使用者的驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-109">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Windows operating system handles the authentication of users either through integrated security or through the explicit reception and validation of user credentials.</span></span> <span data-ttu-id="8cb7e-110">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中可以開發自訂驗證，以支援其他的驗證配置。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-110">Custom authentication can be developed in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to support additional authentication schemes.</span></span> <span data-ttu-id="8cb7e-111">這是透過安全性延伸介面 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> 來達成。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-111">This is made possible through the security extension interface <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>.</span></span> <span data-ttu-id="8cb7e-112">所有的延伸模組都會針對報表伺服器所部署和使用的任何延伸模組，自 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 基底介面繼承。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-112">All extensions inherit from the <xref:Microsoft.ReportingServices.Interfaces.IExtension> base interface for any extension deployed and used by the report server.</span></span> <span data-ttu-id="8cb7e-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension> 以及 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension> 是 <xref:Microsoft.ReportingServices.Interfaces> 命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-113"><xref:Microsoft.ReportingServices.Interfaces.IExtension>, as well as <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension>, are members of the <xref:Microsoft.ReportingServices.Interfaces> namespace.</span></span>  
  
 <span data-ttu-id="8cb7e-114">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中針對報表伺服器驗證的主要方法是 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-114">The primary way to authenticate against a report server in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method.</span></span> <span data-ttu-id="8cb7e-115">Reporting Services Web 服務的這個成員，可用以將使用者認證傳遞給報告伺服器以供驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-115">This member of the Reporting Services Web service can be used to pass user credentials to a report server for validation.</span></span> <span data-ttu-id="8cb7e-116">您的基礎安全性延伸模組會執行**IAuthenticationExtension** ，其中包含您的自訂驗證程式代碼。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-116">Your underlying security extension implements **IAuthenticationExtension.LogonUser** which contains your custom authentication code.</span></span> <span data-ttu-id="8cb7e-117">在表單驗證範例中，**LogonUser** 會針對提供的認證以及資料庫中的自訂使用者存放區執行驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-117">In the Forms Authentication sample, **LogonUser**, which performs an authentication check against the supplied credentials and a custom user store in a database.</span></span> <span data-ttu-id="8cb7e-118">**LogonUser** 的實作範例看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="8cb7e-118">An example of an implementation of **LogonUser** looks like this:</span></span>  
  
```  
public bool LogonUser(string userName, string password, string authority)  
{  
   return AuthenticationUtilities.VerifyPassword(userName, password);  
}  
  
```  
  
 <span data-ttu-id="8cb7e-119">下列範例函數是用以驗證提供的認證：</span><span class="sxs-lookup"><span data-stu-id="8cb7e-119">The following sample function is used to verify the supplied credentials:</span></span>  
  
```  
  
internal static bool VerifyPassword(string suppliedUserName,  
   string suppliedPassword)  
{   
   bool passwordMatch = false;  
   // Get the salt and pwd from the database based on the user name.  
   // See "How To: Use DPAPI (Machine Store) from ASP.NET," "How To:  
   // Use DPAPI (User Store) from Enterprise Services," and "How To:  
   // Create a DPAPI Library" for more information about how to use  
   // DPAPI to securely store connection strings.  
   SqlConnection conn = new SqlConnection(  
      "Server=localhost;" +   
      "Integrated Security=SSPI;" +  
      "database=UserAccounts");  
   SqlCommand cmd = new SqlCommand("LookupUser", conn);  
   cmd.CommandType = CommandType.StoredProcedure;  
  
   SqlParameter sqlParam = cmd.Parameters.Add("@userName",  
       SqlDbType.VarChar,  
       255);  
   sqlParam.Value = suppliedUserName;  
   try  
   {  
      conn.Open();  
      SqlDataReader reader = cmd.ExecuteReader();  
      reader.Read(); // Advance to the one and only row  
      // Return output parameters from returned data stream  
      string dbPasswordHash = reader.GetString(0);  
      string salt = reader.GetString(1);  
      reader.Close();  
      // Now take the salt and the password entered by the user  
      // and concatenate them together.  
      string passwordAndSalt = String.Concat(suppliedPassword, salt);  
      // Now hash them  
      string hashedPasswordAndSalt =  
         FormsAuthentication.HashPasswordForStoringInConfigFile(  
         passwordAndSalt,  
         "SHA1");  
      // Now verify them. Returns true if they are equal.  
      passwordMatch = hashedPasswordAndSalt.Equals(dbPasswordHash);  
   }  
   catch (Exception ex)  
   {  
       throw new Exception("Exception verifying password. " +  
          ex.Message);  
   }  
   finally  
   {  
       conn.Close();  
   }  
   return passwordMatch;  
}  
```  
  
## <a name="authentication-flow"></a><span data-ttu-id="8cb7e-120">驗證流程</span><span class="sxs-lookup"><span data-stu-id="8cb7e-120">Authentication Flow</span></span>  
 <span data-ttu-id="8cb7e-121">Reporting Services Web 服務提供自訂驗證延伸模組，以允許報表管理員與報表伺服器的表單驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-121">The Reporting Services Web service provides custom authentication extensions to enable Forms Authentication by Report Manager and the report server.</span></span>  
  
 <span data-ttu-id="8cb7e-122">Reporting Services Web 服務的 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法是用以將認證提交到報表伺服器以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-122">The <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of the Reporting Services Web service is used to submit credentials to the report server for authentication.</span></span> <span data-ttu-id="8cb7e-123">Web 服務使用 HTTP 標頭，將驗證 Ticket (又稱為 Cookie) 從伺服器傳遞到用戶端，以驗證登入要求。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-123">The Web service uses HTTP headers to pass an authentication ticket (known as a "cookie") from the server to the client for validated logon requests.</span></span>  
  
 <span data-ttu-id="8cb7e-124">下圖描述當應用程式是使用報表伺服器來部署，而該報表伺服器是設定成使用自訂驗證延伸模組時，在 Web 服務中驗證使用者的方法。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-124">The following illustration depicts the method of authenticating users to the Web service when your application is deployed with a report server configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="8cb7e-125">![Reporting Services 安全性驗證流程](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services 安全性驗證流程")</span><span class="sxs-lookup"><span data-stu-id="8cb7e-125">![Reporting Services security authentication flow](../../media/rosettasecurityextensionauthenticationflow.gif "Reporting Services security authentication flow")</span></span>  
  
 <span data-ttu-id="8cb7e-126">如圖 2 所示，驗證程序如下：</span><span class="sxs-lookup"><span data-stu-id="8cb7e-126">As shown in Figure 2, the authentication process is as follows:</span></span>  
  
1.  <span data-ttu-id="8cb7e-127">用戶端應用程式會呼叫 Web 服務的 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-127">A client application calls the Web service <xref:ReportService2010.ReportingService2010.LogonUser%2A> method to authenticate a user.</span></span>  
  
2.  <span data-ttu-id="8cb7e-128">Web 服務會呼叫安全性延伸模組的 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 方法，具體來說，就是執行**IAuthenticationExtension**的類別。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-128">The Web service makes a call to the <xref:ReportService2010.ReportingService2010.LogonUser%2A> method of your security extension, specifically, the class that implements **IAuthenticationExtension**.</span></span>  
  
3.  <span data-ttu-id="8cb7e-129"><xref:ReportService2010.ReportingService2010.LogonUser%2A> 的實作會在使用者存放區或是安全性授權中，驗證使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-129">Your implementation of <xref:ReportService2010.ReportingService2010.LogonUser%2A> validates the user name and password in the user store or security authority.</span></span>  
  
4.  <span data-ttu-id="8cb7e-130">一旦成功驗證，Web 服務會為工作階段建立 Cookie 並管理它。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-130">Upon successful authentication, the Web service creates a cookie and manages it for the session.</span></span>  
  
5.  <span data-ttu-id="8cb7e-131">Web 服務會將驗證 Ticket 傳回 HTTP 標頭上的呼叫應用程式。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-131">The Web service returns the authentication ticket to the calling application on the HTTP header.</span></span>  
  
 <span data-ttu-id="8cb7e-132">當 Web 服務透過安全性延伸模組成功地驗證使用者時，它會產生用於後續要求的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-132">When the Web service successfully authenticates a user through the security extension, it generates a cookie that is used for subsequent requests.</span></span> <span data-ttu-id="8cb7e-133">在自訂安全性授權中可能無法保存 Cookie，因為報表伺服器並未擁有安全性授權。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-133">The cookie may not persist within the custom security authority because the report server does not own the security authority.</span></span> <span data-ttu-id="8cb7e-134">Cookie 會從 <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web 服務方法傳回，而且是用於後續的 Web 服務方法呼叫和 URL 存取中。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-134">The cookie is returned from the <xref:ReportService2010.ReportingService2010.LogonUser%2A> Web service method and is used in subsequent Web service method calls and in URL access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8cb7e-135">為了避免在傳輸期間破壞 Cookie，應該使用安全通訊端層 (SSL) 加密，安全地傳輸從 <xref:ReportService2010.ReportingService2010.LogonUser%2A> 傳回的驗證 Cookie。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-135">In order to avoid compromising the cookie during transmission, authentication cookies returned from <xref:ReportService2010.ReportingService2010.LogonUser%2A> should be transmitted securely using Secure Sockets Layer (SSL) encryption.</span></span>  
  
 <span data-ttu-id="8cb7e-136">當有安裝自訂安全性延伸模組時，如果您透過 URL 來存取報表伺服器，Internet Information Services (IIS) 與 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 會自動管理驗證 Ticket 的傳輸。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-136">If you access the report server through URL access when a custom security extension is installed, Internet Information Services (IIS) and [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] automatically manage the transmission of the authentication ticket.</span></span> <span data-ttu-id="8cb7e-137">如果您透過 SOAP API 存取報表伺服器，Proxy 類別的實作必須包括其他支援，以管理驗證 Ticket。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-137">If you are accessing the report server through the SOAP API, your implementation of the proxy class must include additional support for managing the authentication ticket.</span></span> <span data-ttu-id="8cb7e-138">如需有關使用 SOAP API 以及管理驗證 Ticket 的詳細資訊，請參閱「透過自訂安全性使用 Web 服務」。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-138">For more information about using the SOAP API and managing the authentication ticket, see "Using the Web Service with Custom Security."</span></span>  
  
## <a name="forms-authentication"></a><span data-ttu-id="8cb7e-139">表單驗證</span><span class="sxs-lookup"><span data-stu-id="8cb7e-139">Forms Authentication</span></span>  
 <span data-ttu-id="8cb7e-140">表單驗證是一種 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 驗證類型，它會將未驗證的使用者導向 HTML 表單。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-140">Forms Authentication is a type of [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in which an unauthenticated user is directed to an HTML form.</span></span> <span data-ttu-id="8cb7e-141">一旦使用者提供認證，系統會發出包含驗證 Ticket 的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-141">Once the user provides credentials, the system issues a cookie containing an authentication ticket.</span></span> <span data-ttu-id="8cb7e-142">對於之後的要求，系統會先檢查 Cookie 來查看報表伺服器是否已驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-142">On later requests, the system first checks the cookie to see if the user was already authenticated by the report server.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8cb7e-143">可加以擴充，以便透過 Reporting Services API 使用可用的安全性擴充性介面。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-143">can be extended to support Forms Authentication using the security extensibility interfaces available through the Reporting Services API.</span></span> <span data-ttu-id="8cb7e-144">如果您擴充 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 來使用表單驗證，請為所有與報表伺服器的通訊使用安全通訊端層 (SSL)，以防止惡意的使用者存取其他使用者的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-144">If you extend [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] to use Forms Authentication, use Secure Sockets Layer (SSL) for all communications with the report server to prevent malicious users from gaining access to another user's cookie.</span></span> <span data-ttu-id="8cb7e-145">SSL 允許用戶端和報表伺服器驗證彼此，並確保沒有其他的電腦可以讀取兩台電腦之間的通訊內容。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-145">SSL enables clients and a report server to authenticate each other and to ensure that no other computers can read the contents of communications between the two computers.</span></span> <span data-ttu-id="8cb7e-146">所有透過 SSL 連接從用戶端傳送的資料都會經過加密，因此惡意的使用者將無法攔截傳送到報表伺服器的密碼或是資料。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-146">All data sent from a client through an SSL connection is encrypted so that malicious users cannot intercept passwords or data sent to a report server.</span></span>  
  
 <span data-ttu-id="8cb7e-147">通常會實作表單驗證以支援 Windows 之外的平台其帳戶和驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-147">Forms Authentication is generally implemented to support accounts and authentication for platforms other than Windows.</span></span> <span data-ttu-id="8cb7e-148">對於要求存取報表伺服器的使用者會顯示圖形介面，而且會將提供的認證提交到安全性授權以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-148">A graphical interface is presented to a user who requests access to a report server, and the supplied credentials are submitted to a security authority for authentication.</span></span>  
  
 <span data-ttu-id="8cb7e-149">表單驗證需要該人員在場以輸入認證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-149">Forms Authentication requires that a person is present to enter credentials.</span></span> <span data-ttu-id="8cb7e-150">對於直接與 Reporting Services Web 服務通訊的自動執行應用程式，必須將表單驗證與自訂驗證配置結合。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-150">For unattended applications that communicate directly with the Reporting Services Web service, Forms Authentication must be combined with a custom authentication scheme.</span></span>  
  
 <span data-ttu-id="8cb7e-151">在下列情況下，表單驗證適用於 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="8cb7e-151">Forms Authentication is appropriate for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] when:</span></span>  
  
-   <span data-ttu-id="8cb7e-152">您需要儲存和驗證沒有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 帳戶的使用者，而且</span><span class="sxs-lookup"><span data-stu-id="8cb7e-152">You need to store and authenticate users that do not have [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows accounts, and</span></span>  
  
-   <span data-ttu-id="8cb7e-153">您需要提供自己的使用者介面表單，做為網站上兩個不同網頁之間的登入網頁。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-153">You need to provide your own user interface form as a logon page between different pages on a Web site.</span></span>  
  
 <span data-ttu-id="8cb7e-154">撰寫可支援表單驗證的自訂安全性延伸模組時，請考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="8cb7e-154">Consider the following when writing a custom security extension that supports Forms Authentication:</span></span>  
  
-   <span data-ttu-id="8cb7e-155">如果您使用表單驗證，必須在 Internet Information Services (IIS) 中的報表伺服器虛擬目錄上啟用匿名存取。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-155">If you use Forms Authentication, anonymous access must be enabled on the report server virtual directory in Internet Information Services (IIS).</span></span>  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="8cb7e-156">驗證必須設定為 Forms。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-156">authentication must be set to Forms.</span></span> <span data-ttu-id="8cb7e-157">您為報表伺服器在 Web.config 檔案中設定 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-157">You configure [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] authentication in the Web.config file for the report server.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8cb7e-158">可以使用 Windows 驗證或是自訂驗證，來驗證和授權使用者，但並不能同時使用這兩者。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-158">can authenticate and authorize users with either Windows Authentication or custom authentication, but not both.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8cb7e-159">並不支援同時使用多個安全性延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8cb7e-159">does not support simultaneous use of multiple security extensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb7e-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cb7e-160">See Also</span></span>  
 [<span data-ttu-id="8cb7e-161">實作安全性延伸模組</span><span class="sxs-lookup"><span data-stu-id="8cb7e-161">Implementing a Security Extension</span></span>](../security-extension/implementing-a-security-extension.md)  
  
  
