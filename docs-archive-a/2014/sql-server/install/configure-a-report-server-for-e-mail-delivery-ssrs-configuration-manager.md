---
title: 針對 (SSRS Configuration Manager) 的電子郵件傳遞設定報表伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], distributing
- report servers [Reporting Services], e-mail delivery
- remote SMTP service [Reporting Services]
- distributing reports [Reporting Services], e-mail
- CDO
- Collaboration Data Objects
- SMTP settings [Reporting Services]
- e-mail [Reporting Services]
- sending reports
- mail [Reporting Services]
- local SMTP service [Reporting Services]
ms.assetid: b838f970-d11a-4239-b164-8d11f4581d83
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3122dbbb5debc90afa73ca0f8ab0d8e23d38a0ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597565"
---
# <a name="configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager"></a><span data-ttu-id="0f9ee-102">為電子郵件傳遞設定報表伺服器 (SSRS 組態管理員)</span><span class="sxs-lookup"><span data-stu-id="0f9ee-102">Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)</span></span>


  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="0f9ee-103">包含一個電子郵件傳遞延伸模組，讓您能夠透過電子郵件散發報表。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-103">includes an e-mail delivery extension so that you can distribute reports through e-mail.</span></span> <span data-ttu-id="0f9ee-104">根據您定義電子郵件訂閱的方式而定，傳遞可能會由通知、連結、附加檔案或內嵌報表所組成。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-104">Depending on how you define the e-mail subscription, a delivery might consist of a notification, link, attachment, or embedded report.</span></span> <span data-ttu-id="0f9ee-105">電子郵件傳遞延伸模組可搭配現有的郵件伺服器技術一起使用。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-105">The e-mail delivery extension works with your existing mail server technology.</span></span> <span data-ttu-id="0f9ee-106">郵件伺服器必須是 SMTP 伺服器或轉送器。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-106">The mail server must be an SMTP server or forwarder.</span></span> <span data-ttu-id="0f9ee-107">報表伺服器會透過作業系統提供的 Collaboration Data Objects (CDO) 程式庫 (cdosys.dll) 連接到 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-107">The report server connects to an SMTP server through Collaboration Data Objects (CDO) libraries (cdosys.dll) that are provided by the operating system.</span></span>  
  
 <span data-ttu-id="0f9ee-108">根據預設，系統並不會設定報表伺服器電子郵件傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-108">The report server e-mail delivery extension is not configured by default.</span></span> <span data-ttu-id="0f9ee-109">您必須使用 Reporting Services 組態管理員，以最低限度的方式設定此延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-109">You must use the Reporting Services Configuration Manager to minimally configure the extension.</span></span> <span data-ttu-id="0f9ee-110">若要設定進階屬性，則必須編輯 `RSReportServer.config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-110">To set advanced properties, you must edit the `RSReportServer.config` file.</span></span> <span data-ttu-id="0f9ee-111">如果您無法將報表伺服器設定為使用此延伸模組，則可以改成將報表傳遞到共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-111">If you cannot configure the report server to use this extension, you can deliver reports to a shared folder instead.</span></span> <span data-ttu-id="0f9ee-112">如需詳細資訊，請參閱＜ [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-112">For more information, see [File Share Delivery in Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md).</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="0f9ee-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式</span><span class="sxs-lookup"><span data-stu-id="0f9ee-113">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 
  
##  <a name="configuration-requirements"></a><a name="bkmk_configuration_requirements"></a><span data-ttu-id="0f9ee-114">設定需求</span><span class="sxs-lookup"><span data-stu-id="0f9ee-114">Configuration Requirements</span></span>  
  
-   <span data-ttu-id="0f9ee-115">報表伺服器電子郵件傳遞是在 Collaboration Data Objects (CDO) 上實作，並需要本機或遠端 Simple Mail Transfer Protocol (SMTP) 伺服器或 SMTP 轉送器。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-115">Report server e-mail delivery is implemented on Collaboration Data Objects (CDO) and requires a local or remote Simple Mail Transfer Protocol (SMTP) server or SMTP forwarder.</span></span> <span data-ttu-id="0f9ee-116">並非所有的 Windows 作業系統都支援 SMTP。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-116">SMTP is not supported on all Windows operating systems.</span></span> <span data-ttu-id="0f9ee-117">如果您是使用 Itanium 型版本的 Windows Server 2008，SMTP 將不受支援。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-117">If you are using the Itanium-based edition of Windows Server 2008, SMTP is not supported.</span></span> <span data-ttu-id="0f9ee-118">如需有關透過 CDO 提供之組態選項的詳細資訊，請參閱 MSDN 上的 [組態 CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) 。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-118">For more information about configuration options provided through CDO, see [Configuration CoClass](https://go.microsoft.com/fwlink/?LinkId=98237) on MSDN.</span></span>  
  
-   <span data-ttu-id="0f9ee-119">報表伺服器服務帳戶在 SMTP 伺服器上必須擁有傳送郵件的權限。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-119">The Report Server service account must have permission on the SMTP server to send mail.</span></span>  
  
-   <span data-ttu-id="0f9ee-120">電子郵件傳遞延伸模組會在電子郵件附加檔案中使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-120">The e-mail delivery extension uses UTF-8 encoding in e-mail attachments.</span></span> <span data-ttu-id="0f9ee-121">您不能修改編碼；HTML 轉譯延伸模組只支援 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-121">You cannot modify the encoding; the HTML rendering extension only supports UTF-8.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f9ee-122">預設電子郵件傳遞延伸模組不提供以數位方式，將外寄郵件訊息簽章或加密的支援。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-122">The default e-mail delivery extension does not provide support for digitally signing or encrypting outgoing mail messages.</span></span>  
  
 
  
##  <a name="configuring-a-report-server-for-local-or-remote-smtp-service"></a><a name="bkmk_configure_for_local_or_remote_SMTP"></a><span data-ttu-id="0f9ee-123">設定本機或遠端 SMTP 服務的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="0f9ee-123">Configuring a Report Server for Local or Remote SMTP Service</span></span>  
 <span data-ttu-id="0f9ee-124">您可以使用本機 SMTP 服務，或遠端 SMTP 伺服器或轉送子以支援電子郵件傳遞。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-124">You can use a local SMTP service or a remote SMTP server or forwarder to support e-mail delivery.</span></span> <span data-ttu-id="0f9ee-125">如果您擁有現有之遠端 SMTP 伺服器的存取權，應該考慮使用該存取權。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-125">If you have access to an existing remote SMTP server, you should consider using it.</span></span> <span data-ttu-id="0f9ee-126">如果沒有可用的 SMTP 伺服器，或者您隨後遇到因為電腦連接失敗造成的報表傳遞錯誤，則應該切換到使用本機 SMTP 服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-126">If there is no SMTP server available or if you subsequently encounter report delivery errors that can be attributed to computer connection failures, you should switch to using a local SMTP service.</span></span> <span data-ttu-id="0f9ee-127">此主題會進一步提供有關如何設定報表伺服器，以供本機或遠端服務的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-127">Details about how to configure a report server for local or remote service are provided further on in this topic.</span></span>  
  
  
  
##  <a name="setting-configuration-options-for-e-mail-delivery"></a><a name="bkmk_setting_email_delivery"></a><span data-ttu-id="0f9ee-128">設定電子郵件傳遞的設定選項</span><span class="sxs-lookup"><span data-stu-id="0f9ee-128">Setting Configuration Options for E-Mail Delivery</span></span>  
 <span data-ttu-id="0f9ee-129">您必須先設定提供要使用哪個 SMTP 伺服器之相關資訊的組態值，才能使用報表伺服器電子郵件傳遞。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-129">Before you can use Report Server e-mail delivery, you must set configuration values that provide information about which SMTP server to use.</span></span>  
  
 <span data-ttu-id="0f9ee-130">若要為電子郵件傳遞設定報表伺服器，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0f9ee-130">To configure a report server for e-mail delivery, do the following:</span></span>  
  
-   <span data-ttu-id="0f9ee-131">如果您只是要指定 SMTP 伺服器和一個擁有傳送電子郵件之權限的使用者帳戶，請使用 Reporting Services 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-131">Use the Reporting Services Configuration Manager if you are specifying just an SMTP server and a user account that has permission to send e-mail.</span></span> <span data-ttu-id="0f9ee-132">這些是設定報表伺服器電子郵件傳遞延伸模組時所需的最小設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-132">These are the minimum settings that are required for configuring the Report Server e-mail delivery extension.</span></span> <span data-ttu-id="0f9ee-133">如需詳細資訊，請參閱[電子郵件設定-Configuration Manager &#40;SSRS 原生模式&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)和[Reporting Services 中的電子郵件傳遞](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-133">For more information, see [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md) and [E-Mail Delivery in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="0f9ee-134">(選擇性) 請使用文字編輯器在 RSreportserver.config 檔案中指定其他設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-134">(Optionally) Use a text editor to specify additional settings in the RSreportserver.config file.</span></span> <span data-ttu-id="0f9ee-135">這個檔案包含報表伺服器電子郵件傳遞的所有組態設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-135">This file contains all of the configuration settings for Report Server e-mail delivery.</span></span> <span data-ttu-id="0f9ee-136">如果您要使用本機 SMTP 伺服器，或要設定只能對特定主機進行電子郵件傳遞的限制，則必須在這些檔案中指定其他設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-136">Specifying additional settings in these files is required if you are using a local SMTP server or if you are restricting e-mail delivery to specific hosts.</span></span> <span data-ttu-id="0f9ee-137">如需尋找和修改設定檔的詳細資訊，請參閱 SQL Server 線上叢書中的[修改 Reporting Services 設定檔 &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-137">For more information about finding and modifying configuration files, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f9ee-138">報表伺服器電子郵件設定是以 CDO 為基礎。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-138">Report server e-mail settings are based on CDO.</span></span> <span data-ttu-id="0f9ee-139">如果您想要取得有關特定設定的詳細資料，可以參考 CDO 產品文件集。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-139">If you want more detail about specific settings, you can refer to the CDO production documentation.</span></span>  
  

  
##  <a name="example-report-server-e-mail-configuration"></a><a name="bkmk_example_config_file"></a><span data-ttu-id="0f9ee-140">報表伺服器電子郵件設定範例</span><span class="sxs-lookup"><span data-stu-id="0f9ee-140">Example Report Server E-Mail Configuration</span></span>  
 <span data-ttu-id="0f9ee-141">下列範例說明遠端 SMTP 伺服器之 RSreportserver.config 檔案中的設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-141">The following example illustrates the settings in the RSreportserver.config file for a remote SMTP server.</span></span> <span data-ttu-id="0f9ee-142">若要查看有關設定描述和有效值的資訊，請參閱《 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 線上叢書》中的＜ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl線上叢書》中的＜e or the CDO product documentation.</span><span class="sxs-lookup"><span data-stu-id="0f9ee-142">To read about the setting descriptions and valid values, see [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online or the CDO product documentation.</span></span>  
  
```  
<RSEmailDPConfiguration>  
     <SMTPServer>mySMTPServer.Adventure-Works.com</SMTPServer>  
     <SMTPServerPort></SMTPServerPort>  
     <SMTPAccountName></SMTPAccountName>  
     <SMTPConnectionTimeout></SMTPConnectionTimeout>  
     <SMTPServerPickupDirectory></SMTPServerPickupDirectory>  
     <SMTPUseSSL></SMTPUseSSL>  
     <SendUsing>2</SendUsing>  
     <SMTPAuthenticate></SMTPAuthenticate>  
     <From>my-rs-email-account@Adventure-Works.com</From>  
     <EmbeddedRenderFormats>  
          <RenderingExtension>MHTML</RenderingExtension>  
     </EmbeddedRenderFormats>  
     <PrivilegedUserRenderFormats></PrivilegedUserRenderFormats>  
     <ExcludedRenderFormats>  
          <RenderingExtension>HTMLOWC</RenderingExtension>  
          <RenderingExtension>NULL</RenderingExtension>  
     </ExcludedRenderFormats>  
     <SendEmailToUserAlias>True</SendEmailToUserAlias>  
     <DefaultHostName></DefaultHostName>  
     <PermittedHosts>  
          <HostName>Adventure-Works.com</HostName>  
          <HostName>hotmail.com</HostName>  
     </PermittedHosts>  
</RSEmailDPConfiguration>  
```  
  

  
##  <a name="configuration-options-for-setting-the-to-field-in-a-message"></a><a name="bkmk_setting_TO_field"></a><span data-ttu-id="0f9ee-143">在訊息中設定 [To：] 欄位的設定選項</span><span class="sxs-lookup"><span data-stu-id="0f9ee-143">Configuration Options for Setting the To: Field in a Message</span></span>  
 <span data-ttu-id="0f9ee-144">依據 [**管理個別訂閱**] 工作所授與的許可權所建立的使用者自訂訂閱，會包含以網域使用者帳戶為基礎的預先設定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-144">User-defined subscriptions that are created according to the permissions granted by the **Manage individual subscriptions** task contain a pre-set user name that is based on the domain user account.</span></span> <span data-ttu-id="0f9ee-145">當使用者建立訂閱時，系統就會利用建立訂閱之使用者的網域使用者帳戶，自行處理 **[收件者:]** 欄位中的收件者名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-145">When the user creates the subscription, the recipient name in the **To:** field is self-addressed using the domain user account of the person creating the subscription.</span></span>  
  
 <span data-ttu-id="0f9ee-146">如果使用 SMTP 伺服器或轉送器，而伺服器或轉送器所使用的電子郵件帳戶與網域使用者帳戶不同時，則 SMTP 伺服器嘗試將報表傳遞給該使用者時便會失敗。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-146">If you are using an SMTP server or forwarder that uses e-mail accounts that are different from the domain user account, the report delivery will fail when the SMTP server tries to deliver the report to that user.</span></span>  
  
 <span data-ttu-id="0f9ee-147">若要解決這個問題，您可以修改組態，允許使用者在 **[收件者:]** 欄位中輸入名稱：</span><span class="sxs-lookup"><span data-stu-id="0f9ee-147">To workaround this issue, you can modify configuration settings that allow users to enter a name in the **To:** field:</span></span>  
  
1.  <span data-ttu-id="0f9ee-148">以文字編輯器開啟 RSReportServer.config。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-148">Open RSReportServer.config with a text editor.</span></span>  
  
2.  <span data-ttu-id="0f9ee-149">將 `SendEmailToUserAlias` 設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-149">Set `SendEmailToUserAlias` to `False`.</span></span>  
  
3.  <span data-ttu-id="0f9ee-150">將 `DefaultHostName` 設定為 SMTP 伺服器或轉送器的網域名稱系統 (DNS) 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-150">Set `DefaultHostName` to the Domain Name System (DNS) name or IP address of the SMTP server or forwarder.</span></span>  
  
4.  <span data-ttu-id="0f9ee-151">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-151">Save the file.</span></span>  
  
  
  
##  <a name="configuration-options-for-remote-smtp-service"></a><a name="bkmk_options_remote_SMTP"></a><span data-ttu-id="0f9ee-152">遠端 SMTP 服務的設定選項</span><span class="sxs-lookup"><span data-stu-id="0f9ee-152">Configuration Options for Remote SMTP Service</span></span>  
 <span data-ttu-id="0f9ee-153">報表伺服器和 SMTP 伺服器或轉寄站之間的連接，是由下列組態設定決定：</span><span class="sxs-lookup"><span data-stu-id="0f9ee-153">The connection between the report server and an SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="0f9ee-154">`SendUsing` 指定傳送訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-154">`SendUsing` specifies a method for sending messages.</span></span> <span data-ttu-id="0f9ee-155">您可以選擇網路 SMTP 服務或本機 SMTP 服務收取目錄。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-155">You can choose between a network SMTP service or a local SMTP service pickup directory.</span></span> <span data-ttu-id="0f9ee-156">若要使用遠端 SMTP 服務，必須在 RSReportServer.config 檔案中將此值設定為 **2** 。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-156">To use a remote SMTP service, this value must be set to **2** in the RSReportServer.config file.</span></span>  
  
-   <span data-ttu-id="0f9ee-157">`SMTPServer` 指定遠端 SMTP 伺服器或轉送子。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-157">`SMTPServer` specifies the remote SMTP server or forwarder.</span></span> <span data-ttu-id="0f9ee-158">如果您使用的是遠端 SMTP 伺服器或轉送子，此值為必要的。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-158">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
-   <span data-ttu-id="0f9ee-159">`From`設定出現在電子郵件訊息的 [**寄件者：** ] 行中的值。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-159">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="0f9ee-160">如果您使用的是遠端 SMTP 伺服器或轉送子，此值為必要的。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-160">This value is a required value if you are using a remote SMTP server or forwarder.</span></span>  
  
 <span data-ttu-id="0f9ee-161">用於遠端 SMTP 服務的其他值包括下列項目 (請注意，除非您要覆寫預設值，否則不需要指定這些值)。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-161">Other values that are used for remote SMTP service include the following (note that you do not need to specify these values unless you want to override the default values).</span></span>  
  
-   <span data-ttu-id="0f9ee-162">**[SMTPServerPort]** 會設定為通訊埠 25。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-162">**SMTPServerPort** is configured for port 25.</span></span>  
  
-   <span data-ttu-id="0f9ee-163">**SMTPAuthenticate** 會指定報表伺服器如何連接到遠端 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-163">**SMTPAuthenticate** specifies how the report server connects to the remote SMTP server.</span></span> <span data-ttu-id="0f9ee-164">預設值是 0 (或無驗證)。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-164">The default value is 0 (or no authentication).</span></span> <span data-ttu-id="0f9ee-165">在此情況下，連接是透過匿名存取。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-165">In this case, the connection is made through Anonymous access.</span></span> <span data-ttu-id="0f9ee-166">依照您的網域組態，報表伺服器和 SMTP 伺服器可能必須是同一網域的成員。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-166">Depending on your domain configuration, the report server and the SMTP server may need to be members of the same domain.</span></span>  
  
     <span data-ttu-id="0f9ee-167">若要傳送電子郵件至限制的通訊群組清單 (例如，只接受來自已驗證帳戶之內送訊息的通訊群組清單)，請將 **[SMTPAuthenticate]** 設定為 **[2]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-167">To send e-mail to restricted distribution lists (for example, distribution lists that accept incoming messages only from authenticated accounts), set **SMTPAuthenticate** to **2**.</span></span>  
  

  
##  <a name="configuration-options-for-local-smtp-service"></a><a name="bkmk_options_local_SMTP"></a><span data-ttu-id="0f9ee-168">本機 SMTP 服務的設定選項</span><span class="sxs-lookup"><span data-stu-id="0f9ee-168">Configuration Options for Local SMTP Service</span></span>  
 <span data-ttu-id="0f9ee-169">如果您是測試報表伺服器電子郵件傳遞或進行疑難排解，則設定本機 SMTP 服務很有用。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-169">Configuring a local SMTP service is useful if you are testing or troubleshooting report server e-mail delivery.</span></span> <span data-ttu-id="0f9ee-170">根據預設，不會啟用本機 SMTP 服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-170">The local SMTP service is not enabled by default.</span></span> <span data-ttu-id="0f9ee-171">如需如何啟用它的指示，請參閱[設定報表伺服器以進行電子郵件傳遞 (ssrs Configuration Manager) ](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)和[電子郵件設定-Configuration Manager &#40;Ssrs 原生模式&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-171">For instructions on how to enable it, see [Configure a Report Server for E-Mail Delivery (SSRS Configuration Manager)](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [E-mail Settings - Configuration Manager &#40;SSRS Native Mode&#41;](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="0f9ee-172">報表伺服器和本機 SMTP 伺服器或轉寄站之間的連接，是由下列組態設定決定：</span><span class="sxs-lookup"><span data-stu-id="0f9ee-172">The connection between the report server and a local SMTP server or forwarder is determined by the following configuration settings:</span></span>  
  
-   <span data-ttu-id="0f9ee-173">`SendUsing` 設定為 **1**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-173">`SendUsing` is set to **1**.</span></span>  
  
-   <span data-ttu-id="0f9ee-174">**[SMTPServerPickupDirectory]** 設定為本機磁碟機上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-174">**SMTPServerPickupDirectory** is set to a folder on the local drive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0f9ee-175">`SMTPServer`如果您使用的是本機 SMTP 伺服器，請確定未設定。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-175">Be sure that you do not set `SMTPServer` if you are using a local SMTP server.</span></span>  
  
-   <span data-ttu-id="0f9ee-176">`From`設定出現在電子郵件訊息的 [**寄件者：** ] 行中的值。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-176">`From` sets the value that appears in the **From:** line of an e-mail message.</span></span> <span data-ttu-id="0f9ee-177">這是必要的值。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-177">This value is required.</span></span>  
  
 
  
##  <a name="to-configure-report-server-e-mail-using-the-reporting-services-configuration-manager"></a><a name="bkmk_use_configuration_manager"></a><span data-ttu-id="0f9ee-178">若要使用 Reporting Services 組態管理員設定報表伺服器電子郵件</span><span class="sxs-lookup"><span data-stu-id="0f9ee-178">To configure report server e-mail using the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="0f9ee-179">確認報表伺服器 Windows 服務擁有 SMTP 伺服器的 `Send As` 權限。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-179">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="0f9ee-180">啟動 Reporting Services 組態管理員，並連接到報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-180">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span>  
  
3.  <span data-ttu-id="0f9ee-181">在 [電子郵件設定] 頁面上，輸入 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-181">On the Email Settings page, enter the name of the SMTP server.</span></span> <span data-ttu-id="0f9ee-182">此值可以是 IP 位址、您公司內部網路之電腦的 UNC 名稱，或是完整的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-182">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
4.  <span data-ttu-id="0f9ee-183">在 **[寄件者地址]** 中，輸入擁有從 SMTP 伺服器傳送電子郵件之權限的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-183">In **Sender Address**, enter the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
5.  <span data-ttu-id="0f9ee-184">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-184">Click **Apply**.</span></span>  
  

  
##  <a name="to-configure-a-remote-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_remote_SMTP"></a><span data-ttu-id="0f9ee-185">若要設定報表伺服器的遠端 SMTP 服務</span><span class="sxs-lookup"><span data-stu-id="0f9ee-185">To configure a remote SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="0f9ee-186">確認報表伺服器 Windows 服務擁有 SMTP 伺服器的 `Send As` 權限。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-186">Verify that the Report Server Windows service has `Send As` permissions on the SMTP server.</span></span>  
  
2.  <span data-ttu-id="0f9ee-187">在文字編輯器中開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-187">Open the RSReportServer.config file in a text editor.</span></span>  
  
3.  <span data-ttu-id="0f9ee-188">確認 <`UrlRoot`> 設定為 [報表伺服器 URL] 位址。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-188">Verify that <`UrlRoot`> is set to the report server URL address.</span></span> <span data-ttu-id="0f9ee-189">此值是在您設定報表伺服器時設定的，所以它應該已被填入。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-189">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="0f9ee-190">如果未設定此值，請輸入報表伺服器的 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-190">If it is not set, type the report server URL address.</span></span>  
  
4.  <span data-ttu-id="0f9ee-191">在 [傳遞] 區段中，尋找 <`ReportServerEmail`>。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-191">In the Delivery section, find <`ReportServerEmail`>.</span></span>  
  
5.  <span data-ttu-id="0f9ee-192">在 [<`SMTPServer`> 中，輸入 SMTP 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-192">In <`SMTPServer`>, type the name of the SMTP server.</span></span> <span data-ttu-id="0f9ee-193">此值可以是 IP 位址、您公司內部網路之電腦的 UNC 名稱，或是完整的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-193">This value can be an IP address, a UNC name of a computer on your corporate intranet, or a fully qualified domain name.</span></span>  
  
6.  <span data-ttu-id="0f9ee-194">確認 <`SendUsing`> 設定為2。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-194">Verify that <`SendUsing`> is set to 2.</span></span> <span data-ttu-id="0f9ee-195">如果將它設定為其他值，報表伺服器就不會設定為使用遠端 SMTP 服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-195">If it is set another value, the report server is not configured to use a remote SMTP service.</span></span>  
  
7.  <span data-ttu-id="0f9ee-196">在 `From` [<> 中，輸入具有從 SMTP 伺服器傳送電子郵件之許可權的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-196">In <`From`>, type the name an account that has permission to send e-mail from the SMTP server.</span></span>  
  
8.  <span data-ttu-id="0f9ee-197">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-197">Save the file.</span></span>  
  
     <span data-ttu-id="0f9ee-198">報表伺服器會自動使用新的設定；您不需要重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-198">The report server will use the new settings automatically; you do not need to restart the service.</span></span> <span data-ttu-id="0f9ee-199">您可以指定其他 SMTP 設定，來進一步設定如何將 SMTP 伺服器用於報表伺服器電子郵件傳遞。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-199">You can specify additional SMTP settings to further configure how the SMTP server is used for report server e-mail delivery.</span></span> <span data-ttu-id="0f9ee-200">如需詳細資訊，請參閱 [ssNoVersion](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) 以及 [ssNoVersion](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) 線上叢書》中的＜ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Onl線上叢書》中的＜e.</span><span class="sxs-lookup"><span data-stu-id="0f9ee-200">For more information, see [Configuring a Report Server for E-Mail Delivery](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) and [RSReportServer Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  

  
##  <a name="to-configure-a-local-smtp-service-for-the-report-server"></a><a name="bkmk_confiugre_local_SMTP"></a><span data-ttu-id="0f9ee-201">若要設定報表伺服器的本機 SMTP 服務</span><span class="sxs-lookup"><span data-stu-id="0f9ee-201">To configure a local SMTP Service for the report server</span></span>  
  
1.  <span data-ttu-id="0f9ee-202">在 [控制台] 中，按一下 **[新增或移除程式]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-202">In Control Panel, click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="0f9ee-203">按一下 **[新增/移除 Windows 元件]** 以啟動 [Windows 元件精靈]。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-203">Click **Add/Remove Windows Components** to start the Windows Component Wizard.</span></span>  
  
3.  <span data-ttu-id="0f9ee-204">選取 **[應用程式伺服器]** 並按一下 **[詳細資料]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-204">Select **Application Server** and click **Details**.</span></span>  
  
4.  <span data-ttu-id="0f9ee-205">選取 **[Internet Information Services (IIS)]** ，再按一下 **[詳細資料]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-205">Select **Internet Information Services (IIS)** and click **Details**.</span></span>  
  
5.  <span data-ttu-id="0f9ee-206">選取 **[SMTP 服務]** 核取方塊，再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-206">Select the **SMTP Service** checkbox and click **OK**.</span></span>  
  
6.  <span data-ttu-id="0f9ee-207">在 [Windows 元件精靈] 中按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-207">On the Windows Component Wizard, click **Next**.</span></span> <span data-ttu-id="0f9ee-208">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-208">Click **Finish**.</span></span>  
  
7.  <span data-ttu-id="0f9ee-209">確認 **[服務]** 主控台中有執行該服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-209">Verify that the service is running in the **Services** console.</span></span>  
  
8.  <span data-ttu-id="0f9ee-210">在文字編輯器中開啟**RSReportServer.config**檔案。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-210">Open the **RSReportServer.config** file in a text editor.</span></span>  
  
9. <span data-ttu-id="0f9ee-211">確認 `<UrlRoot>` 設定為報表伺服器的 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-211">Verify that `<UrlRoot>` is set to the report server URL address.</span></span> <span data-ttu-id="0f9ee-212">此值是在您設定報表伺服器時設定的，所以它應該已被填入。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-212">This value is set when you configure the report server and it should be filled in already.</span></span> <span data-ttu-id="0f9ee-213">如果未設定此值，請輸入報表伺服器的 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-213">If it is not set, type the report server URL address.</span></span>  
  
10. <span data-ttu-id="0f9ee-214">在 [傳遞] 區段中，尋找 `<ReportServerEmail>.`。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-214">In the Delivery section, find `<ReportServerEmail>.`</span></span>  
  
11. <span data-ttu-id="0f9ee-215">在 `<SMTPServer>`中，清除此設定的所有值，但不要刪除標記。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-215">In `<SMTPServer>`, clear any values for this setting, but do not delete the tags.</span></span>  
  
12. <span data-ttu-id="0f9ee-216">請將 `<SendUsing>` 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-216">Set `<SendUsing>` to 1.</span></span> <span data-ttu-id="0f9ee-217">如果將它設定為其他值，報表伺服器就不會設定為使用本機 SMTP 服務。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-217">If it is set another value, the report server is not configured to use a local SMTP service.</span></span>  
  
13. <span data-ttu-id="0f9ee-218">將 `<SMTPServerPickupDirectory>` 設定為本機磁碟機上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-218">Set `<SMTPServerPickupDirectory>` to a folder on the local drive.</span></span>  
  
14. <span data-ttu-id="0f9ee-219">將 `<From>` 設定為擁有從 SMTP 伺服器傳送電子郵件之權限的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-219">Set `<From>` to an account that has permission to send e-mail from the SMTP server.</span></span>  
  
15. <span data-ttu-id="0f9ee-220">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="0f9ee-220">Save the file.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="0f9ee-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f9ee-221">See Also</span></span>  
 [<span data-ttu-id="0f9ee-222">Reporting Services 組態管理員 &#40;原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="0f9ee-222">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
