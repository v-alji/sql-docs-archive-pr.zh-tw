---
title: Analysis Services PowerShell |Microsoft Docs
ms.custom: ''
ms.date: 03/11/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56af6f26c29e5c1ddb278b620b6f525c70bd1203
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593197"
---
# <a name="analysis-services-powershell"></a><span data-ttu-id="8ca50-102">Analysis Services PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ca50-102">Analysis Services PowerShell</span></span>
  [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] <span data-ttu-id="8ca50-103">包含 Analysis Services PowerShell (SQLAS) 提供者和指令程式，讓您可以使用 Windows PowerShell 來導覽、管理和查詢 Analysis Services 物件。</span><span class="sxs-lookup"><span data-stu-id="8ca50-103">includes an Analysis Services PowerShell (SQLAS) provider and cmdlets so that you can use Windows PowerShell to navigate, administer, and query Analysis Services objects.</span></span>  
  
 <span data-ttu-id="8ca50-104">Analysis Services PowerShell 是由下列項目所構成：</span><span class="sxs-lookup"><span data-stu-id="8ca50-104">Analysis Services PowerShell consists of the following:</span></span>  
  
-   <span data-ttu-id="8ca50-105">用於導覽分析管理物件 (AMO) 階層的 `SQLAS` 提供者。</span><span class="sxs-lookup"><span data-stu-id="8ca50-105">`SQLAS` provider used for navigating the Analysis Management Object (AMO) hierarchy.</span></span>  
  
-   <span data-ttu-id="8ca50-106">用於執行 MDX、DMX 或 XMLA 指令碼的 `Invoke-ASCmd` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="8ca50-106">`Invoke-ASCmd` cmdlet used for executing MDX, DMX, or XMLA script.</span></span>  
  
-   <span data-ttu-id="8ca50-107">例行作業的工作特定指令程式，例如處理、角色管理、資料分割管理、備份和還原。</span><span class="sxs-lookup"><span data-stu-id="8ca50-107">Task-specific cmdlets for routine operations, such as processing, role management, partition management, backup and restore.</span></span>  
  
## <a name="in-this-article"></a><span data-ttu-id="8ca50-108">本文內容</span><span class="sxs-lookup"><span data-stu-id="8ca50-108">In this article</span></span>  
 [<span data-ttu-id="8ca50-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="8ca50-109">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="8ca50-110">支援的 Analysis Services 版本和模式</span><span class="sxs-lookup"><span data-stu-id="8ca50-110">Supported Versions and Modes of Analysis Services</span></span>](#bkmk_vers)  
  
 [<span data-ttu-id="8ca50-111">驗證需求與安全性考量</span><span class="sxs-lookup"><span data-stu-id="8ca50-111">Authentication Requirements and Security Considerations</span></span>](#bkmk_auth)  
  
 [<span data-ttu-id="8ca50-112">Analysis Services PowerShell 工作</span><span class="sxs-lookup"><span data-stu-id="8ca50-112">Analysis Services PowerShell Tasks</span></span>](#bkmk_tasks)  

<span data-ttu-id="8ca50-113">如需語法和範例的詳細資訊，請參閱[Analysis Services PowerShell 參考](/sql/analysis-services/powershell/analysis-services-powershell-reference)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-113">For more information about syntax and examples, see [Analysis Services PowerShell Reference](/sql/analysis-services/powershell/analysis-services-powershell-reference).</span></span>

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="8ca50-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="8ca50-114">Prerequisites</span></span>  
 <span data-ttu-id="8ca50-115">您必須安裝 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="8ca50-115">Windows PowerShell 2.0 must be installed.</span></span> <span data-ttu-id="8ca50-116">此元件預設安裝在較新版的 Windows 作業系統上。</span><span class="sxs-lookup"><span data-stu-id="8ca50-116">It is installed by default on newer versions of the Windows operating systems.</span></span> <span data-ttu-id="8ca50-117">如需詳細資訊，請參閱[安裝 Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span><span class="sxs-lookup"><span data-stu-id="8ca50-117">For more information, see [Install Windows PowerShell 2.0](https://msdn.microsoft.com/library/ff637750.aspx)</span></span>

<!-- ff637750.aspx above is linked to by:  (https://go.microsoft.com/fwlink/?LinkId=227613). -->
  
 <span data-ttu-id="8ca50-118">您必須安裝包含 SQL Server PowerShell (SQLPS) 模組與用戶端程式庫的 SQL Server 功能。</span><span class="sxs-lookup"><span data-stu-id="8ca50-118">You must install a SQL Server feature that includes the SQL Server PowerShell (SQLPS) module and client libraries.</span></span> <span data-ttu-id="8ca50-119">最簡單的安裝方式是安裝 SQL Server Management Studio，其中就會自動包含 PowerShell 功能與用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="8ca50-119">The easiest way to do this is by installing SQL Server Management Studio, which includes the PowerShell feature and client libraries automatically.</span></span> <span data-ttu-id="8ca50-120">SQL Server PowerShell (SQLPS) 模組包含所有 SQL Server 功能的 PowerShell 提供者和指令程式，包括 SQLASCmdlets 模組和 SQLAS 提供者 (用於導覽 Analysis Services 物件階層)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-120">The SQL Server PowerShell (SQLPS) module contains the PowerShell providers and cmdlets for all SQL Server features, including the SQLASCmdlets module and SQLAS provider used for navigating the Analysis Services object hierarchy.</span></span>  
  
 <span data-ttu-id="8ca50-121">您必須先匯入**SQLPS**模組，才能使用 `SQLAS` 提供者和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ca50-121">You must import the **SQLPS** module before you can use the `SQLAS` provider and cmdlets.</span></span> <span data-ttu-id="8ca50-122">SQLAS 提供者是提供者的延伸模組 `SQLServer` 。</span><span class="sxs-lookup"><span data-stu-id="8ca50-122">The SQLAS provider is an extension of the `SQLServer` provider.</span></span> <span data-ttu-id="8ca50-123">匯入 SQLPS 模組的方式有許多種。</span><span class="sxs-lookup"><span data-stu-id="8ca50-123">There are several ways to import the SQLPS module.</span></span> <span data-ttu-id="8ca50-124">如需詳細資訊，請參閱 [匯入 SQLPS 模組](../../2014/database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-124">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
 <span data-ttu-id="8ca50-125">您必須啟用遠端管理和檔案共用，才能從遠端存取 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ca50-125">Remote access to an Analysis Services instance requires that you enable remote administration and file sharing.</span></span> <span data-ttu-id="8ca50-126">如需詳細資訊，請參閱本主題中的[啟用遠端系統管理](#bkmk_remote)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-126">For more information, see [Enable Remote Administration](#bkmk_remote) in this topic.</span></span>  
  
##  <a name="supported-versions-and-modes-of-analysis-services"></a><a name="bkmk_vers"></a> <span data-ttu-id="8ca50-127">Analysis Services 的支援版本和模式</span><span class="sxs-lookup"><span data-stu-id="8ca50-127">Supported Versions and Modes of Analysis Services</span></span>  
 <span data-ttu-id="8ca50-128">目前，在 Windows Server 2008 R2、Windows Server 2008 SP1 或 Windows 7 上執行的任何 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services 版本都支援 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8ca50-128">Currently, Analysis Services PowerShell is supported on any edition of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services running on Windows Server 2008 R2, Windows Server 2008 SP1, or Windows 7.</span></span>  
  
 <span data-ttu-id="8ca50-129">下表顯示不同內容中 Analysis Services PowerShell 的可用性。</span><span class="sxs-lookup"><span data-stu-id="8ca50-129">The following table shows the availability of Analysis Services PowerShell in different contexts.</span></span>  
  
|<span data-ttu-id="8ca50-130">內容</span><span class="sxs-lookup"><span data-stu-id="8ca50-130">Context</span></span>|<span data-ttu-id="8ca50-131">PowerShell 功能可用性</span><span class="sxs-lookup"><span data-stu-id="8ca50-131">PowerShell Feature Availability</span></span>|  
|-------------|-------------------------------------|  
|<span data-ttu-id="8ca50-132">多維度執行個體與資料庫</span><span class="sxs-lookup"><span data-stu-id="8ca50-132">Multidimensional instances and databases</span></span>|<span data-ttu-id="8ca50-133">支援本機和遠端管理。</span><span class="sxs-lookup"><span data-stu-id="8ca50-133">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="8ca50-134">合併資料分割需要本機連接。</span><span class="sxs-lookup"><span data-stu-id="8ca50-134">Merge-partition requires a local connection.</span></span>|  
|<span data-ttu-id="8ca50-135">表格式執行個體與資料庫</span><span class="sxs-lookup"><span data-stu-id="8ca50-135">Tabular instances and databases</span></span>|<span data-ttu-id="8ca50-136">支援本機和遠端管理。</span><span class="sxs-lookup"><span data-stu-id="8ca50-136">Supported for local and remote administration.</span></span><br /><br /> <span data-ttu-id="8ca50-137">如需詳細資訊，請參閱8月2011的 blog，瞭解如何[使用 PowerShell 管理表格式模型](https://go.microsoft.com/fwlink/?linkID=227685)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-137">For more information, see an August 2011 blog about [Manage Tabular Models Using PowerShell](https://go.microsoft.com/fwlink/?linkID=227685).</span></span>|  
|<span data-ttu-id="8ca50-138">PowerPivot for SharePoint 執行個體與資料庫</span><span class="sxs-lookup"><span data-stu-id="8ca50-138">PowerPivot for SharePoint instances and databases</span></span>|<span data-ttu-id="8ca50-139">有限支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-139">Limited support.</span></span> <span data-ttu-id="8ca50-140">您可以使用 HTTP 連接和 SQLAS 提供者來檢視執行個體與資料庫資訊。</span><span class="sxs-lookup"><span data-stu-id="8ca50-140">You can use HTTP connections and the SQLAS provider to view instance and database information.</span></span><br /><br /> <span data-ttu-id="8ca50-141">但是，不支援使用指令程式。</span><span class="sxs-lookup"><span data-stu-id="8ca50-141">However, using the cmdlets is not supported.</span></span> <span data-ttu-id="8ca50-142">您不得使用 Analysis Services PowerShell 備份與還原記憶體中 InMemory PowerPivot 資料庫，也不得加入或移除角色、處理資料，或執行任意的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8ca50-142">You must not use Analysis Services PowerShell to backup and restore in-memory PowerPivot database, nor should you add or remove roles, process data, or run arbitrary XMLA script.</span></span><br /><br /> <span data-ttu-id="8ca50-143">基於組態目的，PowerPivot for SharePoint 具有個別提供的內建 PowerShell 支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-143">For configuration purposes, PowerPivot for SharePoint has built-in PowerShell support that is provided separately.</span></span> <span data-ttu-id="8ca50-144">如需詳細資訊，請參閱[PowerPivot for SharePoint 的 PowerShell 參考](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-144">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>|  
|<span data-ttu-id="8ca50-145">本機 Cube 的原生連接</span><span class="sxs-lookup"><span data-stu-id="8ca50-145">Native connections to local cubes</span></span><br /><br /> <span data-ttu-id="8ca50-146">"Data Source = c:\backup\test.cub"</span><span class="sxs-lookup"><span data-stu-id="8ca50-146">"Data Source=c:\backup\test.cub"</span></span>|<span data-ttu-id="8ca50-147">不支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-147">Not supported.</span></span>|  
|<span data-ttu-id="8ca50-148">SharePoint 中 BI 語意模型 (.bism) 連接檔案的 HTTP 連接</span><span class="sxs-lookup"><span data-stu-id="8ca50-148">HTTP connections to BI semantic model (.bism) connection files in SharePoint</span></span><br /><br /> <span data-ttu-id="8ca50-149">「資料 http://server/shared_docs/name.bism 源 =」</span><span class="sxs-lookup"><span data-stu-id="8ca50-149">"Data Source=http://server/shared_docs/name.bism"</span></span>|<span data-ttu-id="8ca50-150">不支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-150">Not supported.</span></span>|  
|<span data-ttu-id="8ca50-151">PowerPivot 資料庫的內嵌連接</span><span class="sxs-lookup"><span data-stu-id="8ca50-151">Embedded connections to PowerPivot databases</span></span><br /><br /> <span data-ttu-id="8ca50-152">"Data Source = $Embedded $"</span><span class="sxs-lookup"><span data-stu-id="8ca50-152">"Data Source=$Embedded$"</span></span>|<span data-ttu-id="8ca50-153">不支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-153">Not supported.</span></span>|  
|<span data-ttu-id="8ca50-154">Analysis Services 預存程序中的本機伺服器內容</span><span class="sxs-lookup"><span data-stu-id="8ca50-154">Local server context in Analysis Services stored procedures</span></span><br /><br /> <span data-ttu-id="8ca50-155">"Data Source = \*"</span><span class="sxs-lookup"><span data-stu-id="8ca50-155">"Data Source=\*"</span></span>|<span data-ttu-id="8ca50-156">不支援。</span><span class="sxs-lookup"><span data-stu-id="8ca50-156">Not supported.</span></span>|  
  
##  <a name="authentication-requirements-and-security-considerations"></a><a name="bkmk_auth"></a><span data-ttu-id="8ca50-157">驗證需求和安全性考慮</span><span class="sxs-lookup"><span data-stu-id="8ca50-157">Authentication Requirements and Security Considerations</span></span>  
 <span data-ttu-id="8ca50-158">連接至 Analysis Services 時，您必須使用 Windows 使用者識別建立連接。</span><span class="sxs-lookup"><span data-stu-id="8ca50-158">When connecting to Analysis Services, you must make the connection using a Windows user identity.</span></span> <span data-ttu-id="8ca50-159">在大部分情況下，您是使用 Windows 整合式安全性建立連接，其中目前的使用者識別會設定用來執行伺服器作業的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="8ca50-159">For the most part, a connection is made using Windows integrated security, where the identity of the current user sets the security context under which server operations are performed.</span></span> <span data-ttu-id="8ca50-160">不過，當您設定 Analysis Services 的 HTTP 存取時，其他驗證方法會變成可以使用。</span><span class="sxs-lookup"><span data-stu-id="8ca50-160">However, additional authentication methods become available when you configure HTTP access to Analysis Services.</span></span> <span data-ttu-id="8ca50-161">本節說明連接類型如何決定您可以使用的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="8ca50-161">This section explains how the type of connection determines which authentication options you can use.</span></span>  
  
 <span data-ttu-id="8ca50-162">Analysis Services 連接的特性會以原生連接或 HTTP 連接來辨別。</span><span class="sxs-lookup"><span data-stu-id="8ca50-162">Connections to Analysis Services are characterized as either native connections or HTTP connections.</span></span> <span data-ttu-id="8ca50-163">原生連接是從用戶端應用程式到伺服器的直接連接。</span><span class="sxs-lookup"><span data-stu-id="8ca50-163">A native connection is a direct connection from a client application to the server.</span></span> <span data-ttu-id="8ca50-164">在 PowerShell 工作階段中，PowerShell 用戶端會使用 OLE DB Provider for Analysis Services 直接連接至 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ca50-164">In a PowerShell session, the PowerShell client uses the OLE DB provider for Analysis Services to connect directly to an Analysis Services instance.</span></span> <span data-ttu-id="8ca50-165">原生連接一律是使用 Windows 整合式安全性所建立，其中 Analysis Services PowerShell 會以目前使用者的身分執行。</span><span class="sxs-lookup"><span data-stu-id="8ca50-165">A native connection is always made using Windows integrated security, where Analysis Services PowerShell executes as the current user.</span></span> <span data-ttu-id="8ca50-166">Analysis Services 不支援模擬。</span><span class="sxs-lookup"><span data-stu-id="8ca50-166">Analysis Services does not support impersonation.</span></span> <span data-ttu-id="8ca50-167">如果您要以特定使用者的身分執行作業，則必須以該使用者的身分啟動 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="8ca50-167">If you want to perform an operation as a specific user, you must start the PowerShell session as that user.</span></span>  
  
 <span data-ttu-id="8ca50-168">HTTP 連接則是間接透過 IIS 建立，讓其他驗證選項 (例如基本驗證) 連接至 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ca50-168">HTTP connections are made indirectly through IIS, allowing for additional authentication options, such as Basic authentication, to connect to an Analysis Services instance.</span></span> <span data-ttu-id="8ca50-169">IIS 支援模擬，因此您可以提供一個連接字串，其中包含建立連接時 IIS 將用來模擬的認證。</span><span class="sxs-lookup"><span data-stu-id="8ca50-169">Because IIS supports impersonation, you can provide a connection string that includes credentials IIS will use to impersonate when making a connection.</span></span> <span data-ttu-id="8ca50-170">若要提供認證，您可以使用-Credential 參數。</span><span class="sxs-lookup"><span data-stu-id="8ca50-170">To provide credentials, you can use the -Credential parameter.</span></span>  
  
 <span data-ttu-id="8ca50-171">**在 PowerShell 中使用-Credential 參數**</span><span class="sxs-lookup"><span data-stu-id="8ca50-171">**Using the -Credential Parameter in PowerShell**</span></span>  
  
 <span data-ttu-id="8ca50-172">-Credential 參數會接受可指定使用者名稱和密碼的 PSCredential 物件。</span><span class="sxs-lookup"><span data-stu-id="8ca50-172">The -Credential parameter takes a PSCredential object that specifies a user name and password.</span></span> <span data-ttu-id="8ca50-173">在 Analysis Services PowerShell 中，-Credential 參數適用于向 Analysis Services 發出連線要求的 Cmdlet，而不是在現有連接的內容中執行的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ca50-173">In Analysis Services PowerShell, the -Credential parameter is available for cmdlets that make a connection request to Analysis Services, as opposed to cmdlets that run within the context of an existing connection.</span></span> <span data-ttu-id="8ca50-174">提出連接連接要求的指令程式包括 Invoke-ASCmd、Backup-ASDatabase 和 Restore-ASDatabase。</span><span class="sxs-lookup"><span data-stu-id="8ca50-174">Cmdlets that make a connection request include Invoke-ASCmd, Backup-ASDatabase, and Restore-ASDatabase.</span></span> <span data-ttu-id="8ca50-175">在這些 Cmdlet 中，可以使用-Credential 參數，假設符合下列準則：</span><span class="sxs-lookup"><span data-stu-id="8ca50-175">For these cmdlets, the -Credential parameter can be used, assuming the following criteria are met:</span></span>  
  
1.  <span data-ttu-id="8ca50-176">伺服器會設定成 HTTP 存取，也就是說，IIS 會處理連接、讀取使用者名稱和密碼，並在連接到 Analysis Services 時模擬該使用者識別。</span><span class="sxs-lookup"><span data-stu-id="8ca50-176">The server is configured for HTTP access, which means that IIS handles the connection, reads the user name and password, and impersonates that user identity when connecting to Analysis Services.</span></span> <span data-ttu-id="8ca50-177">如需詳細資訊，請參閱 [設定 Internet Information Services &#40;IIS&#41; 8.0 上 Analysis Services 的 HTTP 存取](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)(Microsoft BI 驗證及識別委派)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-177">For more information, see [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md).</span></span>  
  
2.  <span data-ttu-id="8ca50-178">針對 Analysis Services HTTP 存取建立的 IIS 虛擬目錄會設定成基本驗證。</span><span class="sxs-lookup"><span data-stu-id="8ca50-178">The IIS virtual directory that was created for Analysis Services HTTP access is configured for Basic authentication.</span></span>  
  
3.  <span data-ttu-id="8ca50-179">認證物件所提供的使用者名稱和密碼會解析 Windows 使用者識別。</span><span class="sxs-lookup"><span data-stu-id="8ca50-179">The user name and password provided by the credential object resolves to a Windows user identity.</span></span> <span data-ttu-id="8ca50-180">Analysis Services 會以目前使用者的身分使用此識別。</span><span class="sxs-lookup"><span data-stu-id="8ca50-180">Analysis Services uses this identity as the current user.</span></span> <span data-ttu-id="8ca50-181">如果使用者不是 Windows 使用者，或缺少執行所要求之作業的足夠權限，則要求將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ca50-181">If the user is not a Windows user, or lacks sufficient permissions to perform the requested operation, the request will fail.</span></span>  
  
 <span data-ttu-id="8ca50-182">若要建立認證物件，您可以使用 Get-Credential 指令程式，向操作員收集認證。</span><span class="sxs-lookup"><span data-stu-id="8ca50-182">To create a credential object, you can use the Get-Credential cmdlet to collect the credentials from the operator.</span></span> <span data-ttu-id="8ca50-183">接著，您可以在命令中使用連接至 Analysis Services 的認證物件。</span><span class="sxs-lookup"><span data-stu-id="8ca50-183">You can then use the credential object on a command that connects to Analysis Services.</span></span> <span data-ttu-id="8ca50-184">下列範例將說明其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="8ca50-184">The following example illustrates one approach.</span></span> <span data-ttu-id="8ca50-185">在此範例中，連接至本機實例 (`SQLSERVER:\SQLAS\HTTP_DS`) 設定 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="8ca50-185">In this example, the connection is to a local instance (`SQLSERVER:\SQLAS\HTTP_DS`) configured for HTTP access.</span></span>  
  
```powershell
$cred = Get-Credential adventureworks\dbadmin  
Invoke-ASCmd -Inputfile:"c:\discoverconnections.xmla" -Credential:$cred  
```  
  
 <span data-ttu-id="8ca50-186">使用基本驗證時，您應該一律搭配 SSL 使用 HTTPS，才能透過加密的連接傳送使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="8ca50-186">When using Basic authentication, you should always use HTTPS with SSL so that username and passwords are sent over an encrypted connection.</span></span> <span data-ttu-id="8ca50-187">如需詳細資訊，請參閱[在 iis 7.0 中設定安全通訊端層](https://go.microsoft.com/fwlink/?linkID=184299)和[ (Iis 7) 設定基本驗證](https://go.microsoft.com/fwlink/?LinkId=230776)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-187">For more information, see [Configure Secure Sockets Layer in IIS 7.0](https://go.microsoft.com/fwlink/?linkID=184299) and [Configure Basic Authentication (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=230776).</span></span>  
  
 <span data-ttu-id="8ca50-188">請記住，您在 PowerShell 中所提供的認證、查詢和命令會原封不動地傳遞至傳輸層。</span><span class="sxs-lookup"><span data-stu-id="8ca50-188">Remember that credentials, queries, and commands that you provide in PowerShell are passed unchanged to the transport layer.</span></span> <span data-ttu-id="8ca50-189">在指令碼中加入敏感內容會增加惡意插入攻擊的風險。</span><span class="sxs-lookup"><span data-stu-id="8ca50-189">Including sensitive content in your scripts increases the risk of a malicious injection attack.</span></span>  
  
 <span data-ttu-id="8ca50-190">**當做 Microsoft.Secure.String 物件提供密碼**</span><span class="sxs-lookup"><span data-stu-id="8ca50-190">**Providing a password as a Microsoft.Secure.String object**</span></span>  
  
 <span data-ttu-id="8ca50-191">有些作業 (例如備份與還原) 支援您在命令中提供密碼時所啟用的加密選項。</span><span class="sxs-lookup"><span data-stu-id="8ca50-191">Some operations, such as backup and restore, support encryption options that are activated when you provide a password in the command.</span></span> <span data-ttu-id="8ca50-192">提供密碼會向 Analysis Services 發出加密或解密備份檔的訊號。</span><span class="sxs-lookup"><span data-stu-id="8ca50-192">Providing the password signals Analysis Services to encrypt or decrypt the backup file.</span></span> <span data-ttu-id="8ca50-193">在 Analysis Services 中，此密碼會當做安全的字串物件具現化。</span><span class="sxs-lookup"><span data-stu-id="8ca50-193">In Analysis Services, this password is instantiated as a secure string object.</span></span> <span data-ttu-id="8ca50-194">下列範例說明如何在執行階段向操作員收集密碼。</span><span class="sxs-lookup"><span data-stu-id="8ca50-194">The following example provides an illustration of how to collect a password from the operator at run time.</span></span>  
  
```powershell
$pwd = read-host -AsSecureString -Prompt "Password"  
$pwd -is [System.IDisposable]  
```  
  
 <span data-ttu-id="8ca50-195">您現在可以備份或還原加密的資料庫，並將 $pwd 變數傳遞給密碼參數。</span><span class="sxs-lookup"><span data-stu-id="8ca50-195">You can now backup or restore an encrypted database file, passing the $pwd variable to the password parameter.</span></span> <span data-ttu-id="8ca50-196">若要查看將此圖與其他 Cmdlet 結合的完整範例，請參閱[.asdatabase Cmdlet](/powershell/module/sqlserver/backup-asdatabase)和[.asdatabase Cmdlet](/powershell/module/sqlserver/restore-asdatabase)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-196">To view a complete example that combines this illustration with other cmdlets, see [Backup-ASDatabase cmdlet](/powershell/module/sqlserver/backup-asdatabase) and [Restore-ASDatabase cmdlet](/powershell/module/sqlserver/restore-asdatabase).</span></span>
  
 <span data-ttu-id="8ca50-197">後續步驟是，從工作階段中移除密碼和變數。</span><span class="sxs-lookup"><span data-stu-id="8ca50-197">As a follow up step, remove both the password and variable from the session.</span></span>  
  
```powershell
$pwd.Dispose()  
Remove-Variable -Name pwd  
```  
  
##  <a name="analysis-services-powershell-tasks"></a><a name="bkmk_tasks"></a><span data-ttu-id="8ca50-198">Analysis Services PowerShell 工作</span><span class="sxs-lookup"><span data-stu-id="8ca50-198">Analysis Services PowerShell Tasks</span></span>  
 <span data-ttu-id="8ca50-199">您可以從 Windows PowerShell 管理命令介面或 Windows 命令提示字元執行 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8ca50-199">You can run Analysis Services PowerShell from the Windows PowerShell management shell or a Windows command prompt.</span></span> <span data-ttu-id="8ca50-200">不支援從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行 Analysis Services PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8ca50-200">Running Analysis Services PowerShell from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is not supported.</span></span>  
  
 <span data-ttu-id="8ca50-201">本節將描述使用 Analysis Services PowerShell 的一般工作。</span><span class="sxs-lookup"><span data-stu-id="8ca50-201">This section describes common tasks for using Analysis Services PowerShell.</span></span>  
  
-   [<span data-ttu-id="8ca50-202">載入 Analysis Services 提供者和指令程式</span><span class="sxs-lookup"><span data-stu-id="8ca50-202">Load the Analysis Services Provider and Cmdlets</span></span>](#bkmk_load)  
  
-   [<span data-ttu-id="8ca50-203">啟用遠端管理</span><span class="sxs-lookup"><span data-stu-id="8ca50-203">Enable Remote Administration</span></span>](#bkmk_remote)  
  
-   [<span data-ttu-id="8ca50-204">連接到 Analysis Services 物件</span><span class="sxs-lookup"><span data-stu-id="8ca50-204">Connect to an Analysis Services Object</span></span>](#bkmk_connect)  
  
-   [<span data-ttu-id="8ca50-205">管理服務</span><span class="sxs-lookup"><span data-stu-id="8ca50-205">Administer the Service</span></span>](#bkmk_admin)  
  
-   [<span data-ttu-id="8ca50-206">取得 Analysis Services PowerShell 的說明</span><span class="sxs-lookup"><span data-stu-id="8ca50-206">Get Help for Analysis Services PowerShell</span></span>](#bkmk_help)  
  
###  <a name="load-the-analysis-services-provider-and-cmdlets"></a><a name="bkmk_load"></a><span data-ttu-id="8ca50-207">載入 Analysis Services 提供者和 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ca50-207">Load the Analysis Services Provider and Cmdlets</span></span>  
 <span data-ttu-id="8ca50-208">Analysis Services 提供者是 SQL Server 根提供者的延伸模組，它會在您匯入 SQLPS 模組之後變成可用狀態。</span><span class="sxs-lookup"><span data-stu-id="8ca50-208">The Analysis Services provider is an extension of the SQL Server root provider that becomes available when you import the SQLPS module.</span></span> <span data-ttu-id="8ca50-209">系統會同時載入 Analysis Services 指令程式。不過，如果您想要使用指令程式而不使用提供者，也可以單獨載入它們。</span><span class="sxs-lookup"><span data-stu-id="8ca50-209">Analysis Services cmdlets are loaded simultaneously; you can also load them independently if you want to use them without the provider.</span></span>  
  
-   <span data-ttu-id="8ca50-210">若要載入包含所有 Analysis Services PowerShell 功能的 SQLPS，請執行 Import-module 指令程式。</span><span class="sxs-lookup"><span data-stu-id="8ca50-210">Run the Import-module cmdlet to load SQLPS that includes all of the Analysis Services PowerShell functionality.</span></span> <span data-ttu-id="8ca50-211">如果您無法匯入此模組，可以針對載入模組的目的，暫時將執行原則變更為不受限制。</span><span class="sxs-lookup"><span data-stu-id="8ca50-211">If you cannot import the module, you can temporarily change the execution policy to unrestricted for the purpose of the loading the module.</span></span> <span data-ttu-id="8ca50-212">如需詳細資訊，請參閱 [匯入 SQLPS 模組](../../2014/database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-212">For more information, see [Import the SQLPS Module](../../2014/database-engine/import-the-sqlps-module.md).</span></span>  
  
    ```powershell
    Import-Module "sqlps"  
    ```  
  
     <span data-ttu-id="8ca50-213">或者，您也可以使用 `import-module "sqlps" -disablenamechecking` 來隱藏有關未核准之動詞名稱的警告。</span><span class="sxs-lookup"><span data-stu-id="8ca50-213">Alternatively, use `import-module "sqlps" -disablenamechecking` to suppress the warning about unapproved verb names.</span></span>  
  
-   <span data-ttu-id="8ca50-214">若要單獨載入工作專用的 Analysis Services 指令程式，而不載入 Analysis Services 提供者或 Invoke-ASCmd 指令程式，您可以用獨立作業的方式載入 SQLASCmdlets 模組。</span><span class="sxs-lookup"><span data-stu-id="8ca50-214">To load just the task-specific Analysis Services cmdlets, without the Analysis Services provider or the Invoke-ASCmd cmdlet, you can load the SQLASCmdlets module as an independent operation.</span></span>  
  
    ```powershell
    Import-Module "sqlascmdlets"  
    ```  
  
###  <a name="enable-remote-administration"></a><a name="bkmk_remote"></a><span data-ttu-id="8ca50-215">啟用遠端系統管理</span><span class="sxs-lookup"><span data-stu-id="8ca50-215">Enable Remote Administration</span></span>  
 <span data-ttu-id="8ca50-216">您必須先啟用遠端管理和檔案共用，然後才能使用 Analysis Services PowerShell 搭配遠端 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ca50-216">Before you can use Analysis Services PowerShell with a remote Analysis Services instance, you must first enable remote administration and file sharing.</span></span> <span data-ttu-id="8ca50-217">下列錯誤表示防火牆設定問題：「RPC 伺服器無法使用。</span><span class="sxs-lookup"><span data-stu-id="8ca50-217">The following error indicates a firewall configuration issue: "The RPC server is unavailable.</span></span> <span data-ttu-id="8ca50-218">(來自 HRESULT 的例外狀況: 0x800706BA)」。</span><span class="sxs-lookup"><span data-stu-id="8ca50-218">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
1.  <span data-ttu-id="8ca50-219">確認本機和遠端電腦都有 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 版本的用戶端與伺服器工具。</span><span class="sxs-lookup"><span data-stu-id="8ca50-219">Verify that both local and remote computers have the [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] versions of the client and server tools.</span></span>  
  
2.  <span data-ttu-id="8ca50-220">在裝載 Analysis Services 執行個體的遠端伺服器上，於 Windows 防火牆中開啟 TCP 通訊埠 2383。</span><span class="sxs-lookup"><span data-stu-id="8ca50-220">On the remote server that is hosting an Analysis Services instance, open TCP port 2383 in Windows Firewall.</span></span> <span data-ttu-id="8ca50-221">如果您將 Analysis Services 安裝成具名執行個體或者正在使用自訂通訊埠，此通訊埠編號將會不同。</span><span class="sxs-lookup"><span data-stu-id="8ca50-221">If you installed Analysis Services as a named instance or are using a custom port, the port number will be different.</span></span> <span data-ttu-id="8ca50-222">如需詳細資訊，請參閱 [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-222">For more information, see [Configure the Windows Firewall to Allow Analysis Services Access](instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
3.  <span data-ttu-id="8ca50-223">在遠端伺服器上，確認下列服務已啟動：遠端程序呼叫 (RPC) 服務、TCP/IP NetBIOS Helper 服務、Windows Management Instrumentation (WMI) 服務、Windows 遠端管理 (WS-Management) 服務。</span><span class="sxs-lookup"><span data-stu-id="8ca50-223">On the remote server, verify that the followings services are started:  Remote Procedure Call (RPC) service, TCP/IP NetBIOS Helper service, Windows Management Instrumentation (WMI) service, Windows Remote Management (WS-Management) service.</span></span>  
  
4.  <span data-ttu-id="8ca50-224">在遠端伺服器上，啟動 [群組原則物件編輯器] 嵌入式管理單元 (gpedit.msc)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-224">On the remote server, start the Group Policy Object Editor snap-in (gpedit.msc).</span></span>  
  
5.  <span data-ttu-id="8ca50-225">依序開啟 [電腦設定]、[系統管理範本]、[網路]、[網路連線]、[Windows 防火牆] 和 [網域設定檔]。</span><span class="sxs-lookup"><span data-stu-id="8ca50-225">Open Computer Configuration, open Administrative Templates, open Network, open Network Connections, open Windows Firewall, and then open Domain Profile.</span></span>  
  
6.  <span data-ttu-id="8ca50-226">按兩下 [ **Windows 防火牆：允許輸入遠端系統管理例外**]，選取 [**已啟用**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8ca50-226">Double-click **Windows Firewall: Allow inbound remote administration exception**, select **Enabled**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8ca50-227">按兩下 [ **Windows 防火牆：允許輸入檔案及印表機共用例外**]，選取 [**已啟用**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8ca50-227">Double-click **Windows Firewall: Allow inbound file and printer sharing exception**, select **Enabled**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="8ca50-228">在具有用戶端工具的本機電腦上，使用下列 Cmdlet 來確認遠端系統管理，並以實際的伺服器名稱取代*遠端伺服器名稱*的預留位置。</span><span class="sxs-lookup"><span data-stu-id="8ca50-228">On the local computer that has the client tools, use the following cmdlets to verify remote administration, substituting the actual server name for the *remote-server-name* placeholder.</span></span> <span data-ttu-id="8ca50-229">如果 Analysis Services 安裝成預設執行個體，請省略執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8ca50-229">Omit the instance name if Analysis Services is installed as the default instance.</span></span> <span data-ttu-id="8ca50-230">您先前必須匯入 SQLPS 模組，才能讓此命令運作。</span><span class="sxs-lookup"><span data-stu-id="8ca50-230">You must have previously imported the SQLPS module in order for the command to work.</span></span>  
  
    ```
    PS SQLSERVER:\> cd sqlas
    PS SQLSERVER:\sqlas> cd <remote-server-name\instance-name>  
    PS SQLSERVER:\sqlas\<remote-server-name\instance-name> dir  
    ```  
  
 <span data-ttu-id="8ca50-231">在某些情況下，可能需要額外的設定。</span><span class="sxs-lookup"><span data-stu-id="8ca50-231">In some cases, additional configuration might be necessary.</span></span> <span data-ttu-id="8ca50-232">您可能必須在遠端伺服器上輸入下列命令，然後才能從另一部電腦發出命令至遠端伺服器：</span><span class="sxs-lookup"><span data-stu-id="8ca50-232">You might need to type the following on the remote server before you can issue commands to it from another computer:</span></span>  
  
```powershell
Enable-PSRemoting  
```  
  
  
###  <a name="connect-to-an-analysis-services-object"></a><a name="bkmk_connect"></a><span data-ttu-id="8ca50-233">連接到 Analysis Services 物件</span><span class="sxs-lookup"><span data-stu-id="8ca50-233">Connect to an Analysis Services Object</span></span>  
 <span data-ttu-id="8ca50-234">Analysis Services PowerShell 提供者支援導覽 Analysis Services 物件階層，而且它會設定執行命令的內容。</span><span class="sxs-lookup"><span data-stu-id="8ca50-234">The Analysis Services PowerShell provider supports navigation of the Analysis Services object hierarchy and sets the context for running commands.</span></span> <span data-ttu-id="8ca50-235">此提供者是透過 SQLPS 模組提供之 SQLSERVER 根提供者的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8ca50-235">The provider is an extension of the SQLSERVER root provider available through the SQLPS module.</span></span> <span data-ttu-id="8ca50-236">載入 SQLPS 模組之後，您就可以導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="8ca50-236">After you load the SQLPS module, you can navigate the path.</span></span>  
  
 <span data-ttu-id="8ca50-237">您可以連接到本機或遠端執行個體，但是某些指令程式只能在本機執行個體上執行 (亦即 merge-partition)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-237">You can connect to a local or remote instance, but some cmdlets only run on a local instance (namely, merge-partition).</span></span> <span data-ttu-id="8ca50-238">您可以針對設定為 HTTP 存取的 Analysis Services 伺服器使用原生連接或 HTTP 連接。</span><span class="sxs-lookup"><span data-stu-id="8ca50-238">You can use a native connection or an HTTP connection for Analysis Services servers that you configured for HTTP access.</span></span> <span data-ttu-id="8ca50-239">下圖顯示原生和 HTTP 連接的導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="8ca50-239">The following illustrations show the navigation path for native and HTTP connections.</span></span> <span data-ttu-id="8ca50-240">下圖顯示原生和 HTTP 連接的導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="8ca50-240">The following illustrations show the navigation path for native and HTTP connections.</span></span>  
  
 <span data-ttu-id="8ca50-241">**Analysis Services 的原生連接**</span><span class="sxs-lookup"><span data-stu-id="8ca50-241">**Native Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="8ca50-242">![Analysis Services 的原生連接](media/ssas-powershell-nativeconnection.gif "Analysis Services 的原生連接")</span><span class="sxs-lookup"><span data-stu-id="8ca50-242">![Native connection to Analysis Services](media/ssas-powershell-nativeconnection.gif "Native connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="8ca50-243">下列範例示範如何使用原生連接來導覽物件階層。</span><span class="sxs-lookup"><span data-stu-id="8ca50-243">The following example is a demonstration of how to use a native connection to navigate object hierarchy.</span></span> <span data-ttu-id="8ca50-244">您可以從提供者發出 `dir` 來檢視執行個體資訊。</span><span class="sxs-lookup"><span data-stu-id="8ca50-244">From the provider, you can issue a `dir` to view instance information.</span></span> <span data-ttu-id="8ca50-245">您可以使用 `cd` 來檢視該執行個體的物件。</span><span class="sxs-lookup"><span data-stu-id="8ca50-245">You can use `cd` to view objects of that instance.</span></span>  
  
```  
PS SQLSERVER:> cd sqlas  
PS SQLSERVER\sqlas:> dir  
PS SQLSERVER\sqlas:> cd localhost\default  
PS SQLSERVER\sqlas\localhost\default:> dir  
```  
  
 <span data-ttu-id="8ca50-246">您應該會看見下列集合：Assemblies、Databases、Roles 和 Traces。</span><span class="sxs-lookup"><span data-stu-id="8ca50-246">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="8ca50-247">如果繼續使用 `cd` 和 `dir`，您就可以檢視每個集合的內容。</span><span class="sxs-lookup"><span data-stu-id="8ca50-247">Continuing to use `cd` and `dir`, you can view the contents of each collection.</span></span>  
  
 <span data-ttu-id="8ca50-248">**Analysis Services 的 HTTP 連接**</span><span class="sxs-lookup"><span data-stu-id="8ca50-248">**HTTP Connections to Analysis Services**</span></span>  
  
 <span data-ttu-id="8ca50-249">![Analysis Services 的 HTTP 連接](media/ssas-powershell-httpconnection.gif "Analysis Services 的 HTTP 連接")</span><span class="sxs-lookup"><span data-stu-id="8ca50-249">![HTTP Connection to Analysis Services](media/ssas-powershell-httpconnection.gif "HTTP Connection to Analysis Services")</span></span>  
  
 <span data-ttu-id="8ca50-250">如果您使用本主題中的指示設定伺服器以進行 HTTP 存取，HTTP 連線會很有用： [Internet Information Services &#40;IIS&#41; 8.0 設定 Http 存取 Analysis Services](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span><span class="sxs-lookup"><span data-stu-id="8ca50-250">HTTP connections are useful if you configured your server for HTTP access using the instructions in this topic: [Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)</span></span>  
  
 <span data-ttu-id="8ca50-251">假設的伺服器 URL 為 http://localhost/olap/msmdpump.dll ，連接看起來可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="8ca50-251">Assuming a server URL of http://localhost/olap/msmdpump.dll, a connection might look like the following:</span></span>  
  
```  
PS SQLSERVER\sqlas:> cd http_ds  
PS SQLSERVER\sqlas\http_ds:> $Url=Encode-SqlName "http://localhost/olap/msmdpump.dll"  
PS SQLSERVER\sqlas\http_ds:> cd $Url  
PS SQLSERVER\sqlas\http_ds\http%3A%2F%2Flocalhost%2olap%2msmdpump%2Edll:> dir  
```  
  
 <span data-ttu-id="8ca50-252">您應該會看見下列集合：Assemblies、Databases、Roles 和 Traces。</span><span class="sxs-lookup"><span data-stu-id="8ca50-252">You should see the following collections: Assemblies, Databases, Roles, and Traces.</span></span> <span data-ttu-id="8ca50-253">如果您無法檢視這些集合的內容，請檢查 OLAP 虛擬目錄的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="8ca50-253">If you cannot view the contents of these collections, check the authentication settings on the OLAP virtual directory.</span></span> <span data-ttu-id="8ca50-254">請確定匿名存取已停用。</span><span class="sxs-lookup"><span data-stu-id="8ca50-254">Make sure that Anonymous Access is disabled.</span></span> <span data-ttu-id="8ca50-255">如果您正在使用 Windows 驗證，請確定 Windows 使用者帳戶擁有 Analysis Services 執行個體的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="8ca50-255">If you are using Windows Authentication, be sure that your Windows user account has administrative permissions on the Analysis Services instance.</span></span>  
  
###  <a name="administer-the-service"></a><a name="bkmk_admin"></a><span data-ttu-id="8ca50-256">管理服務</span><span class="sxs-lookup"><span data-stu-id="8ca50-256">Administer the Service</span></span>  
 <span data-ttu-id="8ca50-257">確認服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="8ca50-257">Verify the service is running.</span></span> <span data-ttu-id="8ca50-258">傳回 SQL Server 服務的狀態、名稱和顯示名稱，包括 Analysis Services (MSSQLServerOLAPService) 和 Database Engine。</span><span class="sxs-lookup"><span data-stu-id="8ca50-258">Returns status, name, and display name for SQL Server services, including Analysis Services (MSSQLServerOLAPService) and the Database Engine.</span></span>  
  
```powershell
Get-Service mssql*  
```  
  
 <span data-ttu-id="8ca50-259">傳回處理序的相關屬性，包括處理序識別碼、控制代碼計數和記憶體使用量：</span><span class="sxs-lookup"><span data-stu-id="8ca50-259">Returns properties about a process, including process ID, handle count, and memory usage:</span></span>  
  
```powershell
Get-Process msmdsrv  
```  
  
 <span data-ttu-id="8ca50-260">當您從管理員命令介面發出下列指令程式時，就會重新啟動服務：</span><span class="sxs-lookup"><span data-stu-id="8ca50-260">Restarts the service when you issue the following cmdlet from the administrator shell:</span></span>  
  
```powershell
Restart-Service mssqlserverolapservice  
```  
  
###  <a name="get-help-for-analysis-services-powershell"></a><a name="bkmk_help"></a><span data-ttu-id="8ca50-261">取得 Analysis Services PowerShell 的說明</span><span class="sxs-lookup"><span data-stu-id="8ca50-261">Get Help for Analysis Services PowerShell</span></span>  
 <span data-ttu-id="8ca50-262">您可以使用下列任何指令程式來確認指令程式可用性，並且取得有關服務、處理序和物件的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="8ca50-262">Use any of the following cmdlets to verify cmdlet availability and to get more information about services, processes, and objects.</span></span>  
  
1.  <span data-ttu-id="8ca50-263">`Get-Help` 會傳回 Analysis Services 指令程式的內建說明，包括範例：</span><span class="sxs-lookup"><span data-stu-id="8ca50-263">`Get-Help` returns the built-in help for an Analysis Services cmdlet, including examples:</span></span>  
  
    ```powershell
    Get-Help invoke-ascmd -Examples  
    ```  
  
2.  <span data-ttu-id="8ca50-264">`Get-Command` 會傳回十一個 Analysis Services PowerShell 指令程式的清單：</span><span class="sxs-lookup"><span data-stu-id="8ca50-264">`Get-Command` returns a list of the eleven Analysis Services PowerShell cmdlets:</span></span>  
  
    ```powershell
    Get-Command -module SQLASCmdlets  
    ```  
  
3.  <span data-ttu-id="8ca50-265">`Get-Member` 會傳回服務或處理序的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="8ca50-265">`Get-Member` returns properties or methods of a service or process.</span></span>  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Property  
    ```  
  
    ```powershell
    Get-Service mssqlserverolapservice | Get-Member -Type Method  
    ```  
  
    ```powershell
    Get-Process msmdsrv | Get-Member -Type Property  
    ```  
  
4.  <span data-ttu-id="8ca50-266">`Get-Member` 也可以搭配 SQLAS 提供者來指定伺服器執行個體，以便傳回物件的屬性或方法 (例如，伺服器物件的 AMO 方法)。</span><span class="sxs-lookup"><span data-stu-id="8ca50-266">`Get-Member` can also be used to return properties or methods of an object (for example, AMO methods on the server object) using the SQLAS provider to specify the server instance.</span></span>  
  
    ```
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = New-Object Microsoft.AnalysisServices.Server  
    PS SQLSERVER:\sqlas\localhost\default > $serverObj = | Get-Member -Type Method  
    ```  
  
5.  <span data-ttu-id="8ca50-267">`Get-PSdrive` 會傳回目前已安裝的提供者清單。</span><span class="sxs-lookup"><span data-stu-id="8ca50-267">`Get-PSdrive` returns a list of the providers that are currently installed.</span></span> <span data-ttu-id="8ca50-268">如果您匯入了 SQLPS 模組，就會在清單中看見 `SQLServer` 提供者 (SQLAS 屬於 SQLServer 提供者的一部分，永遠不會個別出現在清單中)：</span><span class="sxs-lookup"><span data-stu-id="8ca50-268">If you imported the SQLPS module, you will see the `SQLServer` provider in the list (SQLAS is part of the SQLServer provider and never appears separately in the list):</span></span>  
  
    ```powershell
    Get-PSDrive  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8ca50-269">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca50-269">See Also</span></span>  
 <span data-ttu-id="8ca50-270">[安裝 SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="8ca50-270">[Install SQL Server PowerShell](../database-engine/install-windows/install-sql-server-powershell.md) </span></span>  
 <span data-ttu-id="8ca50-271">[使用 PowerShell 管理表格式模型 (blog) ](https://go.microsoft.com/fwlink/?linkID=227685) </span><span class="sxs-lookup"><span data-stu-id="8ca50-271">[Manage Tabular Models Using PowerShell (blog)](https://go.microsoft.com/fwlink/?linkID=227685) </span></span>  
 [<span data-ttu-id="8ca50-272">設定 Internet Information Services &#40;IIS&#41; 8.0 上 Analysis Services 的 HTTP 存取</span><span class="sxs-lookup"><span data-stu-id="8ca50-272">Configure HTTP Access to Analysis Services on Internet Information Services &#40;IIS&#41; 8.0</span></span>](instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
