---
title: 為報表伺服器註冊服務主體名稱 (SPN) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 502170f16aad66757e8f44419ccbac3017072449
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606634"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a><span data-ttu-id="8a059-102">為報表伺服器註冊服務主要名稱 (SPN)</span><span class="sxs-lookup"><span data-stu-id="8a059-102">Register a Service Principal Name (SPN) for a Report Server</span></span>
  <span data-ttu-id="8a059-103">如果您在使用 Kerberos 通訊協定進行相互驗證的網路中部署 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，當您想要將報表伺服器服務設定為以網域使用者帳戶的身分執行時，必須為此服務建立服務主要名稱 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="8a059-103">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in a network that uses the Kerberos protocol for mutual authentication, you must create a Service Principal Name (SPN) for the Report Server service if you configure it to run as a domain user account.</span></span>  
  
## <a name="about-spns"></a><span data-ttu-id="8a059-104">關於 SPN</span><span class="sxs-lookup"><span data-stu-id="8a059-104">About SPNs</span></span>  
 <span data-ttu-id="8a059-105">SPN 是使用 Kerberos 驗證之網路上某項服務的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8a059-105">An SPN is a unique identifier for a service on a network that uses Kerberos authentication.</span></span> <span data-ttu-id="8a059-106">它是由服務類別、主機名稱和通訊埠所組成。</span><span class="sxs-lookup"><span data-stu-id="8a059-106">It consists of a service class, a host name, and a port.</span></span> <span data-ttu-id="8a059-107">在使用 Kerberos 驗證的網路上，伺服器的 SPN 必須在內建的電腦帳戶 (如 NetworkService 或 LocalSystem) 或使用者帳戶下註冊。</span><span class="sxs-lookup"><span data-stu-id="8a059-107">On a network that uses Kerberos authentication, an SPN for the server must be registered under either a built-in computer account (such as NetworkService or LocalSystem) or user account.</span></span> <span data-ttu-id="8a059-108">內建帳戶會自動註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="8a059-108">SPNs are registered for built-in accounts automatically.</span></span> <span data-ttu-id="8a059-109">但是，當您在網域使用者帳戶下執行服務時，您必須針對您想要使用的帳戶手動註冊 SPN。</span><span class="sxs-lookup"><span data-stu-id="8a059-109">However, when you run a service under a domain user account, you must manually register the SPN for the account you want to use.</span></span>  
  
 <span data-ttu-id="8a059-110">若要建立 SPN，可以使用 **SetSPN** 命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="8a059-110">To create an SPN, you can use the **SetSPN** command line utility.</span></span> <span data-ttu-id="8a059-111">如需詳細資訊，請參閱下列：</span><span class="sxs-lookup"><span data-stu-id="8a059-111">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="8a059-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="8a059-112">[Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).</span></span>  
  
-   <span data-ttu-id="8a059-113">[ (spn 的服務主體名稱) SetSPN 語法 ( # A0) ](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="8a059-113">[Service Principal Names (SPNs) SetSPN Syntax (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).</span></span>  
  
 <span data-ttu-id="8a059-114">您必須是網域管理員，才能在網域控制站上執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="8a059-114">You must be a domain administrator to run the utility on the domain controller.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a059-115">語法</span><span class="sxs-lookup"><span data-stu-id="8a059-115">Syntax</span></span>  
 <span data-ttu-id="8a059-116">使用 SetSPN 公用程式來建立報表伺服器之 SPN 的命令語法如下：</span><span class="sxs-lookup"><span data-stu-id="8a059-116">The command syntax for using SetSPN utility to create an SPN for the report server resembles the following:</span></span>  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 <span data-ttu-id="8a059-117">Windows Server 上提供**SetSPN** 。</span><span class="sxs-lookup"><span data-stu-id="8a059-117">**SetSPN** is available with Windows Server.</span></span> <span data-ttu-id="8a059-118">`-s` 引數會在確認沒有重複存在之後加入 SPN。</span><span class="sxs-lookup"><span data-stu-id="8a059-118">The `-s` argument adds a SPN after validating no duplicate exists.</span></span> <span data-ttu-id="8a059-119">**注意：-s** 從 Windows Server 2008 開始已可於 Windows Server 中使用。</span><span class="sxs-lookup"><span data-stu-id="8a059-119">**NOTE:-s** is available in Windows Server starting with Windows Server 2008.</span></span>  
  
 <span data-ttu-id="8a059-120">`HTTP` 為服務類別。</span><span class="sxs-lookup"><span data-stu-id="8a059-120">`HTTP` is the service class.</span></span> <span data-ttu-id="8a059-121">報表伺服器 Web 服務會在 HTTP.SYS 中執行。</span><span class="sxs-lookup"><span data-stu-id="8a059-121">The Report Server Web service runs in HTTP.SYS.</span></span> <span data-ttu-id="8a059-122">依據產品建立適用於 HTTP 的 SPN 就是指相同電腦上在 HTTP.SYS 中執行的所有 Web 應用程式 (包括 IIS 內主控的應用程式) 都將根據網域使用者帳戶來被授與票證。</span><span class="sxs-lookup"><span data-stu-id="8a059-122">A by-product of creating an SPN for HTTP is that all Web applications on the same computer that run in HTTP.SYS (including applications hosted in IIS) will be granted tickets based on the domain user account.</span></span> <span data-ttu-id="8a059-123">如果這些服務在不同的帳戶下執行，驗證要求將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8a059-123">If those services run under a different account, the authentication requests will fail.</span></span> <span data-ttu-id="8a059-124">為了避免這個問題，請務必在相同的帳戶下設定所有要執行的 HTTP 應用程式，或是考慮為每一個應用程式建立主機標頭，然後再為每一個主機標頭建立個別的 SPN。</span><span class="sxs-lookup"><span data-stu-id="8a059-124">To avoid this problem, be sure to configure all HTTP applications to run under the same account, or consider creating host headers for each application and then creating separate SPNs for each host header.</span></span> <span data-ttu-id="8a059-125">當您設定主機標頭時，不論 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態為何，都需要進行 DNS 變更。</span><span class="sxs-lookup"><span data-stu-id="8a059-125">When you configure host headers, DNS changes are required regardless of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration.</span></span>  
  
 <span data-ttu-id="8a059-126">您為、和指定的值，會 \<*computername*> \<*domainname*> \<*port*> 識別主控報表伺服器之電腦的唯一網路位址。</span><span class="sxs-lookup"><span data-stu-id="8a059-126">The values that you specify for \<*computername*>, \<*domainname*>, and \<*port*> identify the unique network address of the computer that hosts the report server.</span></span> <span data-ttu-id="8a059-127">這個值可以是本機主機名稱或完整網域名稱 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="8a059-127">This can be a local host name or a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="8a059-128">如果您只有一個網域，而且使用通訊埠80，您可以在 \<*domainname*> \<*port*> 命令列中省略和。</span><span class="sxs-lookup"><span data-stu-id="8a059-128">If you only have one domain and are using port 80, you can omit \<*domainname*> and \<*port*> from your command line.</span></span> <span data-ttu-id="8a059-129">\<*domain-user-account*>這是用來執行報表伺服器服務以及必須註冊 SPN 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a059-129">\<*domain-user-account*> is the user account under which the Report Server service runs and for which the SPN must be registered.</span></span>  
  
## <a name="register-an-spn-for-domain-user-account"></a><span data-ttu-id="8a059-130">為網域使用者帳戶註冊 SPN</span><span class="sxs-lookup"><span data-stu-id="8a059-130">Register an SPN for Domain User Account</span></span>  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a><span data-ttu-id="8a059-131">若要以網域使用者的身分為報表伺服器服務註冊 SPN</span><span class="sxs-lookup"><span data-stu-id="8a059-131">To register an SPN for a Report Server service running as a domain user</span></span>  
  
1.  <span data-ttu-id="8a059-132">以網域使用者帳戶的身分安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，並設定要執行的報表伺服器服務。</span><span class="sxs-lookup"><span data-stu-id="8a059-132">Install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and configure the Report Server service to run as a domain user account.</span></span> <span data-ttu-id="8a059-133">請注意，要等到您完成下列步驟以後，您才能夠連接報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8a059-133">Note that users will not be able to connect to the report server until you complete the following steps.</span></span>  
  
2.  <span data-ttu-id="8a059-134">以網域管理員的身分登入網域控制站。</span><span class="sxs-lookup"><span data-stu-id="8a059-134">Log on to the domain controller as domain administrator.</span></span>  
  
3.  <span data-ttu-id="8a059-135">開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="8a059-135">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="8a059-136">複製下列命令，使用對您的網路有效的實際值來取代預留位置值：</span><span class="sxs-lookup"><span data-stu-id="8a059-136">Copy the following command, replacing placeholder values with actual values that are valid for your network:</span></span>  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     <span data-ttu-id="8a059-137">例如： `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span><span class="sxs-lookup"><span data-stu-id="8a059-137">For example: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`</span></span>  
  
5.  <span data-ttu-id="8a059-138">執行命令。</span><span class="sxs-lookup"><span data-stu-id="8a059-138">Run the command.</span></span>  
  
6.  <span data-ttu-id="8a059-139">開啟 **RsReportServer.config** 檔，並找出 `<AuthenticationTypes>` 區段。</span><span class="sxs-lookup"><span data-stu-id="8a059-139">Open the **RsReportServer.config** file and locate the `<AuthenticationTypes>` section.</span></span>  
  
7.  <span data-ttu-id="8a059-140">加入 `<RSWindowsNegotiate/>` 當做此區段的第一個項目，以便啟用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="8a059-140">Add `<RSWindowsNegotiate/>` as the first entry in this section to enable NTLM.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a059-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a059-141">See Also</span></span>  
 <span data-ttu-id="8a059-142">[&#40;SSRS Configuration Manager 設定服務帳戶&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8a059-142">[Configure a Service Account &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="8a059-143">[設定報表伺服器服務帳戶 &#40;SSRS 組態管理員&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8a059-143">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="8a059-144">管理 Reporting Services 原生模式報表伺服器</span><span class="sxs-lookup"><span data-stu-id="8a059-144">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
