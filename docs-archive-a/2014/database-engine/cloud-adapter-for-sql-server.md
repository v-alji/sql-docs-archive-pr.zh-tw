---
title: SQL Server 的雲端配接器 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5716435bb1db494bdabeb45ed366c1783926989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597365"
---
# <a name="cloud-adapter-for-sql-server"></a><span data-ttu-id="d8bc3-102">適用 SQL Server 的雲端配接器</span><span class="sxs-lookup"><span data-stu-id="d8bc3-102">Cloud Adapter for SQL Server</span></span>
  <span data-ttu-id="d8bc3-103">在 Azure VM 上布建的過程中，會建立雲端配接器服務 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-103">The Cloud Adapter service is created as part of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provisioning on an Azure VM.</span></span> <span data-ttu-id="d8bc3-104">雲端配接器服務會在其初次執行時產生自我簽署 SSL 憑證，然後以 **本機系統** 帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-104">The Cloud Adapter service generates a self-signed SSL certificate as part of its first run, and then runs as a **Local System** account.</span></span> <span data-ttu-id="d8bc3-105">它會產生用來設定本身的組態檔。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-105">It generates a configuration file that is used to configure itself.</span></span> <span data-ttu-id="d8bc3-106">雲端配接器也會建立 Windows 防火牆規則，以允許其在預設通訊埠 11435 的傳入 TCP 連接。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-106">The Cloud Adapter also creates a Windows Firewall rule to allow its incoming TCP connections at default port 11435.</span></span>  
  
 <span data-ttu-id="d8bc3-107">雲端配接器是無狀態的同步服務，可從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的內部部署執行個體接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-107">The Cloud Adapter is a stateless, synchronous service that receives messages from the on-premise instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d8bc3-108">當雲端配接器服務停止時，它會停止遠端存取雲端配接器、將 SSL 憑證解除繫結，並且停用 Windows 防火牆規則。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-108">When the Cloud Adapter service is stopped, it stops the remote access Cloud Adapter, unbinds the SSL certificate, and disables the Windows Firewall rule.</span></span>  
  
## <a name="cloud-adapter-requirements"></a><span data-ttu-id="d8bc3-109">雲端配接器需求</span><span class="sxs-lookup"><span data-stu-id="d8bc3-109">Cloud Adapter Requirements</span></span>  
 <span data-ttu-id="d8bc3-110">請注意下列 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]適用之安裝、啟用和執行雲端配接器的需求：</span><span class="sxs-lookup"><span data-stu-id="d8bc3-110">Note the following requirements to install, enable, and run the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="d8bc3-111">雲端配接器可在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 及更高版本上支援。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-111">Cloud Adapter is supported with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 and higher.</span></span> <span data-ttu-id="d8bc3-112">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 上，適用於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的雲端配接器需要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 適用的 SQL 管理物件。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-112">On [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012, the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires SQL Management Objects for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.</span></span>  
  
-   <span data-ttu-id="d8bc3-113">雲端配接器 Web 服務會以 **本機系統** 帳戶執行，並且在執行任何工作之前驗證用戶端認證。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-113">Cloud Adapter web service runs as a **Local System** account and verifies client credentials before executing any task.</span></span> <span data-ttu-id="d8bc3-114">用戶端提供的認證必須屬於遠端電腦上本機系統**管理員**群組成員的使用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-114">Credentials supplied by the client must belong to the use account that is a member of the local **Administrators** group on the remote machine.</span></span>  
  
-   <span data-ttu-id="d8bc3-115">雲端配接器只支援 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-115">Cloud Adapter supports only [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="d8bc3-116">雲端配接器使用 VM 本機系統管理員帳戶在本機電腦上執行命令，而非 sa 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-116">Cloud Adapter uses VM local administrator account to execute commands on the local machine, not an sa account.</span></span>  
  
-   <span data-ttu-id="d8bc3-117">雲端配接器會接聽 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-117">Cloud Adapter listens on TCP/IP.</span></span> <span data-ttu-id="d8bc3-118">預設通訊埠是 11435。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-118">The default port is 11435.</span></span>  
  
-   <span data-ttu-id="d8bc3-119">雲端配接器必須具有建立及修改 Windows 防火牆規則的權限。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-119">Cloud Adapter must have permissions to create and modify Windows Firewall rules.</span></span>  
  
## <a name="cloud-adapter-configuration-settings"></a><span data-ttu-id="d8bc3-120">雲端配接器組態設定</span><span class="sxs-lookup"><span data-stu-id="d8bc3-120">Cloud Adapter Configuration Settings</span></span>  
 <span data-ttu-id="d8bc3-121">請使用下列雲端配接器組態詳細資料修改雲端配接器的設定。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-121">Use the following Cloud Adapter configuration details to modify settings for a Cloud Adapter.</span></span>  
  
-   <span data-ttu-id="d8bc3-122">**設定檔案的預設路徑**-C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter</span><span class="sxs-lookup"><span data-stu-id="d8bc3-122">**Default path for the configuration file** - C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter</span></span>\  
  
-   <span data-ttu-id="d8bc3-123">**設定檔參數** -</span><span class="sxs-lookup"><span data-stu-id="d8bc3-123">**Configuration file parameters** -</span></span>  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   <span data-ttu-id="d8bc3-124">**憑證詳細資料**-憑證具有下列值：</span><span class="sxs-lookup"><span data-stu-id="d8bc3-124">**Certificate details** - The certificate has the following values:</span></span>  
  
    -   <span data-ttu-id="d8bc3-125">Subject-"CN = CloudAdapter \<VMName> ，dc = SQL Server，dc = Microsoft"</span><span class="sxs-lookup"><span data-stu-id="d8bc3-125">Subject - "CN=CloudAdapter\<VMName>, DC=SQL Server, DC=Microsoft"</span></span>  
  
    -   <span data-ttu-id="d8bc3-126">憑證應只啟用伺服器驗證 EKU。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-126">The certificate should have only Server Authentication EKU enabled.</span></span>  
  
    -   <span data-ttu-id="d8bc3-127">憑證金鑰長度為 2048。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-127">The certificate key length is 2048.</span></span>  
  
 <span data-ttu-id="d8bc3-128">**設定檔值**：</span><span class="sxs-lookup"><span data-stu-id="d8bc3-128">**Configuration file values**:</span></span>  
  
|<span data-ttu-id="d8bc3-129">設定</span><span class="sxs-lookup"><span data-stu-id="d8bc3-129">Setting</span></span>|<span data-ttu-id="d8bc3-130">值</span><span class="sxs-lookup"><span data-stu-id="d8bc3-130">Values</span></span>|<span data-ttu-id="d8bc3-131">預設</span><span class="sxs-lookup"><span data-stu-id="d8bc3-131">Default</span></span>|<span data-ttu-id="d8bc3-132">註解</span><span class="sxs-lookup"><span data-stu-id="d8bc3-132">Comments</span></span>|  
|-------------|------------|-------------|--------------|  
|<span data-ttu-id="d8bc3-133">WebServicePort</span><span class="sxs-lookup"><span data-stu-id="d8bc3-133">WebServicePort</span></span>|<span data-ttu-id="d8bc3-134">1-65535</span><span class="sxs-lookup"><span data-stu-id="d8bc3-134">1-65535</span></span>|<span data-ttu-id="d8bc3-135">11435</span><span class="sxs-lookup"><span data-stu-id="d8bc3-135">11435</span></span>|<span data-ttu-id="d8bc3-136">若未指定，則使用 11435。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-136">If not specified, use 11435.</span></span>|  
|<span data-ttu-id="d8bc3-137">WebServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="d8bc3-137">WebServiceCertificate</span></span>|<span data-ttu-id="d8bc3-138">Thumbprint</span><span class="sxs-lookup"><span data-stu-id="d8bc3-138">Thumbprint</span></span>|<span data-ttu-id="d8bc3-139">空白</span><span class="sxs-lookup"><span data-stu-id="d8bc3-139">Empty</span></span>|<span data-ttu-id="d8bc3-140">如為空白，則會產生新的自我簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-140">If empty, a new self-signed certificate is generated.</span></span>|  
|<span data-ttu-id="d8bc3-141">ExposeExceptionDetails</span><span class="sxs-lookup"><span data-stu-id="d8bc3-141">ExposeExceptionDetails</span></span>|<span data-ttu-id="d8bc3-142">True/False</span><span class="sxs-lookup"><span data-stu-id="d8bc3-142">True/False</span></span>|<span data-ttu-id="d8bc3-143">否</span><span class="sxs-lookup"><span data-stu-id="d8bc3-143">False</span></span>||  
  
## <a name="cloud-adapter-troubleshooting"></a><span data-ttu-id="d8bc3-144">雲端配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="d8bc3-144">Cloud Adapter Troubleshooting</span></span>  
 <span data-ttu-id="d8bc3-145">請利用下列資訊對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]適用的雲端配接器進行疑難排解：</span><span class="sxs-lookup"><span data-stu-id="d8bc3-145">Use the following information to troubleshoot the Cloud Adapter for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="d8bc3-146">**錯誤處理和記錄**-錯誤和狀態訊息會寫入應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-146">**Error handling and logging** - Errors and status messages are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="d8bc3-147">**追蹤、事件**-所有事件都會寫入應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-147">**Tracing, Events** - All events are written to the Application Event Log.</span></span>  
  
-   <span data-ttu-id="d8bc3-148">**控制，** 設定-使用位於下列位置的設定檔： C:\PROGRAM Files\Microsoft SQL Server\120\Tools\CloudAdapter \\ 。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-148">**Control, configuration** - Use the configuration file located in:  C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\.</span></span>  
  
|<span data-ttu-id="d8bc3-149">錯誤</span><span class="sxs-lookup"><span data-stu-id="d8bc3-149">Error</span></span>|<span data-ttu-id="d8bc3-150">錯誤識別碼</span><span class="sxs-lookup"><span data-stu-id="d8bc3-150">Error ID</span></span>|<span data-ttu-id="d8bc3-151">原因</span><span class="sxs-lookup"><span data-stu-id="d8bc3-151">Cause</span></span>|<span data-ttu-id="d8bc3-152">解決方案</span><span class="sxs-lookup"><span data-stu-id="d8bc3-152">Resolution</span></span>|  
|-----------|--------------|-----------|----------------|  
|<span data-ttu-id="d8bc3-153">將憑證加入至憑證存放區時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-153">There was an exception while adding the certificate to the certificate store.</span></span> <span data-ttu-id="d8bc3-154">{例外狀況文字}。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-154">{Exception text}.</span></span>|<span data-ttu-id="d8bc3-155">45560</span><span class="sxs-lookup"><span data-stu-id="d8bc3-155">45560</span></span>|<span data-ttu-id="d8bc3-156">電腦憑證存放區權限。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-156">Machine certificate store permissions</span></span>|<span data-ttu-id="d8bc3-157">請確認雲端配接器服務具有將憑證加入至電腦憑證存放區的權限。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-157">Ensure that the Cloud Adapter service has permissions to add certificates to the machine certificate store.</span></span>|  
|<span data-ttu-id="d8bc3-158">嘗試設定通訊埠 {通訊埠號碼} 和憑證 {指模} 的 SSL 繫結時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-158">There was an exception while trying to configure the SSL binding for port {Port number} and certificate {Thumbprint}.</span></span> <span data-ttu-id="d8bc3-159">{例外狀況}。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-159">{Exception}.</span></span>|<span data-ttu-id="d8bc3-160">45561</span><span class="sxs-lookup"><span data-stu-id="d8bc3-160">45561</span></span>|<span data-ttu-id="d8bc3-161">其他應用程式已使用該通訊埠並將憑證繫結至該通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-161">Another application has already used the port or bound a certificate to it.</span></span>|<span data-ttu-id="d8bc3-162">請移除現有繫結，或變更組態檔中的雲端配接器通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-162">Remove existing bindings or change Cloud Adapter port in the configuration file.</span></span>|  
|<span data-ttu-id="d8bc3-163">憑證存放區中找不到 SSL 憑證 [{指模}]。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-163">Failed to find SSL certificate [{Thumbprint}] in the certificate store.</span></span>|<span data-ttu-id="d8bc3-164">45564</span><span class="sxs-lookup"><span data-stu-id="d8bc3-164">45564</span></span>|<span data-ttu-id="d8bc3-165">憑證指模位於組態檔中，但服務的個人憑證存放區未包含憑證。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-165">Certificate thumbprint is in the configuration file, but personal certificate store for the service does not contain certificate.</span></span><br /><br /> <span data-ttu-id="d8bc3-166">權限不足。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-166">Insufficient permissions.</span></span>|<span data-ttu-id="d8bc3-167">請確認憑證位於個人服務的個人憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-167">Make sure the certificate is in the personal certificate store for the service.</span></span><br /><br /> <span data-ttu-id="d8bc3-168">請確認服務具有正確的存放區權限。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-168">Make sure the service has correct permissions for the store.</span></span>|  
|<span data-ttu-id="d8bc3-169">無法啟動 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-169">Failed to start the web service.</span></span> <span data-ttu-id="d8bc3-170">{例外狀況文字}。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-170">{Exception text}.</span></span>|<span data-ttu-id="d8bc3-171">45570</span><span class="sxs-lookup"><span data-stu-id="d8bc3-171">45570</span></span>|<span data-ttu-id="d8bc3-172">於例外狀況中描述。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-172">Described in the exception.</span></span>|<span data-ttu-id="d8bc3-173">請啟用 ExposeExceptionDetails 並使用例外狀況中的擴充資訊。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-173">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
|<span data-ttu-id="d8bc3-174">憑證 [{指模}] 已過期。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-174">Certificate [{Thumbprint}] has expired.</span></span>|<span data-ttu-id="d8bc3-175">45565</span><span class="sxs-lookup"><span data-stu-id="d8bc3-175">45565</span></span>|<span data-ttu-id="d8bc3-176">從組態檔參考的憑證已過期。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-176">Expired certificate referenced from the configuration file.</span></span>|<span data-ttu-id="d8bc3-177">請加入有效的憑證，並以其指模更新組態檔。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-177">Add a valid certificate and update the configuration file with its thumbprint.</span></span>|  
|<span data-ttu-id="d8bc3-178">Web 服務錯誤： {0} 。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-178">Web service error: {0}.</span></span>|<span data-ttu-id="d8bc3-179">45571</span><span class="sxs-lookup"><span data-stu-id="d8bc3-179">45571</span></span>|<span data-ttu-id="d8bc3-180">於例外狀況中描述。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-180">Described in the exception.</span></span>|<span data-ttu-id="d8bc3-181">請啟用 ExposeExceptionDetails 並使用例外狀況中的擴充資訊。</span><span class="sxs-lookup"><span data-stu-id="d8bc3-181">Enable ExposeExceptionDetails and use extended information from the exception.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8bc3-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8bc3-182">See Also</span></span>  
 [<span data-ttu-id="d8bc3-183">將 SQL Server Database 部署到 Microsoft Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="d8bc3-183">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
