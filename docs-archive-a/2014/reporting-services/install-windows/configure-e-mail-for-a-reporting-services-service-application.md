---
title: " (SharePoint 2010 和 SharePoint 2013) 設定 Reporting Services 服務應用程式的電子郵件 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 628122289f8a9d83a307d70a369ab51f8f571c04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597633"
---
# <a name="configure-e-mail-for-a-reporting-services-service-application-sharepoint-2010-and-sharepoint-2013"></a><span data-ttu-id="e16f5-102">設定 Reporting Services 服務應用程式的電子郵件 (SharePoint 2010 和 SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="e16f5-102">Configure E-mail for a Reporting Services Service Application (SharePoint 2010 and SharePoint 2013)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e16f5-103">資料警示以電子郵件訊息傳送警示。</span><span class="sxs-lookup"><span data-stu-id="e16f5-103">data alerting sends alerts in e-mail messages.</span></span> <span data-ttu-id="e16f5-104">若要傳送電子郵件，您可能需要設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式，以及修改服務應用程式的電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e16f5-104">To send e-mail you may need to configure your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and you may need to modify the e-mail delivery extension for the service application.</span></span> <span data-ttu-id="e16f5-105">如果您計劃針對 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱功能使用電子郵件傳遞延伸模組，也需要電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="e16f5-105">The e-mail settings are also required if you plan to use the e-mail delivery extension for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription feature.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="e16f5-106">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 模式 &#124; sharepoint 2010 和 sharepoint 2013。</span><span class="sxs-lookup"><span data-stu-id="e16f5-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; SharePoint 2010 and SharePoint 2013.</span></span>|  
  
### <a name="to-configure-e-mail-for-the-shared-service"></a><span data-ttu-id="e16f5-107">設定共用服務的電子郵件</span><span class="sxs-lookup"><span data-stu-id="e16f5-107">To configure e-mail for the shared service</span></span>  
  
1.  <span data-ttu-id="e16f5-108">在 SharePoint 管理中心中，按一下 **[應用程式管理]**。</span><span class="sxs-lookup"><span data-stu-id="e16f5-108">In SharePoint Central Administration, click the **Application Management**.</span></span>  
  
2.  <span data-ttu-id="e16f5-109">在 **[服務應用程式]** 群組中，按一下 **[管理服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="e16f5-109">In the **Service Applications** group, click **Manage service applications**.</span></span>  
  
3.  <span data-ttu-id="e16f5-110">在 **[名稱]** 清單中，按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e16f5-110">In the **Name** list, click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
4.  <span data-ttu-id="e16f5-111">在 [管理 Reporting Services 應用程式]\*\*\*\* 頁面上，按一下 [電子郵件設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e16f5-111">Click **E-mail Settings** on the **Manage Reporting Services Application** page.</span></span>  
  
5.  <span data-ttu-id="e16f5-112">選取 **[使用 SMTP 伺服器]**。</span><span class="sxs-lookup"><span data-stu-id="e16f5-112">Select **Use SMTP server**.</span></span>  
  
6.  <span data-ttu-id="e16f5-113">在 **[外送 SMTP 伺服器]** 方塊中，輸入 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e16f5-113">In the **Outbound SMTP server** box, type the name of an SMTP server.</span></span>  
  
7.  <span data-ttu-id="e16f5-114">在 [來源位址]\*\*\*\* 方塊中，鍵入電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="e16f5-114">In the **From address** box, type an e-mail address.</span></span>  
  
     <span data-ttu-id="e16f5-115">此地址是所有警示電子郵件訊息的寄件者地址。</span><span class="sxs-lookup"><span data-stu-id="e16f5-115">This address is the sender of all alert e-mail messages.</span></span>  
  
     <span data-ttu-id="e16f5-116">在 **[來源位址]** 中指定的使用者帳戶，必須是您在設定 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的應用程式集區時，所指定的受管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="e16f5-116">The account of the user specified in **From address** must be a managed account that you specified when you configured the application pool for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="e16f5-117">如果您具有權限，您可以在 SharePoint 管理中心的 [服務帳戶] 頁面上，檢視現有受管理帳戶的清單。</span><span class="sxs-lookup"><span data-stu-id="e16f5-117">If you have permission, you can view a list of existing managed accounts on the Service Accounts page in SharePoint Central Administration.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="ntlm-authentication"></a><span data-ttu-id="e16f5-118">NTLM 驗證</span><span class="sxs-lookup"><span data-stu-id="e16f5-118">NTLM Authentication</span></span>  
  
1.  <span data-ttu-id="e16f5-119">如果您的電子郵件環境需要 NTLM 驗證，且不允許匿名存取，您需要修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的電子郵件傳遞延伸模組組態。</span><span class="sxs-lookup"><span data-stu-id="e16f5-119">If your email environment requires NTLM authentication and does not allow anonymous access, you need to modify the e-mail delivery extension configuration for your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="e16f5-120">將**SMTPAuthenticate**變更為使用值 "2"。</span><span class="sxs-lookup"><span data-stu-id="e16f5-120">Change the **SMTPAuthenticate** to use a value of "2".</span></span> <span data-ttu-id="e16f5-121">您無法從使用者介面變更此值。</span><span class="sxs-lookup"><span data-stu-id="e16f5-121">This value cannot be changed from the user interface.</span></span> <span data-ttu-id="e16f5-122">下列 PowerShell 指令碼範例會更新服務應用程式 "SSRS_TESTAPPLICATION" 之報表伺服器電子郵件傳遞延伸模組的完整設定。</span><span class="sxs-lookup"><span data-stu-id="e16f5-122">The following PowerShell script example, updates the full configuration for the report server e-mail delivery extension for the service application named "SSRS_TESTAPPLICATION".</span></span> <span data-ttu-id="e16f5-123">請注意，指令碼中列出的部分節點也可以透過使用者介面設定，例如 [寄件者] 地址。</span><span class="sxs-lookup"><span data-stu-id="e16f5-123">Note some of the nodes listed in the script can also be set from the user interface, for example the "From" address.</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION *"}  
    $emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
    $emailXml = [xml]$emailCfg
    $emailXml.SelectSingleNode("//SMTPServer").InnerText = "your email server name"  
    $emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
    $emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
    $emailXml.SelectSingleNode("//From").InnerText = "your FROM email address"  
    Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
    ```  
  
2.  <span data-ttu-id="e16f5-124">如果您需要驗證服務應用程式的名稱，請執行**get-sprsserviceapplication** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e16f5-124">If you need to verify the name of your service application, run the **Get-SPRSServiceApplication** cmdlet.</span></span>  
  
    ```powershell
    Get-SPRSServiceApplication  
    ```  
  
3.  <span data-ttu-id="e16f5-125">下列範例會傳回服務應用程式 "SSRS_TESTAPPLICATION" 的電子郵件延伸模組目前值。</span><span class="sxs-lookup"><span data-stu-id="e16f5-125">The following example will return the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION".</span></span>  
  
    ```powershell
    $app = get-sprsserviceapplication | Where {$_.name -like "SSRSTEST_APPLICATION*"}  
    Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
    ```  
  
4.  <span data-ttu-id="e16f5-126">下列範例會使用服務應用程式 "SSRS_TESTAPPLICATION" 的電子郵件延伸模組目前值，建立名為 "emailconfig.txt" 的新檔案</span><span class="sxs-lookup"><span data-stu-id="e16f5-126">The following example will create a new file named "emailconfig.txt" with the current values of the e-mail extension for the service application named "SSRS_TESTAPPLICATION"</span></span>  
  
    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -like "SSRS_TESTAPPLICATION*"}  
    Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | Select -ExpandProperty ConfigurationXml | Out-File c:\emailconfig.txt  
    ```
