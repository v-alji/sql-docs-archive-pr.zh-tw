---
title: Advanced Multiple 網站 Configuration (SSRS 原生模式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65061eae928227f16b1088a0fb5448b19093cb1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595540"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a><span data-ttu-id="88f66-102">進階多重網站組態 (SSRS 原生模式)</span><span class="sxs-lookup"><span data-stu-id="88f66-102">Advanced Multiple Web Site Configuration (SSRS Native Mode)</span></span>
  <span data-ttu-id="88f66-103">使用此對話方塊可建立及管理用來存取報表伺服器或報表管理員的 URL。</span><span class="sxs-lookup"><span data-stu-id="88f66-103">Use this dialog box to create and manage the URLs used to access a report server or Report Manager.</span></span> <span data-ttu-id="88f66-104">**[進階多重網站組態]** 對話方塊是用來建立其他 URL (亦即包含主機標頭名稱的自訂 URL)，或是指定 IPv4 或 IPv6 格式的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="88f66-104">The **Advanced Multiple Web Site Configuration** dialog box is used to create additional URLs, custom URLs that include a host header name, or specify an IP address in the IPv4 or IPv6 format.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="88f66-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]原生模式。</span><span class="sxs-lookup"><span data-stu-id="88f66-105">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
 <span data-ttu-id="88f66-106">如果您想要設定不同的方式來存取報表伺服器，建立多個 URL 將會非常實用。</span><span class="sxs-lookup"><span data-stu-id="88f66-106">Creating multiple URLs is useful if you want to configure different ways to access a report server.</span></span> <span data-ttu-id="88f66-107">例如，透過內部網路和外部網路連接的報表伺服器存取，通常需要對每一種連接類型都有不同的 URL。</span><span class="sxs-lookup"><span data-stu-id="88f66-107">For example, report server access over intranet and extranet connection typically requires that you have different URLs for each type of connection.</span></span>  
  
 <span data-ttu-id="88f66-108">若要開啟 **[進階多重網站組態]** 對話方塊，請在 **組態管理員的** [Web 服務 URL] **或** [報表管理員 URL] **頁面上按一下** [進階] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="88f66-108">To open the **Advanced Multiple Web Site Configuration** dialog box, click **Advanced** on the **Web Service URL** or the **Report Manager URL** page in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="88f66-109">當 **[進階多重網站組態]** 對話方塊開啟之後，您可以按一下 **[加入]** 或 **[編輯]** ，以定義新的 URL 或是修改或刪除現有的 URL。</span><span class="sxs-lookup"><span data-stu-id="88f66-109">After the **Advanced Multiple Web Site Configuration** dialog box is open, you can click **Add** or **Edit** to define new URLs or modify or delete existing URLs.</span></span>  
  
 <span data-ttu-id="88f66-110">按一下 [確定]  以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="88f66-110">Click **OK** to save your changes.</span></span> <span data-ttu-id="88f66-111">如果您加入或移除 URL，然後沒有先按一下 **[確定]** 就關閉此對話方塊，您的變更將會遺失。</span><span class="sxs-lookup"><span data-stu-id="88f66-111">If you add or remove URLs, but then close the dialog box without first clicking **OK**, your changes will be lost.</span></span>  
  
## <a name="options"></a><span data-ttu-id="88f66-112">選項</span><span class="sxs-lookup"><span data-stu-id="88f66-112">Options</span></span>  
 <span data-ttu-id="88f66-113">**IP 位址**</span><span class="sxs-lookup"><span data-stu-id="88f66-113">**IP Address**</span></span>  
 <span data-ttu-id="88f66-114">識別 TCP/IP 網路上的報表伺服器電腦。</span><span class="sxs-lookup"><span data-stu-id="88f66-114">Identifies the report server computer on a TCP/IP network.</span></span> <span data-ttu-id="88f66-115">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="88f66-115">Valid values include:</span></span>  
  
-   <span data-ttu-id="88f66-116">**[全部指派]** 會指定指派給電腦的任何一個 IP 位址都可以用於指向報表伺服器應用程式的 URL。</span><span class="sxs-lookup"><span data-stu-id="88f66-116">**All Assigned** specifies that any of the IP addresses that are assigned to the computer can be used in a URL that points to a report server application.</span></span> <span data-ttu-id="88f66-117">這個值也包含易記主機名稱 (如電腦名稱)，網域名稱伺服器可將該名稱解析為指派給電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="88f66-117">This value also encompasses friendly host names (such as computer names) that can be resolved by a domain name server to an IP address that is assigned to the computer.</span></span> <span data-ttu-id="88f66-118">這是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL 的預設值。</span><span class="sxs-lookup"><span data-stu-id="88f66-118">This is the default value for a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL.</span></span>  
  
-   <span data-ttu-id="88f66-119">**[全未指派]** 會指定報表伺服器將會接受未完全符合 IP 位址或主機名稱的任何要求。</span><span class="sxs-lookup"><span data-stu-id="88f66-119">**All Unassigned** specifies that the report server will accept any request that does not have an exact match for the IP address or host name.</span></span> <span data-ttu-id="88f66-120">如果有另一個 Web 應用程式已經在使用這個值，請勿使用它。</span><span class="sxs-lookup"><span data-stu-id="88f66-120">Do not use this value if another Web application is already using it.</span></span> <span data-ttu-id="88f66-121">如果您這樣做，您將會中斷其他應用程式的服務。</span><span class="sxs-lookup"><span data-stu-id="88f66-121">If you do so, you will disrupt service for the other application.</span></span>  
  
-   <span data-ttu-id="88f66-122">**[127.0.0.1]** 是用來存取 localhost，</span><span class="sxs-lookup"><span data-stu-id="88f66-122">**127.0.0.1** is used to access to localhost.</span></span> <span data-ttu-id="88f66-123">它可支援報表伺服器電腦上的本機管理。</span><span class="sxs-lookup"><span data-stu-id="88f66-123">It supports local administration on the report server computer.</span></span> <span data-ttu-id="88f66-124">如果您只選取這個值，則只有在本機登入報表伺服器電腦的使用者才會擁有此應用程式的存取權。</span><span class="sxs-lookup"><span data-stu-id="88f66-124">If you select only this value, only users who are logged on locally to the report server computer will have access the application.</span></span>  
  
-   <span data-ttu-id="88f66-125">*Nnn.nnn.nnn.nnn* 是電腦網路卡的 IPv4 位址。</span><span class="sxs-lookup"><span data-stu-id="88f66-125">*Nnn.nnn.nnn.nnn* is the IPv4 address of a network adapter card on your computer.</span></span> <span data-ttu-id="88f66-126">如果您的網路使用 IPv6 位址，則 IP 位址會是 8 4 位元組欄位的128位值，類似下列格式： \<header> ：*nnnn： nnnn： nnnn*： nnnn。</span><span class="sxs-lookup"><span data-stu-id="88f66-126">If your network uses IPv6 addressing, the IP address will be a 128-bit value of 8 4-byte fields similar to the following format: \<header>:*nnnn:nnnn:nnnn:nnnn*.</span></span>  
  
     <span data-ttu-id="88f66-127">如果您有多張網路卡，您會看到每一張網路卡都有一個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="88f66-127">If you have multiple cards, you will see an IP address for each one.</span></span> <span data-ttu-id="88f66-128">如果您只選取這個值，它會將應用程式存取限制為只有該 IP 位址 (以及網域名稱伺服器對應至該位址的任何主機名稱)。</span><span class="sxs-lookup"><span data-stu-id="88f66-128">If you select only this value, it will limit application access to the just the IP address (and any host name that a domain name server maps to that address).</span></span> <span data-ttu-id="88f66-129">您無法使用 localhost 來存取報表伺服器，而且也不能使用安裝於報表伺服器電腦上之其他網路卡的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="88f66-129">You cannot use localhost to access a report server, and you cannot use the IP addresses of other network adapter cards that are installed on the report server computer.</span></span>  
  
 <span data-ttu-id="88f66-130">**連接埠**</span><span class="sxs-lookup"><span data-stu-id="88f66-130">**Port**</span></span>  
 <span data-ttu-id="88f66-131">指定報表伺服器用來監視要求的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="88f66-131">Specifies the port that report server monitors for requests.</span></span> <span data-ttu-id="88f66-132">通訊埠 80 是預設通訊埠。</span><span class="sxs-lookup"><span data-stu-id="88f66-132">Port 80 is the default port.</span></span> <span data-ttu-id="88f66-133">如果您使用通訊埠 80，您不需要在 URL 中包含此通訊埠。</span><span class="sxs-lookup"><span data-stu-id="88f66-133">If you use port 80, you do not have to include it in the URL.</span></span> <span data-ttu-id="88f66-134">如果您使用任何其他埠號碼，則必須一律將它包含在 URL 中 (例如， http://localhost:8181/reports) 。</span><span class="sxs-lookup"><span data-stu-id="88f66-134">If you use any other port number, you must always include it in the URL (for example, http://localhost:8181/reports).</span></span>  
  
 <span data-ttu-id="88f66-135">**主機標頭**</span><span class="sxs-lookup"><span data-stu-id="88f66-135">**Host Header**</span></span>  
 <span data-ttu-id="88f66-136">如果您已經在網域名稱伺服器上定義解析為電腦的主機標頭，您可以在設定報表伺服器存取的 URL 中指定該主機標頭。</span><span class="sxs-lookup"><span data-stu-id="88f66-136">If you already have a host header defined on a domain name server that resolves to your computer, you can specify that host header in a URL that you configure for report server access.</span></span>  
  
 <span data-ttu-id="88f66-137">主機標頭是可讓多個網站共用單一 IP 位址和通訊埠的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="88f66-137">A host header is a unique name that allows multiple Web sites to share a single IP address and port.</span></span> <span data-ttu-id="88f66-138">主機標頭名稱要比 IP 位址和通訊埠編號更容易記得和輸入。</span><span class="sxs-lookup"><span data-stu-id="88f66-138">Host header names are easier to remember and type than IP address and port numbers.</span></span> <span data-ttu-id="88f66-139">主機標頭名稱的一個範例為 www.adventure-works.com 。</span><span class="sxs-lookup"><span data-stu-id="88f66-139">An example of a host header name might be www.adventure-works.com.</span></span>  
  
 <span data-ttu-id="88f66-140">**SSL 通訊埠**</span><span class="sxs-lookup"><span data-stu-id="88f66-140">**SSL Port**</span></span>  
 <span data-ttu-id="88f66-141">為 SSL 連接指定通訊埠。</span><span class="sxs-lookup"><span data-stu-id="88f66-141">Specifies the port for SSL connections.</span></span> <span data-ttu-id="88f66-142">SSL 的預設通訊埠是 443。</span><span class="sxs-lookup"><span data-stu-id="88f66-142">The default port for SSL is 443.</span></span>  
  
 <span data-ttu-id="88f66-143">**SSL 憑證**</span><span class="sxs-lookup"><span data-stu-id="88f66-143">**SSL Certificate**</span></span>  
 <span data-ttu-id="88f66-144">指定您安裝在這部電腦上之 SSL 憑證的憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="88f66-144">Specifies the certificate name of an SSL certificate that you installed on this computer.</span></span> <span data-ttu-id="88f66-145">如果此憑證對應到萬用字元，您可以將它用於報表伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="88f66-145">If the certificate maps to a wildcard, you can use it for a report server connection.</span></span>  
  
 <span data-ttu-id="88f66-146">指定註冊憑證的完整電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="88f66-146">Specifies the fully qualified computer name for which the certificate is registered.</span></span> <span data-ttu-id="88f66-147">所指定的名稱必須與註冊的憑證名稱相同。</span><span class="sxs-lookup"><span data-stu-id="88f66-147">The name that you specify must be identical to the name for which the certificate is registered.</span></span>  
  
 <span data-ttu-id="88f66-148">您必須安裝了憑證，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="88f66-148">You must have a certificate installed to use this option.</span></span> <span data-ttu-id="88f66-149">您也必須修改 RSReportServer.config 檔案中的 UrlRoot 組態設定，使它指定註冊憑證之電腦的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="88f66-149">You must also modify the UrlRoot configuration setting in the RSReportServer.config file so that it specifies the fully qualified name of the computer for which the certificate is registered.</span></span> <span data-ttu-id="88f66-150">如需詳細資訊，請參閱《 [線上叢書》中的](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) 在原生模式報表伺服器上設定 SSL 連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="88f66-150">For more information, see [Configure SSL Connections on a Native Mode Report Server](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="88f66-151">**發給**</span><span class="sxs-lookup"><span data-stu-id="88f66-151">**Issued To**</span></span>  
 <span data-ttu-id="88f66-152">顯示建立憑證的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="88f66-152">Shows the name of the computer for which the certificate was created.</span></span>  
  
 <span data-ttu-id="88f66-153">**加入**</span><span class="sxs-lookup"><span data-stu-id="88f66-153">**Add**</span></span>  
 <span data-ttu-id="88f66-154">定義其他 URL。</span><span class="sxs-lookup"><span data-stu-id="88f66-154">Define an additional URL.</span></span>  
  
 <span data-ttu-id="88f66-155">**編輯**</span><span class="sxs-lookup"><span data-stu-id="88f66-155">**Edit**</span></span>  
 <span data-ttu-id="88f66-156">修改 URL 語法的任何部分。</span><span class="sxs-lookup"><span data-stu-id="88f66-156">Modify any part of the URL syntax.</span></span>  
  
 <span data-ttu-id="88f66-157">**移除**</span><span class="sxs-lookup"><span data-stu-id="88f66-157">**Remove**</span></span>  
 <span data-ttu-id="88f66-158">從清單中清除 URL 項目。</span><span class="sxs-lookup"><span data-stu-id="88f66-158">Clear a URL entry from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f66-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88f66-159">See Also</span></span>  
 <span data-ttu-id="88f66-160">[Reporting Services 組態管理員 &#40;原生模式&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="88f66-160">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="88f66-161">[設定 SSRS Configuration Manager &#40;的 URL&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="88f66-161">[Configure a URL  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="88f66-162">設定報表伺服器 URL &#40;SSRS 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="88f66-162">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
