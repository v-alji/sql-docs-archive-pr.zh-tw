---
title: rsconfig 公用程式 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- connections [Reporting Services], configuring
- rsconfig utility
- report servers [Reporting Services], connections
- command prompt utilities [Reporting Services]
- command prompt utilities [SQL Server], rsconfig
ms.assetid: 84e45a2f-3ca6-4c16-8259-c15ff49d72ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 499fa5529991b36e467567b4c7006845dfcd2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704833"
---
# <a name="rsconfig-utility-ssrs"></a><span data-ttu-id="21673-102">rsconfig 公用程式 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="21673-102">rsconfig Utility (SSRS)</span></span>
  <span data-ttu-id="21673-103">**rsconfig.exe** 公用程式會加密連接和帳戶值，並會將它們儲存在 RSReportServer.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="21673-103">The **rsconfig.exe** utility encrypts and stores connection and account values in the RSReportServer.config file.</span></span> <span data-ttu-id="21673-104">加密的值包括自動處理報表的程序所用的報表伺服器資料庫連接資訊和帳戶值。</span><span class="sxs-lookup"><span data-stu-id="21673-104">Encrypted values include report server database connection information and account values used for unattended report processing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21673-105">語法</span><span class="sxs-lookup"><span data-stu-id="21673-105">Syntax</span></span>  
  
```  
  
      rsconfig {-?}  
{-cconnection}  
{-eunattendedaccount}  
{-mcomputername}  
{-iinstancename}  
{-sservername}  
{-ddatabasename}  
{-aauthmethod}  
{-uusername}  
{-ppassword}  
{-ttrace}  
```  
  
## <a name="arguments"></a><span data-ttu-id="21673-106">引數</span><span class="sxs-lookup"><span data-stu-id="21673-106">Arguments</span></span>  
  
|<span data-ttu-id="21673-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="21673-107">Term</span></span>|<span data-ttu-id="21673-108">選擇性/必要</span><span class="sxs-lookup"><span data-stu-id="21673-108">Optional/Required</span></span>|<span data-ttu-id="21673-109">定義</span><span class="sxs-lookup"><span data-stu-id="21673-109">Definition</span></span>|  
|----------|------------------------|----------------|  
|<span data-ttu-id="21673-110">**-?**</span><span class="sxs-lookup"><span data-stu-id="21673-110">**-?**</span></span>|<span data-ttu-id="21673-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="21673-111">Optional.</span></span>|<span data-ttu-id="21673-112">顯示 Rsconfig.exe 引數的語法。</span><span class="sxs-lookup"><span data-stu-id="21673-112">Displays the syntax of Rsconfig.exe arguments.</span></span>|  
|`-c`|<span data-ttu-id="21673-113">如果未使用 `-e` 引數，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-113">Required if `-e` argument is not used.</span></span>|<span data-ttu-id="21673-114">指定用來將報表伺服器連接到報表伺服器資料庫的連接字串、認證和資料來源值。</span><span class="sxs-lookup"><span data-stu-id="21673-114">Specifies the connection string, credentials, and data source values used to connect a report server to the report server database.</span></span><br /><br /> <span data-ttu-id="21673-115">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="21673-115">This argument does not take a value.</span></span> <span data-ttu-id="21673-116">不過，您也必須指定其他引數來搭配它，以便提供所有必要的連接值。</span><span class="sxs-lookup"><span data-stu-id="21673-116">However, additional arguments must be specified with it to provide all of the required connection values.</span></span><br /><br /> <span data-ttu-id="21673-117">您可以使用來指定的引數， `-c` 包括 `-m` 、 **-s**、 `-i` 、、、、 `-d` `-a` `-u` `-p` 和 `-t` 。</span><span class="sxs-lookup"><span data-stu-id="21673-117">Arguments that you can specify with `-c` include `-m`, **-s**, `-i`,`-d`,`-a`,`-u`,`-p`, and`-t`.</span></span>|  
|`-e`|<span data-ttu-id="21673-118">如果未使用 `-c` 引數，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-118">Required if `-c` argument is not used.</span></span>|<span data-ttu-id="21673-119">指定自動報表執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-119">Specifies the unattended report execution account.</span></span><br /><br /> <span data-ttu-id="21673-120">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="21673-120">This argument does not take a value.</span></span> <span data-ttu-id="21673-121">不過，命令列必須包括其他引數，以便指定組態檔中所加密的值。</span><span class="sxs-lookup"><span data-stu-id="21673-121">However, you must include additional arguments on the command line to specify that values that are encrypted in the configuration file.</span></span><br /><br /> <span data-ttu-id="21673-122">您可以搭配 `-e` 來指定的引數，包括 `-u` 和 `-p`。</span><span class="sxs-lookup"><span data-stu-id="21673-122">Arguments that you can specify with `-e` include `-u` and `-p`.</span></span> <span data-ttu-id="21673-123">您也可以設定 `-t`。</span><span class="sxs-lookup"><span data-stu-id="21673-123">You can also set `-t`.</span></span>|  
|<span data-ttu-id="21673-124">`-m`  *名稱*</span><span class="sxs-lookup"><span data-stu-id="21673-124">`-m`  *computername*</span></span>|<span data-ttu-id="21673-125">如果您在設定遠端報表伺服器執行個體，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-125">Required if you are configuring a remote report server instance.</span></span>|<span data-ttu-id="21673-126">指定主控報表伺服器的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="21673-126">Specifies the name of the computer that is hosting the report server.</span></span> <span data-ttu-id="21673-127">如果省略這個引數，預設值就是 `localhost`。</span><span class="sxs-lookup"><span data-stu-id="21673-127">If this argument is omitted, the default is `localhost`.</span></span>|  
|<span data-ttu-id="21673-128">**-s**  *servername*</span><span class="sxs-lookup"><span data-stu-id="21673-128">**-s**  *servername*</span></span>|<span data-ttu-id="21673-129">必要。</span><span class="sxs-lookup"><span data-stu-id="21673-129">Required.</span></span>|<span data-ttu-id="21673-130">指定主控報表伺服器資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="21673-130">Specifies the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the report server database.</span></span>|  
|<span data-ttu-id="21673-131">`-i`  *instancename*</span><span class="sxs-lookup"><span data-stu-id="21673-131">`-i`  *instancename*</span></span>|<span data-ttu-id="21673-132">如果您使用具名執行個體，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-132">Required if you are using named instances.</span></span>|<span data-ttu-id="21673-133">如果您利用具名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來主控報表伺服器資料庫，這個值會指定具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="21673-133">If you used a named [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the report server database, this value specifies the named instance.</span></span>|  
|<span data-ttu-id="21673-134">`-d`  *名稱*</span><span class="sxs-lookup"><span data-stu-id="21673-134">`-d`  *databasename*</span></span>|<span data-ttu-id="21673-135">必要。</span><span class="sxs-lookup"><span data-stu-id="21673-135">Required.</span></span>|<span data-ttu-id="21673-136">指定報表伺服器資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="21673-136">Specifies the name of the report server database.</span></span>|  
|<span data-ttu-id="21673-137">`-a`  *authmethod*</span><span class="sxs-lookup"><span data-stu-id="21673-137">`-a`  *authmethod*</span></span>|<span data-ttu-id="21673-138">必要。</span><span class="sxs-lookup"><span data-stu-id="21673-138">Required.</span></span>|<span data-ttu-id="21673-139">指定報表伺服器用來連接到報表伺服器資料庫的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="21673-139">Specifies the authentication method that the report server uses to connect to the report server database.</span></span> <span data-ttu-id="21673-140">有效值如下：`Windows` 或 `SQL` (這個引數不區分大小寫)。</span><span class="sxs-lookup"><span data-stu-id="21673-140">Valid values are `Windows` or `SQL` (this argument is not case-sensitive).</span></span><br /><br /> <span data-ttu-id="21673-141">`Windows` 指定報表伺服器使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="21673-141">`Windows` specifies that the report server use Windows Authentication.</span></span><br /><br /> <span data-ttu-id="21673-142">`SQL` 指定報表伺服器使用 SQL Server 驗證。</span><span class="sxs-lookup"><span data-stu-id="21673-142">`SQL` specifies that the report server use SQL Server Authentication.</span></span>|  
|<span data-ttu-id="21673-143">`-u`  *[網域 \\ ]username*</span><span class="sxs-lookup"><span data-stu-id="21673-143">`-u`  *[domain\\]username*</span></span>|<span data-ttu-id="21673-144">對 `-e` 而言，這是必要的；對 `-c` 而言，這是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="21673-144">Required with `-e` Optional with `-c`.</span></span>|<span data-ttu-id="21673-145">指定報表伺服器資料庫連接或自動帳戶的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-145">Specifies a user account for the report server database connection or for the unattended account.</span></span><br /><br /> <span data-ttu-id="21673-146">若為 **rsconfig -e**，此引數是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-146">For **rsconfig -e**, this argument is required.</span></span> <span data-ttu-id="21673-147">它必須是網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-147">It must be a domain user account.</span></span><br /><br /> <span data-ttu-id="21673-148">若為**rsconfig-c**和 `-a SQL` ，此引數必須指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="21673-148">For **rsconfig -c** and `-a SQL`, this argument must specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span><br /><br /> <span data-ttu-id="21673-149">若為**rsconfig-c**和 `-a Windows` ，此引數可能會指定網域使用者、內建帳戶或服務帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="21673-149">For **rsconfig -c** and `-a Windows`, this argument may specify a domain user, a built-in account, or service account credentials.</span></span> <span data-ttu-id="21673-150">如果您指定網域帳戶，請以 <網域>\<使用者名稱>\*\* 的格式指定 <網域>\*\* 和 <使用者名稱>\*\*。</span><span class="sxs-lookup"><span data-stu-id="21673-150">If you are specifying a domain account, specify *domain* and *username* in the format *domain\username*.</span></span> <span data-ttu-id="21673-151">如果您是使用內建帳戶，這個引數就是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="21673-151">If you are using a built-in account, this argument is optional.</span></span> <span data-ttu-id="21673-152">如果您要使用服務帳戶認證，請省略這個引數。</span><span class="sxs-lookup"><span data-stu-id="21673-152">If you want to use service account credentials, omit this argument.</span></span>|  
|<span data-ttu-id="21673-153">`-p`  *許可權*</span><span class="sxs-lookup"><span data-stu-id="21673-153">`-p`  *password*</span></span>|<span data-ttu-id="21673-154">如果指定 `-u` 的話，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="21673-154">Required if `-u` is specified.</span></span>|<span data-ttu-id="21673-155">指定要搭配 <使用者名稱>\*\* 引數使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="21673-155">Specifies the password to use with the *username* argument.</span></span> <span data-ttu-id="21673-156">如果帳戶不需要密碼，您可以將這個引數設為空白值。</span><span class="sxs-lookup"><span data-stu-id="21673-156">You can set this argument to a blank value if the account does not require a password.</span></span> <span data-ttu-id="21673-157">網域帳戶的這個值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="21673-157">This value is case-sensitive for domain accounts.</span></span>|  
|`-t`|<span data-ttu-id="21673-158">選擇性。</span><span class="sxs-lookup"><span data-stu-id="21673-158">Optional.</span></span>|<span data-ttu-id="21673-159">在追蹤記錄中，輸出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="21673-159">Outputs error messages to the trace log.</span></span> <span data-ttu-id="21673-160">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="21673-160">This argument does not take a value.</span></span> <span data-ttu-id="21673-161">如需詳細資訊，請參閱 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="21673-161">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>|  
  
## <a name="permissions"></a><span data-ttu-id="21673-162">權限</span><span class="sxs-lookup"><span data-stu-id="21673-162">Permissions</span></span>  
 <span data-ttu-id="21673-163">您必須是主控您在設定的報表伺服器之電腦的本機管理員。</span><span class="sxs-lookup"><span data-stu-id="21673-163">You must be a local administrator on the computer that hosts the report server you are configuring.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="21673-164">檔案位置</span><span class="sxs-lookup"><span data-stu-id="21673-164">File Location</span></span>  
 <span data-ttu-id="21673-165">Rsconfig.exe 位於 **\Program Files\Microsoft SQL Server\110\Tools\Binn**。</span><span class="sxs-lookup"><span data-stu-id="21673-165">Rsconfig.exe is located in **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="21673-166">您可以從檔案系統上的任何資料夾執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="21673-166">You can run the utility from any folder on your file system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21673-167">備註</span><span class="sxs-lookup"><span data-stu-id="21673-167">Remarks</span></span>  
 <span data-ttu-id="21673-168">Rsconfig.exe 有兩個用途：</span><span class="sxs-lookup"><span data-stu-id="21673-168">Rsconfig.exe is used for two purposes:</span></span>  
  
-   <span data-ttu-id="21673-169">修改報表伺服器用來連接報表伺服器資料庫的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="21673-169">To modify the connection information that a report server uses to connect to a report server database.</span></span>  
  
-   <span data-ttu-id="21673-170">設定特殊帳戶，供報表伺服器在無法使用其他認證時，用來登入遠端資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="21673-170">To configure a special account that the report server uses to log on to a remote database server when other credentials are not available.</span></span>  
  
 <span data-ttu-id="21673-171">您可以在**的本機或遠端執行個體上執行** rsconfig [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]公用程式。</span><span class="sxs-lookup"><span data-stu-id="21673-171">You can run the**rsconfig** utility on a local or remote instance of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="21673-172">您無法使用 **rsconfig** 公用程式解密及檢視已設定的值。</span><span class="sxs-lookup"><span data-stu-id="21673-172">You cannot use the **rsconfig** utility to decrypt and view values that are already set.</span></span>  
  
 <span data-ttu-id="21673-173">在執行這個公用程式之前，您必須先將 Windows Management Instrumentation (WMI) 安裝在您要設定的電腦中。</span><span class="sxs-lookup"><span data-stu-id="21673-173">Before you can run this utility, Windows Management Instrumentation (WMI) must be installed on the computer that you are configuring.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="21673-174">範例</span><span class="sxs-lookup"><span data-stu-id="21673-174">Examples</span></span>  
 <span data-ttu-id="21673-175">下列範例說明 **rsconfig**的使用方式。</span><span class="sxs-lookup"><span data-stu-id="21673-175">The following examples illustrate ways of using **rsconfig**.</span></span>  
  
#### <a name="specifying-a-domain-user-account"></a><span data-ttu-id="21673-176">指定網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-176">Specifying a Domain User Account</span></span>  
 <span data-ttu-id="21673-177">這個範例會顯示在連接本機報表伺服器資料庫時，如何設定報表伺服器來使用網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-177">This example shows how to configure a report server to use a domain user account when connecting to a local report server database.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows -u <MYDOMAIN\MYACCOUNT> -p <PASSWORD>  
```  
  
#### <a name="specifying-a-sql-server-database-user-account"></a><span data-ttu-id="21673-178">指定 SQL Server 資料庫使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-178">Specifying a SQL Server Database User Account</span></span>  
 <span data-ttu-id="21673-179">這個範例會顯示如何設定報表伺服器，利用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入來連接遠端報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="21673-179">This example shows how to configure a report server to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to connect to a remote report server database.</span></span>  
  
```  
rsconfig -c -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -d reportserver -a SQL -u SA -p <SAPASSWORD>  
```  
  
#### <a name="specifying-a-built-in-account"></a><span data-ttu-id="21673-180">指定內建帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-180">Specifying a Built-in Account</span></span>  
 <span data-ttu-id="21673-181">這個範例會顯示在連接本機報表伺服器資料庫時，如何設定報表伺服器來使用內建帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-181">This example shows how to configure a report server to use a built-in account when connecting to a local report server database.</span></span> <span data-ttu-id="21673-182">請注意，不要使用 `-u`。</span><span class="sxs-lookup"><span data-stu-id="21673-182">Notice that `-u` is not used.</span></span> <span data-ttu-id="21673-183">支援的內建帳戶值範例包括本機系統的 NT AUTHORITY\SYSTEM 和網路服務的 NT AUTHORITY\NETWORKSERVICE ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 僅) 。</span><span class="sxs-lookup"><span data-stu-id="21673-183">Examples of supported built-in account values include NT AUTHORITY\SYSTEM for Local System and NT AUTHORITY\NETWORKSERVICE for Network Service ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] only).</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows "NT AUTHORITY\SYSTEM"  
```  
  
#### <a name="specifying-a-service-account"></a><span data-ttu-id="21673-184">指定服務帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-184">Specifying a Service Account</span></span>  
 <span data-ttu-id="21673-185">這個範例會顯示在連接本機報表伺服器資料庫時，如何設定報表伺服器來使用「報表伺服器視窗」服務帳戶和 Web 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-185">This example shows how to configure a report server to use the Report Server Windows service account and Web service account when connecting to a local report server database.</span></span> <span data-ttu-id="21673-186">請注意，不要使用 `-u`，也不要指定任何帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="21673-186">Notice that `-u` is not used and that no account information is specified.</span></span> <span data-ttu-id="21673-187">當您從命令中刪除帳戶值， **rsconfig** 公用程式會使用執行各項服務時所用的整合式安全性和服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-187">When you eliminate account values from the command, the **rsconfig** utility uses integrated security and the service account that each service runs under.</span></span>  
  
```  
rsconfig -c -s <SQLSERVERNAME> -d reportserver -a Windows  
```  
  
#### <a name="specifying-the-unattended-account-on-a-local-server"></a><span data-ttu-id="21673-188">指定本機伺服器中的自動帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-188">Specifying the Unattended Account on a Local Server</span></span>  
 <span data-ttu-id="21673-189">這個範例會顯示如何設定帳戶，供不會將認證傳給外部資料來源的報表之自動執行報表的作業使用。</span><span class="sxs-lookup"><span data-stu-id="21673-189">This example shows how to configure the account used for unattended report execution for reports that do not pass credentials to the external data source.</span></span> <span data-ttu-id="21673-190">這個帳戶必須是 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="21673-190">The account must be a Windows domain account.</span></span> <span data-ttu-id="21673-191">您不能指定這個使用者名稱和密碼的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="21673-191">You cannot specify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for the user name and password.</span></span> <span data-ttu-id="21673-192">這個帳戶設在本機報表伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="21673-192">The account is configured on a local report server instance.</span></span> <span data-ttu-id="21673-193">錯誤訊息放在 ReportingServices\LogFiles 資料夾的追蹤記錄中。</span><span class="sxs-lookup"><span data-stu-id="21673-193">Error messages are captured in the trace logs in the ReportingServices\LogFiles folder.</span></span>  
  
```  
rsconfig -e -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
#### <a name="specifying-the-unattended-account-on-a-remote-server"></a><span data-ttu-id="21673-194">指定遠端伺服器中的自動帳戶</span><span class="sxs-lookup"><span data-stu-id="21673-194">Specifying the Unattended Account on a Remote Server</span></span>  
 <span data-ttu-id="21673-195">這個範例會顯示如何設定與 Rsconfig.exe 版本相同的遠端報表伺服器執行個體的帳戶 (例如，報表伺服器和 Rsconfig.exe 都是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 版)。</span><span class="sxs-lookup"><span data-stu-id="21673-195">This example shows how to configure the account on a remote report server instance that is the same version as Rsconfig.exe (for example, the report server and Rsconfig.exe are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 version).</span></span> <span data-ttu-id="21673-196">錯誤訊息的資訊放在遠端伺服器的追蹤記錄中。</span><span class="sxs-lookup"><span data-stu-id="21673-196">Error message information is captured in the trace logs on the remote server.</span></span>  
  
```  
rsconfig -e -m <REMOTECOMPUTERNAME> -s <SQLSERVERNAME> -u <DOMAIN\ACCOUNT> -p <PASSWORD> -t  
```  
  
## <a name="see-also"></a><span data-ttu-id="21673-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21673-197">See Also</span></span>  
 <span data-ttu-id="21673-198">[&#40;SSRS Configuration Manager 設定報表伺服器資料庫連接&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="21673-198">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="21673-199">[&#40;SSRS Configuration Manager 設定自動執行帳戶&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="21673-199">[Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="21673-200">[Reporting Services 報表伺服器 &#40;原生模式&#41;](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="21673-200">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="21673-201">[儲存加密的報表伺服器資料 &#40;SSRS 組態管理員&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span><span class="sxs-lookup"><span data-stu-id="21673-201">[Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md) </span></span>  
 <span data-ttu-id="21673-202">[Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="21673-202">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="21673-203">[&#40;SSRS&#41;的報表伺服器命令提示字元公用程式](report-server-command-prompt-utilities-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="21673-203">[Report Server Command Prompt Utilities &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md) </span></span>  
 [<span data-ttu-id="21673-204">RSReportServer 設定檔</span><span class="sxs-lookup"><span data-stu-id="21673-204">RSReportServer Configuration File</span></span>](../report-server/rsreportserver-config-configuration-file.md)  
  
  
