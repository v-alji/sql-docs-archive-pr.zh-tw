---
title: 將 Reporting Services 設定為使用主體別名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0312d2d1fff8f854eb2ffb8d0dad2563212ee23b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707269"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="5bcfc-102">設定 Reporting Services 使用主體替代名稱</span><span class="sxs-lookup"><span data-stu-id="5bcfc-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="5bcfc-103">此主題說明如何透過修改 rsreportserver.config 檔案和使用 Netsh.exe 工具來設定 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)，以使用主體替代名稱 (SAN)。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-103">This topic explains how to configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>

||
|-|
|<span data-ttu-id="5bcfc-104">**[!INCLUDE[applies](../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 原生模式</span><span class="sxs-lookup"><span data-stu-id="5bcfc-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|

 <span data-ttu-id="5bcfc-105">這些指示適用於 Reporting Service URL 和 Web 服務 URL。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>

 <span data-ttu-id="5bcfc-106">如果要使用 SAN，必須在伺服器上註冊 SSL 憑證、必須簽署 SSL 憑證，且 SSL 憑證需有私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="5bcfc-107">您不能使用自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-107">You cannot use a self-signed certificate</span></span>

 <span data-ttu-id="5bcfc-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的 URL 可設定為使用 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-108">URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="5bcfc-109">憑證通常只有一個主體名稱，因此一個 SSL (安全通訊端層) 工作階段只允許一個 URL。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="5bcfc-110">SAN 是憑證中的一個額外欄位，它可以允許 SSL 服務接聽、對許多 URL 皆有效，並可和其他應用程式共用 SSL 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="5bcfc-111">SAN 看起來與下列類似：www.s2.com。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-111">The SAN looks something like the following: www.s2.com.</span></span>

 <span data-ttu-id="5bcfc-112">如需 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SSL 設定的詳細資訊，請參閱 [在原生模式報表伺服器上設定 SSL 連接](security/configure-ssl-connections-on-a-native-mode-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-112">For more information about SSL settings for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>

### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="5bcfc-113">設定 SSRS 以針對 Web 服務 URL 使用主體替代名稱</span><span class="sxs-lookup"><span data-stu-id="5bcfc-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>

1.  <span data-ttu-id="5bcfc-114">啟動 Reporting Services 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-114">Start Reporting Services Configuration Manager.</span></span>

     <span data-ttu-id="5bcfc-115">如需詳細資訊，請參閱 [Reporting Services 組態管理員 &#40;原生模式&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>

2.  <span data-ttu-id="5bcfc-116">在 [Web 服務 URL]\*\*\*\* 頁面中，選取 SSL 連接埠和 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>

     <span data-ttu-id="5bcfc-117">![Reporting Services 組態管理員](media/reportingservices-configurationmanager.png "Reporting Services 組態管理員")</span><span class="sxs-lookup"><span data-stu-id="5bcfc-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>

     <span data-ttu-id="5bcfc-118">組態管理員會針對通訊埠註冊 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-118">The configuration manager registers the SSL certificate for the port.</span></span>

3.  <span data-ttu-id="5bcfc-119">開啟 rsreportserver.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-119">Open the rsreportserver.config file.</span></span>

     <span data-ttu-id="5bcfc-120">對於 SSRS 原生模式，檔案的預設位置是下列資料夾。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>

    ```
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer
    ```

4.  <span data-ttu-id="5bcfc-121">複製報表伺服器 Web 服務應用程式的 URL 區段。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-121">Copy the URL section for the Report Server Web Service application.</span></span>

     <span data-ttu-id="5bcfc-122">例如，下列是原始的 URL 區段。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-122">For example, the following is the original URL section.</span></span>

    ```
        <URL>
         <UrlString>https://localhost:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

     <span data-ttu-id="5bcfc-123">下列是修改後的 URL 區段。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-123">The following is the modified URL section.</span></span>

    ```
    <URL>
         <UrlString>https://www.s1.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>
        <URL>
         <UrlString>https://www.s2.com:443</UrlString>
         <AccountSid>S-1-5-20</AccountSid>
         <AccountName>NT Authority\NetworkService</AccountName>
        </URL>

    ```

5.  <span data-ttu-id="5bcfc-124">儲存 rsreportserver.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-124">Save the rsreportserver.config file.</span></span>

6.  <span data-ttu-id="5bcfc-125">以系統管理員身分開啟命令提示字元，然後執行 Netsh.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>

    ```
    C:\windows\system32\netsh
    ```

7.  <span data-ttu-id="5bcfc-126">輸入下列命令以切換到 http 內容。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-126">Switch to the http context by typing the following.</span></span>

    ```
    Netsh>http
    ```

8.  <span data-ttu-id="5bcfc-127">輸入下列命令以顯示現有的 urlacls。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-127">Show the existing urlacls by typing the following.</span></span>

    ```
    Netsh http>show urlacl
    ```

     <span data-ttu-id="5bcfc-128">會出現類似以下的項目。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-128">An entry such as the following appears.</span></span>

    ```
    Reserved URL            : https:// www.s1.com:443/ReportServer/
        User: NT SERVICE\ReportServer
            Listen: Yes
            Delegate: No
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)
    ```

     <span data-ttu-id="5bcfc-129">urlacl是 保留之的 URL 的 DACL (任意存取控制清單)。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>

9. <span data-ttu-id="5bcfc-130">輸入以下命令以使用和現有項目相同的使用者和 SDDL 為主體替代名稱建立新項目。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>

    ```
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer  
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)

    ```

10. <span data-ttu-id="5bcfc-131">在 Reporting Services 設定管理員的 [報表伺服器狀態]  頁面中，按一下 [停止]  ，然後按一下 [啟動]  以重新啟動報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="5bcfc-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bcfc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bcfc-132">See Also</span></span>
 <span data-ttu-id="5bcfc-133">[Rsreportserver.config 設定檔](report-server/rsreportserver-config-configuration-file.md) [Reporting Services 組態管理員 &#40;原生模式&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [修改 Reporting Services 設定檔 &#40;RSreportserver.config](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)&#41;[設定報表伺服器 url &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="5bcfc-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)</span></span>


