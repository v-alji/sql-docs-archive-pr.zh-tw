---
title: sqlcmd 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fbe5a3dcefb2218543e015dad71acfe79aea8e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706921"
---
# <a name="sqlcmd-utility"></a><span data-ttu-id="0357e-102">sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="0357e-102">sqlcmd Utility</span></span>
  <span data-ttu-id="0357e-103">`sqlcmd`公用程式可讓您在 [!INCLUDE[tsql](../includes/tsql-md.md)] 命令提示字元處、在 SQLCMD 模式的 [**查詢編輯器**] 中、在 Windows 腳本檔案中，或是在 Agent 作業的作業系統 ( # A0) 作業步驟中，輸入語句、系統程式和腳本檔案 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0357e-103">The `sqlcmd` utility lets you enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt, in **Query Editor** in SQLCMD mode, in a Windows script file or in an operating system (Cmd.exe) job step of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="0357e-104">這個公用程式利用 ODBC 執行 [!INCLUDE[tsql](../includes/tsql-md.md)] 批次。</span><span class="sxs-lookup"><span data-stu-id="0357e-104">This utility uses ODBC to execute [!INCLUDE[tsql](../includes/tsql-md.md)] batches.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="0357e-105">在 [ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] **查詢編輯器**] 中使用 SQLCLIENT 執行一般和 SQLCMD 模式。</span><span class="sxs-lookup"><span data-stu-id="0357e-105">uses the [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode in **Query Editor**.</span></span> <span data-ttu-id="0357e-106">從命令列執行 `sqlcmd` 時，`sqlcmd` 會使用 ODBC 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="0357e-106">When `sqlcmd` is run from the command line, `sqlcmd` uses the ODBC driver.</span></span> <span data-ttu-id="0357e-107">因為可能會套用不同的預設選項，因此，以 SQLCMD 模式在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中以及在 `sqlcmd` 公用程式中執行相同的查詢時，可能會看到不同的行為。</span><span class="sxs-lookup"><span data-stu-id="0357e-107">Because different default options may apply, you might see different behavior when you execute the same query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] in SQLCMD Mode and in the `sqlcmd` utility.</span></span>  
  
 <span data-ttu-id="0357e-108">目前，`sqlcmd` 不需要在命令列選項與值之間保留一個空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-108">Currently, `sqlcmd` does not require a space between the command line option and the value.</span></span> <span data-ttu-id="0357e-109">但是在未來的版本中，可能會需要在命令列選項與值之間空一個空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-109">However, in a future release, a space may be required between the command line option and the value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0357e-110">語法</span><span class="sxs-lookup"><span data-stu-id="0357e-110">Syntax</span></span>  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a><span data-ttu-id="0357e-111">命令列選項</span><span class="sxs-lookup"><span data-stu-id="0357e-111">Command-line Options</span></span>  
 <span data-ttu-id="0357e-112">**登入相關選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-112">**Login-Related Options**</span></span>  
  <span data-ttu-id="0357e-113">**-A**</span><span class="sxs-lookup"><span data-stu-id="0357e-113">**-A**</span></span>  
 <span data-ttu-id="0357e-114">利用專用管理員連接 (DAC) 來登入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0357e-114">Logs in to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with a Dedicated Administrator Connection (DAC).</span></span> <span data-ttu-id="0357e-115">這種連接可用以進行伺服器的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="0357e-115">This kind of connection is used to troubleshoot a server.</span></span> <span data-ttu-id="0357e-116">只有在支援 DAC 的伺服器電腦上才可進行。</span><span class="sxs-lookup"><span data-stu-id="0357e-116">This will only work with server computers that support DAC.</span></span> <span data-ttu-id="0357e-117">如果無法使用 DAC，`sqlcmd` 會產生一則錯誤訊息，並結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-117">If DAC is not available, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="0357e-118">如需有關 DAC 的詳細資訊，請參閱 [資料庫管理員的診斷連線](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="0357e-118">For more information about DAC, see [Diagnostic Connection for Database Administrators](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span>  
  
 <span data-ttu-id="0357e-119">**-C**</span><span class="sxs-lookup"><span data-stu-id="0357e-119">**-C**</span></span>  
 <span data-ttu-id="0357e-120">這個參數由用戶端所設定，以隱含方式信任伺服器憑證而且不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0357e-120">This switch is used by the client to configure it to implicitly trust the server certificate without validation.</span></span> <span data-ttu-id="0357e-121">這個選項相當於 ADO.NET 選項 `TRUSTSERVERCERTIFICATE = true`。</span><span class="sxs-lookup"><span data-stu-id="0357e-121">This option is equivalent to the ADO.NET option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="0357e-122">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="0357e-122">**-d** _db_name_</span></span>  
 <span data-ttu-id="0357e-123">`USE`當您啟動時，會發出*db_name*的語句 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="0357e-123">Issues a `USE` *db_name* statement when you start `sqlcmd`.</span></span> <span data-ttu-id="0357e-124">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDDBNAME。</span><span class="sxs-lookup"><span data-stu-id="0357e-124">This option sets the `sqlcmd` scripting variable SQLCMDDBNAME.</span></span> <span data-ttu-id="0357e-125">這會指定初始資料庫。</span><span class="sxs-lookup"><span data-stu-id="0357e-125">This specifies the initial database.</span></span> <span data-ttu-id="0357e-126">預設值為您登入的預設資料庫屬性。</span><span class="sxs-lookup"><span data-stu-id="0357e-126">The default is your login's default-database property.</span></span> <span data-ttu-id="0357e-127">如果資料庫不存在，會產生一則錯誤訊息，且會結束 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-127">If the database does not exist, an error message is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="0357e-128">**-l** _login_timeout_</span><span class="sxs-lookup"><span data-stu-id="0357e-128">**-l** _login_timeout_</span></span>  
 <span data-ttu-id="0357e-129">指定在您嘗試連接到伺服器時，ODBC 驅動程式之 `sqlcmd` 登入逾時之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="0357e-129">Specifies the number of seconds before a `sqlcmd` login to the ODBC driver times out when you try to connect to a server.</span></span> <span data-ttu-id="0357e-130">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDLOGINTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="0357e-130">This option sets the `sqlcmd` scripting variable SQLCMDLOGINTIMEOUT.</span></span> <span data-ttu-id="0357e-131">`sqlcmd` 的預設登入逾時值是 8 秒。</span><span class="sxs-lookup"><span data-stu-id="0357e-131">The default time-out for login to `sqlcmd` is eight seconds.</span></span> <span data-ttu-id="0357e-132">此登入逾時必須是介於 0 和 65534 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="0357e-132">The login time-out must be a number between 0 and 65534.</span></span> <span data-ttu-id="0357e-133">如果所提供的值不是數值或不在該範圍內，`sqlcmd` 就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-133">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span> <span data-ttu-id="0357e-134">0 值指定逾時值無限。</span><span class="sxs-lookup"><span data-stu-id="0357e-134">A value of 0 specifies time-out to be infinite.</span></span>  
  
 <span data-ttu-id="0357e-135">**-E**</span><span class="sxs-lookup"><span data-stu-id="0357e-135">**-E**</span></span>  
 <span data-ttu-id="0357e-136">使用信任連接登入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，而不用使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-136">Uses a trusted connection instead of using a user name and password to log on to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0357e-137">根據預設，如果沒有指定 -E，`sqlcmd` 會使用信任連接選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-137">By default, without -E specified, `sqlcmd` uses the trusted connection option.</span></span>  
  
 <span data-ttu-id="0357e-138">**-E** 選項會忽略可能出現的使用者名稱與密碼環境變數設定，例如 SQLCMDPASSWORD。</span><span class="sxs-lookup"><span data-stu-id="0357e-138">The **-E** option ignores possible user name and password environment variable settings such as SQLCMDPASSWORD.</span></span> <span data-ttu-id="0357e-139">如果同時使用 **-E** 選項和 **-U** 或 **-P** 選項，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-139">If the **-E** option is used together with the **-U** option or the **-P** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="0357e-140">**-H** _workstation_name_</span><span class="sxs-lookup"><span data-stu-id="0357e-140">**-H** _workstation_name_</span></span>  
 <span data-ttu-id="0357e-141">這是工作站名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-141">A workstation name.</span></span> <span data-ttu-id="0357e-142">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDWORKSTATION。</span><span class="sxs-lookup"><span data-stu-id="0357e-142">This option sets the `sqlcmd` scripting variable SQLCMDWORKSTATION.</span></span> <span data-ttu-id="0357e-143">工作站名稱列在 **sys.processes** 目錄檢視的 **hostname** 資料行中，而且可以使用預存程序 **sp_who** 傳回名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-143">The workstation name is listed in the **hostname** column of the **sys.processes** catalog view and can be returned using the stored procedure **sp_who**.</span></span> <span data-ttu-id="0357e-144">如果未指定這個選項，預設值為目前的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-144">If this option is not specified, the default is the current computer name.</span></span> <span data-ttu-id="0357e-145">這個名稱可用來識別不同的 `sqlcmd` 工作階段。</span><span class="sxs-lookup"><span data-stu-id="0357e-145">This name can be used to identify different `sqlcmd` sessions.</span></span>  
  
 <span data-ttu-id="0357e-146">**-K** _application_intent_</span><span class="sxs-lookup"><span data-stu-id="0357e-146">**-K** _application_intent_</span></span>  
 <span data-ttu-id="0357e-147">宣告連接到伺服器時的應用程式工作負載類型。</span><span class="sxs-lookup"><span data-stu-id="0357e-147">Declares the application workload type when connecting to a server.</span></span> <span data-ttu-id="0357e-148">目前唯一支援的值是 **ReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="0357e-148">The only currently supported value is **ReadOnly**.</span></span> <span data-ttu-id="0357e-149">若未指定 **-K**，sqlcmd 公用程式將無法支援 AlwaysOn 可用性群組中連接至次要複本。</span><span class="sxs-lookup"><span data-stu-id="0357e-149">If **-K** is not specified, the sqlcmd utility will not support connectivity to a secondary replica in an AlwaysOn availability group.</span></span> <span data-ttu-id="0357e-150">如需詳細資訊，請參閱使用中[次要資料庫：可讀取的次要複本](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="0357e-150">For more information, see [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="0357e-151">`-M`*multisubnet_failover*</span><span class="sxs-lookup"><span data-stu-id="0357e-151">`-M` *multisubnet_failover*</span></span>  
 <span data-ttu-id="0357e-152">在連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可用性群組的可用性群組接聽程式或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體時，永遠指定 `-M`。</span><span class="sxs-lookup"><span data-stu-id="0357e-152">Always specify `-M` when connecting to the availability group listener of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] availability group or a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Failover Cluster Instance.</span></span> <span data-ttu-id="0357e-153">`-M` 提供目前使用中伺服器的更快速偵測與連接。</span><span class="sxs-lookup"><span data-stu-id="0357e-153">`-M` provides for faster detection of and connection to the (currently) active server.</span></span> <span data-ttu-id="0357e-154">如果未指定 `-M`，`-M` 為關閉。</span><span class="sxs-lookup"><span data-stu-id="0357e-154">If `-M` is not specified, `-M` is off.</span></span> <span data-ttu-id="0357e-155">如需的詳細資訊 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] ，請參閱[可用性群組接聽程式、用戶端連線性和應用程式容錯移轉 &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md)、[建立和設定可用性群組 &#40;SQL Server ](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)&#41;、[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)SQL Server&#41;和作用中[次要複本：可讀取的次要複本](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="0357e-155">For more information about [!INCLUDE[ssHADR](../includes/sshadr-md.md)], see [Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md), and [Active Secondaries: Readable Secondary Replicas](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .</span></span>  
  
 <span data-ttu-id="0357e-156">**-N**</span><span class="sxs-lookup"><span data-stu-id="0357e-156">**-N**</span></span>  
 <span data-ttu-id="0357e-157">用戶端會用這個參數要求加密的連接。</span><span class="sxs-lookup"><span data-stu-id="0357e-157">This switch is used by the client to request an encrypted connection.</span></span>  
  
 <span data-ttu-id="0357e-158">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="0357e-158">**-P** _password_</span></span>  
 <span data-ttu-id="0357e-159">這是一個使用者指定的密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-159">Is a user-specified password.</span></span> <span data-ttu-id="0357e-160">密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0357e-160">Passwords are case sensitive.</span></span> <span data-ttu-id="0357e-161">如果使用-U 選項，但未使用 **-P**選項，且未設定 SQLCMDPASSWORD 環境變數，則 `sqlcmd` 會提示使用者輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-161">If the -U option is used and the **-P** option is not used, and the SQLCMDPASSWORD environment variable has not been set, `sqlcmd` prompts the user for a password.</span></span> <span data-ttu-id="0357e-162">如果在沒有密碼的情況下，于命令提示字元的結尾使用 **-P**選項，則會 `sqlcmd` 使用預設密碼 (Null) 。</span><span class="sxs-lookup"><span data-stu-id="0357e-162">If the **-P** option is used at the end of the command prompt without a password `sqlcmd` uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0357e-163">請勿使用空白密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-163">Do not use a blank password.</span></span> <span data-ttu-id="0357e-164">請使用增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-164">Use a strong password.</span></span> <span data-ttu-id="0357e-165">如需詳細資訊，請參閱 [Strong Passwords](../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="0357e-165">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="0357e-166">密碼提示的顯示方式，會以將密碼提示輸出到主控台的方式顯示，如： `Password:`</span><span class="sxs-lookup"><span data-stu-id="0357e-166">The password prompt is displayed by printing the password prompt to the console, as follows: `Password:`</span></span>  
  
 <span data-ttu-id="0357e-167">使用者輸入為隱藏狀態。</span><span class="sxs-lookup"><span data-stu-id="0357e-167">User input is hidden.</span></span> <span data-ttu-id="0357e-168">這表示畫面上不會顯示任何內容，而且游標也不會移動。</span><span class="sxs-lookup"><span data-stu-id="0357e-168">This means that nothing is displayed and the cursor stays in position.</span></span>  
  
 <span data-ttu-id="0357e-169">SQLCMDPASSWORD 環境變數可讓您設定目前工作階段的預設密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-169">The SQLCMDPASSWORD environment variable lets you set a default password for the current session.</span></span> <span data-ttu-id="0357e-170">因此，您不需要將密碼寫在批次檔中。</span><span class="sxs-lookup"><span data-stu-id="0357e-170">Therefore, passwords do not have to be hard-coded into batch files.</span></span>  
  
 <span data-ttu-id="0357e-171">下列範例會先在命令提示字元處設定 SQLCMDPASSWORD 變數，再存取 `sqlcmd` 公用程式。</span><span class="sxs-lookup"><span data-stu-id="0357e-171">The following example first sets the SQLCMDPASSWORD variable at the command prompt and then accesses the `sqlcmd` utility.</span></span> <span data-ttu-id="0357e-172">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-172">At the command prompt, type:</span></span>  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0357e-173">任何能夠見到您的電腦監視器的人，都能夠見到密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-173">The password will be visible to anyone who can see your computer monitor.</span></span>  
  
 <span data-ttu-id="0357e-174">請在下列命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-174">At the following command prompt, type:</span></span>  
  
 `sqlcmd`  
  
 <span data-ttu-id="0357e-175">如果使用者名稱和密碼的組合不正確，會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-175">If the user name and password combination is incorrect, an error message is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-176">保留 OSQLPASSWORD 環境變數的目的是為了與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="0357e-176">The OSQLPASSWORD environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="0357e-177">SQLCMDPASSWORD 環境變數優先于 OSQLPASSWORD 環境變數;這表示 `sqlcmd` 和**osql**可以在彼此不受干擾的情況下使用，而且舊的腳本仍會繼續工作。</span><span class="sxs-lookup"><span data-stu-id="0357e-177">The SQLCMDPASSWORD environment variable takes precedence over the OSQLPASSWORD environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="0357e-178">如果同時使用 **-P** 選項和 **-E** 選項，就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-178">If the **-P** option is used with the **-E** option, an error message is generated.</span></span>  
  
 <span data-ttu-id="0357e-179">如果 **-P** 選項後面有多個引數，便會產生錯誤訊息，而且程式將會結束。</span><span class="sxs-lookup"><span data-stu-id="0357e-179">If the **-P** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="0357e-180">**-S** [*通訊協定*：]*伺服器*[ **\\** _instance_name_] [**，**_埠_]</span><span class="sxs-lookup"><span data-stu-id="0357e-180">**-S** [*protocol*:]*server*[**\\**_instance_name_][**,**_port_]</span></span>  
 <span data-ttu-id="0357e-181">指定要連接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0357e-181">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to which to connect.</span></span> <span data-ttu-id="0357e-182">它會設定 `sqlcmd` 指令碼變數 SQLCMDSERVER。</span><span class="sxs-lookup"><span data-stu-id="0357e-182">It sets the `sqlcmd` scripting variable SQLCMDSERVER.</span></span>  
  
 <span data-ttu-id="0357e-183">指定 *server_name*，即可連接至該伺服器電腦上之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="0357e-183">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="0357e-184">指定*server_name* [ **\\** _instance_name_ ]，以連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 該伺服器電腦上的已命名實例。</span><span class="sxs-lookup"><span data-stu-id="0357e-184">Specify *server_name* [ **\\**_instance_name_ ] to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server computer.</span></span> <span data-ttu-id="0357e-185">如果未指定伺服器電腦，`sqlcmd` 會連接到本機電腦上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="0357e-185">If no server computer is specified, `sqlcmd` connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="0357e-186">當您從網路的遠端電腦執行 `sqlcmd` 時，需要這個選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-186">This option is required when you execute `sqlcmd` from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="0357e-187">*通訊協定*可以 `tcp` (tcp/ip) 、 `lpc` (共用記憶體) ，或 `np` (具名管道) 。</span><span class="sxs-lookup"><span data-stu-id="0357e-187">*protocol* can be `tcp` (TCP/IP), `lpc` (shared memory), or `np` (named pipes).</span></span>  
  
 <span data-ttu-id="0357e-188">如果您在啟動時未指定*server_name* [ **\\** _instance_name_ ]，會 `sqlcmd` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 檢查並使用 SQLCMDSERVER 環境變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-188">If you do not specify a *server_name* [ **\\**_instance_name_ ] when you start `sqlcmd`, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for and uses the SQLCMDSERVER environment variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-189">保留 OSQLSERVER 環境變數的目的是為了與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="0357e-189">The OSQLSERVER environment variable has been kept for backward compatibility.</span></span> <span data-ttu-id="0357e-190">SQLCMDSERVER 環境變數優先于 OSQLSERVER 環境變數;這表示 `sqlcmd` 和**osql**可以在彼此不受干擾的情況下使用，而且舊的腳本仍會繼續工作。</span><span class="sxs-lookup"><span data-stu-id="0357e-190">The SQLCMDSERVER environment variable takes precedence over the OSQLSERVER environment variable; this means that `sqlcmd` and **osql** can be used next to each other without interference and that old scripts will continue to work.</span></span>  
  
 <span data-ttu-id="0357e-191">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="0357e-191">**-U** _login_id_</span></span>  
 <span data-ttu-id="0357e-192">這是使用者登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-192">Is the user login ID.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-193">可利用 OSQLUSER 環境變數達到回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="0357e-193">The OSQLUSER environment variable is available for backward compatibility.</span></span> <span data-ttu-id="0357e-194">SQLCMDUSER 環境變數優先於 OSQLUSER 環境變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-194">The SQLCMDUSER environment variable takes precedence over the OSQLUSER environment variable.</span></span> <span data-ttu-id="0357e-195">這表示您 `sqlcmd` 可以在彼此旁使用和**osql** ，而不會互相干擾。</span><span class="sxs-lookup"><span data-stu-id="0357e-195">This means that `sqlcmd` and **osql** can be used next to each other without interference.</span></span> <span data-ttu-id="0357e-196">這也表示現有的 **osql** 指令碼仍然有效。</span><span class="sxs-lookup"><span data-stu-id="0357e-196">It also means that existing **osql** scripts will continue to work.</span></span>  
  
 <span data-ttu-id="0357e-197">如果沒有指定 **-U**選項或 **-P**選項，則會 `sqlcmd` 嘗試使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 驗證模式進行連接。</span><span class="sxs-lookup"><span data-stu-id="0357e-197">If neither the **-U** option nor the **-P** option is specified, `sqlcmd` tries to connect by using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication mode.</span></span> <span data-ttu-id="0357e-198">這項驗證以執行 `sqlcmd` 之使用者的 Windows 帳戶為基礎。</span><span class="sxs-lookup"><span data-stu-id="0357e-198">Authentication is based on the Windows account of the user who is running `sqlcmd`.</span></span>  
  
 <span data-ttu-id="0357e-199">如果同時使用 **-U** 選項和 **-E** 選項 (本主題稍後將說明)，便會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-199">If the **-U** option is used with the **-E** option (described later in this topic), an error message is generated.</span></span> <span data-ttu-id="0357e-200">如果 **-U** 選項後面有多個引數，就會產生錯誤訊息並結束程式。</span><span class="sxs-lookup"><span data-stu-id="0357e-200">If the **-U** option is followed by more than one argument, an error message is generated and the program exits.</span></span>  
  
 <span data-ttu-id="0357e-201">**-z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="0357e-201">**-z** _new_password_</span></span>  
 <span data-ttu-id="0357e-202">變更密碼：</span><span class="sxs-lookup"><span data-stu-id="0357e-202">Change password:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="0357e-203">**-Z** _new_password_</span><span class="sxs-lookup"><span data-stu-id="0357e-203">**-Z** _new_password_</span></span>  
 <span data-ttu-id="0357e-204">變更密碼並結束：</span><span class="sxs-lookup"><span data-stu-id="0357e-204">Change password and exit:</span></span>  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 <span data-ttu-id="0357e-205">**輸入/輸出選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-205">**Input/Output Options**</span></span>  
  <span data-ttu-id="0357e-206">**-f** _codepage_ | **i:** _codepage_[ **,o:** _codepage_] | **o:** _codepage_[ **,i:** _codepage_]</span><span class="sxs-lookup"><span data-stu-id="0357e-206">**-f** _codepage_ | **i:**_codepage_[**,o:**_codepage_] | **o:**_codepage_[**,i:**_codepage_]</span></span>  
 <span data-ttu-id="0357e-207">指定輸入和輸出字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0357e-207">Specifies the input and output code pages.</span></span> <span data-ttu-id="0357e-208">字碼頁碼是一個數值，指定已安裝的 Windows 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0357e-208">The codepage number is a numeric value that specifies an installed Windows code page.</span></span>  
  
 <span data-ttu-id="0357e-209">字碼頁轉換規則：</span><span class="sxs-lookup"><span data-stu-id="0357e-209">Code-page conversion rules:</span></span>  
  
-   <span data-ttu-id="0357e-210">如果未指定字碼頁，則 `sqlcmd` 會在輸入檔和輸出檔中使用目前的字碼頁，除非輸入檔是 Unicode 檔，否則就不需要轉換。</span><span class="sxs-lookup"><span data-stu-id="0357e-210">If no code pages are specified, `sqlcmd` will use the current code page for both input and output files, unless the input file is a Unicode file, in which case no conversion is required.</span></span>  
  
-   <span data-ttu-id="0357e-211">`sqlcmd` 會自動識別位元組由大到小 (Big-Endian) 和位元組由小到大 (Little-Endian) 的 Unicode 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="0357e-211">`sqlcmd` automatically recognizes both big-endian and little-endian Unicode input files.</span></span> <span data-ttu-id="0357e-212">如果已指定 **-u** 選項，則輸出一律為位元組由小到大的 Unicode。</span><span class="sxs-lookup"><span data-stu-id="0357e-212">If the **-u** option has been specified, the output will always be little-endian Unicode.</span></span>  
  
-   <span data-ttu-id="0357e-213">如果未指定輸出檔，則輸出字碼頁會是主控台字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0357e-213">If no output file is specified, the output code page will be the console code page.</span></span> <span data-ttu-id="0357e-214">這可讓輸出正確地顯示在主控台上。</span><span class="sxs-lookup"><span data-stu-id="0357e-214">This enables the output to be displayed correctly on the console.</span></span>  
  
-   <span data-ttu-id="0357e-215">假設多個輸入檔都是相同的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0357e-215">Multiple input files are assumed to be of the same code page.</span></span> <span data-ttu-id="0357e-216">Unicode 與非 Unicode 的輸入檔可以混合使用。</span><span class="sxs-lookup"><span data-stu-id="0357e-216">Unicode and non-Unicode input files can be mixed.</span></span>  
  
 <span data-ttu-id="0357e-217">在命令提示字元下輸入 `chcp`，以驗證 Cmd.exe 的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0357e-217">Enter `chcp` at the command prompt to verify the code page of Cmd.exe.</span></span>  
  
 <span data-ttu-id="0357e-218">**-i** _input_file_[**，**_input_file2_...]</span><span class="sxs-lookup"><span data-stu-id="0357e-218">**-i** _input_file_[**,**_input_file2_...]</span></span>  
 <span data-ttu-id="0357e-219">識別包含 SQL 陳述式或預存程序的批次之檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-219">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="0357e-220">您可以指定多個檔案，它們會依照順序加以讀取和處理。</span><span class="sxs-lookup"><span data-stu-id="0357e-220">Multiple files may be specified that will be read and processed in order.</span></span> <span data-ttu-id="0357e-221">檔案名稱之間不能有空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-221">Do not use any spaces between file names.</span></span> <span data-ttu-id="0357e-222">`sqlcmd` 會先檢查指定的檔案是否全部存在。</span><span class="sxs-lookup"><span data-stu-id="0357e-222">`sqlcmd` will first check to see whether all the specified files exist.</span></span> <span data-ttu-id="0357e-223">如果有一個或多個檔案不存在，`sqlcmd` 會結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-223">If one or more files do not exist, `sqlcmd` will exit.</span></span> <span data-ttu-id="0357e-224">-i 和 -Q/-q 為互斥選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-224">The -i and the -Q/-q options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0357e-225">路徑範例：</span><span class="sxs-lookup"><span data-stu-id="0357e-225">Path examples:</span></span>  
  
 <span data-ttu-id="0357e-226">**-i**C： \\<檔案名\></span><span class="sxs-lookup"><span data-stu-id="0357e-226">**-i** C:\\<filename\></span></span>  
  
 <span data-ttu-id="0357e-227">**-i** \\ \\<Server \> \\<共用 $>\\<檔案名\></span><span class="sxs-lookup"><span data-stu-id="0357e-227">**-i** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="0357e-228">**-i** "C:\Some Folder\\<檔案名稱\>"</span><span class="sxs-lookup"><span data-stu-id="0357e-228">**-i** "C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="0357e-229">包含空格的檔案路徑必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="0357e-229">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="0357e-230">此選項可以使用一次以上： **-i**_input_file_ **-i**_input_file。_</span><span class="sxs-lookup"><span data-stu-id="0357e-230">This option may be used more than once: **-i**_input_file_ **-I**_I input_file._</span></span>  
  
 <span data-ttu-id="0357e-231">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="0357e-231">**-o** _output_file_</span></span>  
 <span data-ttu-id="0357e-232">識別用來接收 `sqlcmd` 輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-232">Identifies the file that receives output from `sqlcmd`.</span></span>  
  
 <span data-ttu-id="0357e-233">如果指定 **-u** ， *output_file* 會以 Unicode 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="0357e-233">If **-u** is specified, the *output_file* is stored in Unicode format.</span></span> <span data-ttu-id="0357e-234">如果檔案名稱無效，會產生一則錯誤訊息，且會結束 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-234">If the file name is not valid, an error message is generated, and `sqlcmd` exits.</span></span> <span data-ttu-id="0357e-235">`sqlcmd` 不支援同時將多個 `sqlcmd` 處理序寫入相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-235">`sqlcmd` does not support concurrent writing of multiple `sqlcmd` processes to the same file.</span></span> <span data-ttu-id="0357e-236">檔案輸出會損毀或不正確。</span><span class="sxs-lookup"><span data-stu-id="0357e-236">The file output will be corrupted or incorrect.</span></span> <span data-ttu-id="0357e-237">如需檔案格式的詳細資訊，請參閱 **-f** 參數。</span><span class="sxs-lookup"><span data-stu-id="0357e-237">See the **-f** switch for more information about file formats.</span></span> <span data-ttu-id="0357e-238">如果不存在，則會建立這個檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-238">This file will be created if it does not exist.</span></span> <span data-ttu-id="0357e-239">並覆寫先前 `sqlcmd` 工作階段所產生的同名檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-239">A file of the same name from a prior `sqlcmd` session will be overwritten.</span></span> <span data-ttu-id="0357e-240">此處所指定的檔案並不是 **stdout** 檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-240">The file specified here is not the **stdout** file.</span></span> <span data-ttu-id="0357e-241">如果指定**stdout**檔案，則不會使用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-241">If a **stdout** file is specified this file will not be used.</span></span>  
  
 <span data-ttu-id="0357e-242">路徑範例：</span><span class="sxs-lookup"><span data-stu-id="0357e-242">Path examples:</span></span>  
  
 <span data-ttu-id="0357e-243">**-o**C： \\< filename></span><span class="sxs-lookup"><span data-stu-id="0357e-243">**-o** C:\\< filename></span></span>  
  
 <span data-ttu-id="0357e-244">**-o** \\ \\<Server \> \\<共用 $>\\<檔案名\></span><span class="sxs-lookup"><span data-stu-id="0357e-244">**-o** \\\\<Server\>\\<Share$>\\<filename\></span></span>  
  
 <span data-ttu-id="0357e-245">**-o "** C:\Some Folder\\<檔案名稱\>"</span><span class="sxs-lookup"><span data-stu-id="0357e-245">**-o "** C:\Some Folder\\<file name\>"</span></span>  
  
 <span data-ttu-id="0357e-246">包含空格的檔案路徑必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="0357e-246">File paths that contain spaces must be enclosed in quotation marks.</span></span>  
  
 <span data-ttu-id="0357e-247">**-r**[**0** | **1**]</span><span class="sxs-lookup"><span data-stu-id="0357e-247">**-r**[**0** | **1**]</span></span>  
 <span data-ttu-id="0357e-248">將錯誤訊息輸出重新導向至畫面 (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="0357e-248">Redirects the error message output to the screen (**stderr**).</span></span> <span data-ttu-id="0357e-249">如果您沒有指定參數，或指定 **0**，只會重新導向嚴重性層級 11 (含) 以上的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-249">If you do not specify a parameter or if you specify **0**, only error messages that have a severity level of 11 or higher are redirected.</span></span> <span data-ttu-id="0357e-250">如果您指定 **1**，便會重新導向包括 PRINT 在內的所有錯誤訊息輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-250">If you specify **1**, all error message output including PRINT is redirected.</span></span> <span data-ttu-id="0357e-251">如果您使用 -o，不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="0357e-251">Has no effect if you use -o.</span></span> <span data-ttu-id="0357e-252">根據預設，訊息會傳送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-252">By default, messages are sent to **stdout**.</span></span>  
  
 <span data-ttu-id="0357e-253">**-R**</span><span class="sxs-lookup"><span data-stu-id="0357e-253">**-R**</span></span>  
 <span data-ttu-id="0357e-254">會 `sqlcmd` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 根據用戶端的地區設定，將從抓取的數值、貨幣、日期和時間資料行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="0357e-254">Causes `sqlcmd` to localize numeric, currency, date, and time columns retrieved from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] based on the client's locale.</span></span> <span data-ttu-id="0357e-255">根據預設，這些資料行會使用伺服器的地區設定來顯示。</span><span class="sxs-lookup"><span data-stu-id="0357e-255">By default, these columns are displayed using the server's regional settings.</span></span>  
  
 <span data-ttu-id="0357e-256">**-u**</span><span class="sxs-lookup"><span data-stu-id="0357e-256">**-u**</span></span>  
 <span data-ttu-id="0357e-257">指定無論 *input_file* 的格式為何， *output_file*均以 Unicode 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="0357e-257">Specifies that *output_file* is stored in Unicode format, regardless of the format of *input_file*.</span></span>  
  
 <span data-ttu-id="0357e-258">**查詢執行選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-258">**Query Execution Options**</span></span>  
  <span data-ttu-id="0357e-259">**-e**</span><span class="sxs-lookup"><span data-stu-id="0357e-259">**-e**</span></span>  
 <span data-ttu-id="0357e-260">將輸入指令碼寫入標準的輸出裝置 (**stdout**) 中。</span><span class="sxs-lookup"><span data-stu-id="0357e-260">Writes input scripts to the standard output device (**stdout**).</span></span>  
  
 <span data-ttu-id="0357e-261">**-I**</span><span class="sxs-lookup"><span data-stu-id="0357e-261">**-I**</span></span>  
 <span data-ttu-id="0357e-262">將 SET QUOTED_IDENTIFIER 連接選項設為 ON。</span><span class="sxs-lookup"><span data-stu-id="0357e-262">Sets the SET QUOTED_IDENTIFIER connection option to ON.</span></span> <span data-ttu-id="0357e-263">依預設，此選項設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="0357e-263">By default, it is set to OFF.</span></span> <span data-ttu-id="0357e-264">如需詳細資訊，請參閱 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0357e-264">For more information, see [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).</span></span>  
  
 <span data-ttu-id="0357e-265">**-q"** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="0357e-265">**-q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="0357e-266">當 `sqlcmd` 啟動時執行查詢，但查詢結束執行後不要退出 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-266">Executes a query when `sqlcmd` starts, but does not exit `sqlcmd` when the query has finished running.</span></span> <span data-ttu-id="0357e-267">可以執行多項以分號分隔的查詢。</span><span class="sxs-lookup"><span data-stu-id="0357e-267">Multiple-semicolon-delimited queries can be executed.</span></span> <span data-ttu-id="0357e-268">請依照下列範例所示，利用引號來括住查詢。</span><span class="sxs-lookup"><span data-stu-id="0357e-268">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0357e-269">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-269">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0357e-270">請勿在查詢中使用 GO 結束字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-270">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="0357e-271">如果使用此選項時指定了 `-b`，`sqlcmd` 會發生錯誤，並結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-271">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="0357e-272">本主題稍後將說明 `-b`。</span><span class="sxs-lookup"><span data-stu-id="0357e-272">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="0357e-273">**-Q "** _cmdline query_ **"**</span><span class="sxs-lookup"><span data-stu-id="0357e-273">**-Q"** _cmdline query_ **"**</span></span>  
 <span data-ttu-id="0357e-274">啟動 `sqlcmd` 時執行查詢，然後立即退出 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-274">Executes a query when `sqlcmd` starts and then immediately exits `sqlcmd`.</span></span> <span data-ttu-id="0357e-275">可以執行多項以分號分隔的查詢。</span><span class="sxs-lookup"><span data-stu-id="0357e-275">Multiple-semicolon-delimited queries can be executed.</span></span>  
  
 <span data-ttu-id="0357e-276">請依照下列範例所示，利用引號來括住查詢。</span><span class="sxs-lookup"><span data-stu-id="0357e-276">Use quotation marks around the query, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0357e-277">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-277">At the command prompt, type:</span></span>  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0357e-278">請勿在查詢中使用 GO 結束字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-278">Do not use the GO terminator in the query.</span></span>  
  
 <span data-ttu-id="0357e-279">如果使用此選項時指定了 `-b`，`sqlcmd` 會發生錯誤，並結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-279">If `-b` is specified together with this option, `sqlcmd` exits on error.</span></span> <span data-ttu-id="0357e-280">本主題稍後將說明 `-b`。</span><span class="sxs-lookup"><span data-stu-id="0357e-280">`-b` is described later in this topic.</span></span>  
  
 <span data-ttu-id="0357e-281">**-t** _query_timeout_</span><span class="sxs-lookup"><span data-stu-id="0357e-281">**-t** _query_timeout_</span></span>  
 <span data-ttu-id="0357e-282">指定命令 (或 SQL 語句) 超時之前的秒數。此選項會設定 `sqlcmd` 腳本變數 SQLCMDSTATTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="0357e-282">Specifies the number of seconds before a command (or SQL statement) times out. This option sets the `sqlcmd` scripting variable SQLCMDSTATTIMEOUT.</span></span> <span data-ttu-id="0357e-283">如果未指定 *time_out* 值，命令不會逾時。*query\*\*time_out* 必須是介於 1 與 65534 之間的數字。</span><span class="sxs-lookup"><span data-stu-id="0357e-283">If a *time_out* value is not specified, the command does not time out. The *query\*\*time_out* must be a number between 1 and 65534.</span></span> <span data-ttu-id="0357e-284">如果所提供的值不是數值或不在該範圍內，`sqlcmd` 就會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-284">If the value supplied is not numeric or does not fall into that range, `sqlcmd` generates an error message.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-285">實際逾時值可能與指定的 *time_out* 值之間有幾秒的差異。</span><span class="sxs-lookup"><span data-stu-id="0357e-285">The actual time out value may vary from the specified *time_out* value by several seconds.</span></span>  
  
 <span data-ttu-id="0357e-286">**-vvar =** _value_[ **var =** _value_...]</span><span class="sxs-lookup"><span data-stu-id="0357e-286">**-vvar =** _value_[ **var =** _value_...]</span></span>  
 <span data-ttu-id="0357e-287">建立 `sqlcmd` 可在腳本中使用的腳本變數 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="0357e-287">Creates a `sqlcmd`scripting variable that can be used in a `sqlcmd` script.</span></span> <span data-ttu-id="0357e-288">如果值包含空格，請用引號括住該值。</span><span class="sxs-lookup"><span data-stu-id="0357e-288">Enclose the value in quotation marks if the value contains spaces.</span></span> <span data-ttu-id="0357e-289">您可以指定多個**_var_** = **" *`values`* "** 值。</span><span class="sxs-lookup"><span data-stu-id="0357e-289">You can specify multiple **_var_**=**"*`values`*"** values.</span></span> <span data-ttu-id="0357e-290">如果指定的任何值發生錯誤，`sqlcmd` 會產生一則錯誤訊息，並結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-290">If there are errors in any of the values specified, `sqlcmd` generates an error message and then exits.</span></span>  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 <span data-ttu-id="0357e-291">**-x**</span><span class="sxs-lookup"><span data-stu-id="0357e-291">**-x**</span></span>  
 <span data-ttu-id="0357e-292">讓 `sqlcmd` 忽略指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-292">Causes `sqlcmd` to ignore scripting variables.</span></span> <span data-ttu-id="0357e-293">當指令碼所包含的許多 INSERT 陳述式可能含有與一般變數 (例如 $(*variable_name*)) 相同格式的字串時，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="0357e-293">This is useful when a script contains many INSERT statements that may contain strings that have the same format as regular variables, such as $(*variable_name*).</span></span>  
  
 <span data-ttu-id="0357e-294">**格式化選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-294">**Formatting Options**</span></span>  
  <span data-ttu-id="0357e-295">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="0357e-295">**-h** _headers_</span></span>  
 <span data-ttu-id="0357e-296">指定資料行標頭之間所要列印的資料列數。</span><span class="sxs-lookup"><span data-stu-id="0357e-296">Specifies the number of rows to print between the column headings.</span></span> <span data-ttu-id="0357e-297">預設值是每一組查詢結果各列印一次標頭。</span><span class="sxs-lookup"><span data-stu-id="0357e-297">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="0357e-298">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDHEADERS。</span><span class="sxs-lookup"><span data-stu-id="0357e-298">This option sets the `sqlcmd` scripting variable SQLCMDHEADERS.</span></span> <span data-ttu-id="0357e-299">請利用 **-1** 來指定不列印標頭。</span><span class="sxs-lookup"><span data-stu-id="0357e-299">Use **-1** to specify that headers must not be printed.</span></span> <span data-ttu-id="0357e-300">任何無效的值都會讓 `sqlcmd` 產生錯誤訊息，並結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-300">Any value that is not valid causes `sqlcmd` to generate an error message and then exit.</span></span>  
  
 <span data-ttu-id="0357e-301">**-k** [**1** | **2**]</span><span class="sxs-lookup"><span data-stu-id="0357e-301">**-k** [**1** | **2**]</span></span>  
 <span data-ttu-id="0357e-302">從輸出中移除所有控制字元，如定位字元和新行字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-302">Removes all control characters, such as tabs and new line characters from the output.</span></span> <span data-ttu-id="0357e-303">這會在資料傳回時，保留資料行的格式。</span><span class="sxs-lookup"><span data-stu-id="0357e-303">This preserves column formatting when data is returned.</span></span> <span data-ttu-id="0357e-304">如果指定 1，會用單一空格來取代控制字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-304">If 1 is specified, the control characters are replaced by a single space.</span></span> <span data-ttu-id="0357e-305">如果指定 2，會用單一空格取代連續控制字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-305">If 2 is specified, consecutive control characters are replaced by a single space.</span></span> <span data-ttu-id="0357e-306">**-k** 與 **-k1**相同。</span><span class="sxs-lookup"><span data-stu-id="0357e-306">**-k** is the same as **-k1**.</span></span>  
  
 <span data-ttu-id="0357e-307">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="0357e-307">**-s** _col_separator_</span></span>  
 <span data-ttu-id="0357e-308">指定資料行分隔字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-308">Specifies the column-separator character.</span></span> <span data-ttu-id="0357e-309">預設值是空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-309">The default is a blank space.</span></span> <span data-ttu-id="0357e-310">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDCOLSEP。</span><span class="sxs-lookup"><span data-stu-id="0357e-310">This option sets the `sqlcmd` scripting variable SQLCMDCOLSEP.</span></span> <span data-ttu-id="0357e-311">若要使用對作業系統有特殊意義的字元，如連字號 (&) 或分號 (;)，請用引號 (") 括住該字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-311">To use characters that have special meaning to the operating system such as the ampersand (&), or semicolon (;), enclose the character in quotation marks (").</span></span> <span data-ttu-id="0357e-312">資料行分隔字元可以是任何 8 位元的字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-312">The column separator can be any 8-bit character.</span></span>  
  
 <span data-ttu-id="0357e-313">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="0357e-313">**-w** _column_width_</span></span>  
 <span data-ttu-id="0357e-314">指定輸出的螢幕寬度。</span><span class="sxs-lookup"><span data-stu-id="0357e-314">Specifies the screen width for output.</span></span> <span data-ttu-id="0357e-315">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDCOLWIDTH。</span><span class="sxs-lookup"><span data-stu-id="0357e-315">This option sets the `sqlcmd` scripting variable SQLCMDCOLWIDTH.</span></span> <span data-ttu-id="0357e-316">資料行寬度必須是大於 8 且小於 65536 的數字。</span><span class="sxs-lookup"><span data-stu-id="0357e-316">The column width must be a number greater than 8 and less than 65536.</span></span> <span data-ttu-id="0357e-317">如果指定的資料行寬度不在該範圍內，`sqlcmd` 會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-317">If the specified column width does not fall into that range, `sqlcmd` generates and error message.</span></span> <span data-ttu-id="0357e-318">預設寬度是 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-318">The default width is 80 characters.</span></span> <span data-ttu-id="0357e-319">當輸出行超出指定的資料行寬度時，它會折行。</span><span class="sxs-lookup"><span data-stu-id="0357e-319">When an output line exceeds the specified column width, it wraps on to the next line.</span></span>  
  
 <span data-ttu-id="0357e-320">**-W**</span><span class="sxs-lookup"><span data-stu-id="0357e-320">**-W**</span></span>  
 <span data-ttu-id="0357e-321">這個選項會從資料行中移除尾端的空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-321">This option removes trailing spaces from a column.</span></span> <span data-ttu-id="0357e-322">在準備要匯出至另一個應用程式的資料時，請使用 **-s** 選項與這個選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-322">Use this option together with the **-s** option when preparing data that is to be exported to another application.</span></span> <span data-ttu-id="0357e-323">這個選項不能搭配 **-y** 或 **-Y** 選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="0357e-323">Cannot be used with the **-y** or **-Y** options.</span></span>  
  
 <span data-ttu-id="0357e-324">**-y** _variable_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="0357e-324">**-y** _variable_length_type_display_width_</span></span>  
 <span data-ttu-id="0357e-325">設定 `sqlcmd` 指令碼變數 SQLCMDMAXVARTYPEWIDTH。</span><span class="sxs-lookup"><span data-stu-id="0357e-325">Sets the `sqlcmd` scripting variable SQLCMDMAXVARTYPEWIDTH.</span></span> <span data-ttu-id="0357e-326">預設值是 256。</span><span class="sxs-lookup"><span data-stu-id="0357e-326">The default is 256.</span></span> <span data-ttu-id="0357e-327">這會限制大型可變長度資料類型的傳回字元數：</span><span class="sxs-lookup"><span data-stu-id="0357e-327">It limits the number of characters that are returned for the large variable length data types:</span></span>  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-328">UDT 可以是固定長度，這會隨著實作情況而不同。</span><span class="sxs-lookup"><span data-stu-id="0357e-328">UDTs can be of fixed length depending on the implementation.</span></span> <span data-ttu-id="0357e-329">如果固定長度 UDT 的長度小於 *display_width*，傳回的 UDT 值不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="0357e-329">If this length of a fixed length UDT is shorter that *display_width*, the value of the UDT returned is not affected.</span></span> <span data-ttu-id="0357e-330">不過，如果長度超出 *display_width*，便會截斷輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-330">However, if the length is longer than *display_width*, the output is truncated.</span></span>  
  
 
> [!IMPORTANT]  
>  <span data-ttu-id="0357e-331">使用 **-y 0** 選項時，要非常小心，因為它可能會讓伺服器和網路出現嚴重的效能問題，這會隨著傳回的資料大小而不同。</span><span class="sxs-lookup"><span data-stu-id="0357e-331">Use the **-y 0** option with extreme caution because it may cause serious performance issues on both the server and the network, depending on the size of data returned.</span></span>  
  
 <span data-ttu-id="0357e-332">**-Y** _fixed_length_type_display_width_</span><span class="sxs-lookup"><span data-stu-id="0357e-332">**-Y** _fixed_length_type_display_width_</span></span>  
 <span data-ttu-id="0357e-333">設定 `sqlcmd` 指令碼變數 SQLCMDMAXFIXEDTYPEWIDTH。</span><span class="sxs-lookup"><span data-stu-id="0357e-333">Sets the `sqlcmd` scripting variable SQLCMDMAXFIXEDTYPEWIDTH.</span></span> <span data-ttu-id="0357e-334">預設值是 0 (無限制)。</span><span class="sxs-lookup"><span data-stu-id="0357e-334">The default is 0 (unlimited).</span></span> <span data-ttu-id="0357e-335">限制針對下列資料類型傳回的字元數：</span><span class="sxs-lookup"><span data-stu-id="0357e-335">Limits the number of characters that are returned for the following data types:</span></span>  
  
-   <span data-ttu-id="0357e-336">`char(`*n* `)` ，其中 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="0357e-336">`char(` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="0357e-337">`nchar(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="0357e-337">`nchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="0357e-338">`varchar(n`*n* `)` ，其中 1<= n<= 8000</span><span class="sxs-lookup"><span data-stu-id="0357e-338">`varchar(n` *n* `)`, where 1<=n<=8000</span></span>  
  
-   <span data-ttu-id="0357e-339">`nvarchar(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="0357e-339">`nvarchar(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   <span data-ttu-id="0357e-340">`varbinary(n`*n* `)` ，其中 1<= n<= 4000</span><span class="sxs-lookup"><span data-stu-id="0357e-340">`varbinary(n` *n* `)`, where 1<=n<=4000</span></span>  
  
-   `variant`  
  
 <span data-ttu-id="0357e-341">**錯誤報告選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-341">**Error Reporting Options**</span></span>  
  `-b`  
 <span data-ttu-id="0357e-342">指定在發生錯誤時，`sqlcmd` 會結束作業並傳回 DOS ERRORLEVEL 值。</span><span class="sxs-lookup"><span data-stu-id="0357e-342">Specifies that `sqlcmd` exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="0357e-343">當 **錯誤訊息的嚴重性層級大於 10 時，傳回 DOS ERRORLEVEL 變數的值是** 1 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ；否則，傳回的值是 **0**。</span><span class="sxs-lookup"><span data-stu-id="0357e-343">The value that is returned to the DOS ERRORLEVEL variable is **1** when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity level greater than 10; otherwise, the value returned is **0**.</span></span> <span data-ttu-id="0357e-344">如果除了設定 `-V` 以外，還設定了 `-b` 選項，且嚴重性層級低於使用 `-V` 所設定的值，則 `sqlcmd` 不會報告發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0357e-344">If the `-V` option has been set in addition to `-b`, `sqlcmd` will not report an error if the severity level is lower than the values set using `-V`.</span></span> <span data-ttu-id="0357e-345">命令提示字元批次檔案可以測試 ERRORLEVEL 的值，而且能夠適當地處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="0357e-345">Command prompt batch files can test the value of ERRORLEVEL and handle the error appropriately.</span></span> <span data-ttu-id="0357e-346">`sqlcmd` 不會報告嚴重性層級 10 (參考用訊息) 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0357e-346">`sqlcmd` does not report errors for severity level 10 (informational messages).</span></span>  
  
 <span data-ttu-id="0357e-347">如果 `sqlcmd` 指令碼包含不正確的命令、語法錯誤，或遺漏指令碼變數，則傳回的 ERRORLEVEL 便是 1。</span><span class="sxs-lookup"><span data-stu-id="0357e-347">If the `sqlcmd` script contains an incorrect comment, syntax error, or is missing a scripting variable, ERRORLEVEL returned is 1.</span></span>  
  
 <span data-ttu-id="0357e-348">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="0357e-348">**-m** _error_level_</span></span>  
 <span data-ttu-id="0357e-349">控制哪些錯誤訊息會傳送至 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-349">Controls which error messages are sent to **stdout**.</span></span> <span data-ttu-id="0357e-350">系統會傳送嚴重性層級大於或等於這個層級的訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-350">Messages that have a severity level greater than or equal to this level are sent.</span></span> <span data-ttu-id="0357e-351">當這個值設定為 **-1**時，系統就會傳送包括資訊訊息的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-351">When this value is set to **-1**, all messages including informational messages, are sent.</span></span> <span data-ttu-id="0357e-352">**-m** 與 **-1**之間不允許有空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-352">Spaces are not allowed between the **-m** and **-1**.</span></span> <span data-ttu-id="0357e-353">例如， **-m-1** 為有效，而 **-m -1** 為無效。</span><span class="sxs-lookup"><span data-stu-id="0357e-353">For example, **-m-1** is valid, and **-m-1** is not.</span></span>  
  
 <span data-ttu-id="0357e-354">這個選項也會設定 `sqlcmd` 指令碼變數 SQLCMDERRORLEVEL。</span><span class="sxs-lookup"><span data-stu-id="0357e-354">This option also sets the `sqlcmd` scripting variable SQLCMDERRORLEVEL.</span></span> <span data-ttu-id="0357e-355">這個變數具有預設值 0。</span><span class="sxs-lookup"><span data-stu-id="0357e-355">This variable has a default of 0.</span></span>  
  
 <span data-ttu-id="0357e-356">`-V`*error_severity_level*</span><span class="sxs-lookup"><span data-stu-id="0357e-356">`-V` *error_severity_level*</span></span>  
 <span data-ttu-id="0357e-357">控制用來設定 ERRORLEVEL 變數的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="0357e-357">Controls the severity level that is used to set the ERRORLEVEL variable.</span></span> <span data-ttu-id="0357e-358">嚴重性層級大於或等於這個值的錯誤訊息會設定 ERRORLEVEL。</span><span class="sxs-lookup"><span data-stu-id="0357e-358">Error messages that have severity levels greater than or equal to this value set ERRORLEVEL.</span></span> <span data-ttu-id="0357e-359">小於 0 的值會回報成 0。</span><span class="sxs-lookup"><span data-stu-id="0357e-359">Values that are less than 0 are reported as 0.</span></span> <span data-ttu-id="0357e-360">批次和 CMD 檔案可用來測試 ERRORLEVEL 變數的值。</span><span class="sxs-lookup"><span data-stu-id="0357e-360">Batch and CMD files can be used to test the value of the ERRORLEVEL variable.</span></span>  
  
 <span data-ttu-id="0357e-361">**其他選項**</span><span class="sxs-lookup"><span data-stu-id="0357e-361">**Miscellaneous Options**</span></span>  
  <span data-ttu-id="0357e-362">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="0357e-362">**-a** _packet_size_</span></span>  
 <span data-ttu-id="0357e-363">要求不同大小的封包。</span><span class="sxs-lookup"><span data-stu-id="0357e-363">Requests a packet of a different size.</span></span> <span data-ttu-id="0357e-364">這個選項會設定 `sqlcmd` 指令碼變數 SQLCMDPACKETSIZE。</span><span class="sxs-lookup"><span data-stu-id="0357e-364">This option sets the `sqlcmd` scripting variable SQLCMDPACKETSIZE.</span></span> <span data-ttu-id="0357e-365">*packet_size* 必須是介於 512 與 32767 之間的值。</span><span class="sxs-lookup"><span data-stu-id="0357e-365">*packet_size* must be a value between 512 and 32767.</span></span> <span data-ttu-id="0357e-366">預設 = 4096。</span><span class="sxs-lookup"><span data-stu-id="0357e-366">The default = 4096.</span></span> <span data-ttu-id="0357e-367">較大的封包大小可以讓 GO 命令之間具有許多 SQL 陳述式的指令碼執行得以提高效能。</span><span class="sxs-lookup"><span data-stu-id="0357e-367">A larger packet size can enhance performance for execution of scripts that have lots of SQL statements between GO commands.</span></span> <span data-ttu-id="0357e-368">您可以要求較大的封包。</span><span class="sxs-lookup"><span data-stu-id="0357e-368">You can request a larger packet size.</span></span> <span data-ttu-id="0357e-369">但是，若要求遭到拒絕，`sqlcmd` 便會使用伺服器預設的封包大小。</span><span class="sxs-lookup"><span data-stu-id="0357e-369">However, if the request is denied, `sqlcmd` uses the server default for packet size.</span></span>  
  
 <span data-ttu-id="0357e-370">**-c** _batch_terminator_</span><span class="sxs-lookup"><span data-stu-id="0357e-370">**-c** _batch_terminator_</span></span>  
 <span data-ttu-id="0357e-371">指定批次結束字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-371">Specifies the batch terminator.</span></span> <span data-ttu-id="0357e-372">依預設，在一行中單獨輸入 "GO" 這個字，便會終止命令，並將命令傳給 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0357e-372">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by typing the word "GO" on a line by itself.</span></span> <span data-ttu-id="0357e-373">當您重設批次結束字元時，請勿使用對作業系統有特殊意義的 [!INCLUDE[tsql](../includes/tsql-md.md)] 保留關鍵字或字元，即使它們前面附加了反斜線也一樣。</span><span class="sxs-lookup"><span data-stu-id="0357e-373">When you reset the batch terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved keywords or characters that have special meaning to the operating system, even if they are preceded by a backslash.</span></span>  
  
 <span data-ttu-id="0357e-374">**-L**[**c**]</span><span class="sxs-lookup"><span data-stu-id="0357e-374">**-L**[**c**]</span></span>  
 <span data-ttu-id="0357e-375">列出設定在本機的伺服器電腦，以及在網路中進行廣播的伺服器電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-375">Lists the locally configured server computers, and the names of the server computers that are broadcasting on the network.</span></span> <span data-ttu-id="0357e-376">這個參數不能結合其他參數來使用。</span><span class="sxs-lookup"><span data-stu-id="0357e-376">This parameter cannot be used in combination with other parameters.</span></span> <span data-ttu-id="0357e-377">可以列出的最大伺服器電腦數目為 3000。</span><span class="sxs-lookup"><span data-stu-id="0357e-377">The maximum number of server computers that can be listed is 3000.</span></span> <span data-ttu-id="0357e-378">如果伺服器清單因為緩衝區的大小而遭到截斷，將會顯示一則警告訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-378">If the server list is truncated because of the size of the buffer a warning message is displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-379">由於網路廣播的本質之故，`sqlcmd` 可能不會收到所有伺服器及時的回應。</span><span class="sxs-lookup"><span data-stu-id="0357e-379">Because of the nature of broadcasting on networks, `sqlcmd` may not receive a timely response from all servers.</span></span> <span data-ttu-id="0357e-380">因此，這個選項每次的引動過程，所傳回的伺服器清單可能各不相同。</span><span class="sxs-lookup"><span data-stu-id="0357e-380">Therefore, the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="0357e-381">如果指定了選擇性的參數**c** ，輸出就會顯示，但不會有 Servers：標頭行，而且會列出每個伺服器行，而不會有開頭空白。</span><span class="sxs-lookup"><span data-stu-id="0357e-381">If the optional parameter **c** is specified, the output appears without the Servers: header line and each server line is listed without leading spaces.</span></span> <span data-ttu-id="0357e-382">這稱為清除輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-382">This is referred to as clean output.</span></span> <span data-ttu-id="0357e-383">清除輸出可以增進指令碼語言的處理效能。</span><span class="sxs-lookup"><span data-stu-id="0357e-383">Clean output improves the processing performance of scripting languages.</span></span>  
  
 <span data-ttu-id="0357e-384">**-p**[**1**]</span><span class="sxs-lookup"><span data-stu-id="0357e-384">**-p**[**1**]</span></span>  
 <span data-ttu-id="0357e-385">列印每個結果集的效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="0357e-385">Prints performance statistics for every result set.</span></span> <span data-ttu-id="0357e-386">以下是效能統計資料的格式範例：</span><span class="sxs-lookup"><span data-stu-id="0357e-386">The following is an example of the format for performance statistics:</span></span>  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 <span data-ttu-id="0357e-387">其中：</span><span class="sxs-lookup"><span data-stu-id="0357e-387">Where:</span></span>  
  
 <span data-ttu-id="0357e-388">`x` = [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 所處理的交易數目。</span><span class="sxs-lookup"><span data-stu-id="0357e-388">`x` = Number of transactions that are processed by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0357e-389">`t1` = 所有交易的總時間。</span><span class="sxs-lookup"><span data-stu-id="0357e-389">`t1` = Total time for all transactions.</span></span>  
  
 <span data-ttu-id="0357e-390">`t2` = 單一交易的平均時間。</span><span class="sxs-lookup"><span data-stu-id="0357e-390">`t2` = Average time for a single transaction.</span></span>  
  
 <span data-ttu-id="0357e-391">`t3` = 每秒的平均交易數。</span><span class="sxs-lookup"><span data-stu-id="0357e-391">`t3` = Average number of transactions per second.</span></span>  
  
 <span data-ttu-id="0357e-392">所有時間都以毫秒表示。</span><span class="sxs-lookup"><span data-stu-id="0357e-392">All times are in milliseconds.</span></span>  
  
 <span data-ttu-id="0357e-393">如果指定了選擇性參數 **1** ，統計資料的輸出格式是用冒號分隔的格式，很容易匯入試算表中，指令碼也很容易處理它。</span><span class="sxs-lookup"><span data-stu-id="0357e-393">If the optional parameter **1** is specified, the output format of the statistics is in colon-separated format that can be imported easily into a spreadsheet or processed by a script.</span></span>  
  
 <span data-ttu-id="0357e-394">如果選擇性參數是**1**以外的任何值，則會產生錯誤並結束 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="0357e-394">If the optional parameter is any value other than **1**, an error is generated and `sqlcmd` exits.</span></span>  
  
 <span data-ttu-id="0357e-395">`-X`[**1**]</span><span class="sxs-lookup"><span data-stu-id="0357e-395">`-X`[**1**]</span></span>  
 <span data-ttu-id="0357e-396">停用從批次檔執行 `sqlcmd` 時，可能會危及系統安全性的命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-396">Disables commands that might compromise system security when `sqlcmd` is executed from a batch file.</span></span> <span data-ttu-id="0357e-397">仍會辨識停用的命令；`sqlcmd` 會發出一則警告訊息，並繼續作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-397">The disabled commands are still recognized; `sqlcmd` issues a warning message and continues.</span></span> <span data-ttu-id="0357e-398">如果指定了選擇性參數**1** ，會 `sqlcmd` 產生錯誤訊息，然後結束。</span><span class="sxs-lookup"><span data-stu-id="0357e-398">If the optional parameter **1** is specified, `sqlcmd` generates an error message and then exits.</span></span> <span data-ttu-id="0357e-399">使用 `-X` 選項時，會停用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0357e-399">The following commands are disabled when the `-X` option is used:</span></span>  
  
-   <span data-ttu-id="0357e-400">**ED**</span><span class="sxs-lookup"><span data-stu-id="0357e-400">**ED**</span></span>  
  
-   <span data-ttu-id="0357e-401">**!!**</span><span class="sxs-lookup"><span data-stu-id="0357e-401">**!!**</span></span> <span data-ttu-id="0357e-402">_command_</span><span class="sxs-lookup"><span data-stu-id="0357e-402">_command_</span></span>  
  
 <span data-ttu-id="0357e-403">如果指定了 `-X` 選項，您就無法將環境變數傳給 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-403">If the `-X` option is specified, it prevents environment variables from being passed on to `sqlcmd`.</span></span> <span data-ttu-id="0357e-404">也無法執行利用 SQLCMDINI 指令碼變數所指定的啟動指令碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-404">It also prevents the startup script specified by using the SQLCMDINI scripting variable from being executed.</span></span> <span data-ttu-id="0357e-405">如需腳本變數的詳細資訊 `sqlcmd` ，請參閱搭配[腳本變數使用 sqlcmd](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="0357e-405">For more information about `sqlcmd` scripting variables, see [Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).</span></span>  
  
 <span data-ttu-id="0357e-406">**-?**</span><span class="sxs-lookup"><span data-stu-id="0357e-406">**-?**</span></span>  
 <span data-ttu-id="0357e-407">顯示 `sqlcmd` 選項的語法摘要。</span><span class="sxs-lookup"><span data-stu-id="0357e-407">Displays the syntax summary of `sqlcmd` options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0357e-408">備註</span><span class="sxs-lookup"><span data-stu-id="0357e-408">Remarks</span></span>  
 <span data-ttu-id="0357e-409">您不需要按照語法區段中顯示的順序使用選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-409">Options do not have to be used in the order shown in the syntax section.</span></span>  
  
 <span data-ttu-id="0357e-410">傳回多項結果時，`sqlcmd` 會在批次的各結果集之間，列印一行空白行。</span><span class="sxs-lookup"><span data-stu-id="0357e-410">When multiple results are returned, `sqlcmd` prints a blank line between each result set in a batch.</span></span> <span data-ttu-id="0357e-411">此外， \<x> 當「受影響的資料列」訊息不適用於執行的語句時，就不會出現。</span><span class="sxs-lookup"><span data-stu-id="0357e-411">In addition, the "\<x> rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
 <span data-ttu-id="0357e-412">若要以 `sqlcmd` 互動方式使用，請 `sqlcmd` 在命令提示字元中，使用本主題稍早所述的一或多個選項來輸入。</span><span class="sxs-lookup"><span data-stu-id="0357e-412">To use `sqlcmd` interactively, type `sqlcmd` at the command prompt with any one or more of the options described earlier in this topic.</span></span> <span data-ttu-id="0357e-413">如需詳細資訊，請參閱 [使用 sqlcmd 公用程式](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span><span class="sxs-lookup"><span data-stu-id="0357e-413">For more information, see [Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-414">選項 **-L**、 **-Q**、 **-Z**或 **-i**會導致 `sqlcmd` 在執行之後結束。</span><span class="sxs-lookup"><span data-stu-id="0357e-414">The options **-L**, **-Q**, **-Z** or **-i** cause `sqlcmd` to exit after execution.</span></span>  
  
 <span data-ttu-id="0357e-415">命令列環境 (Cmd.exe) 中之 `sqlcmd` 命令列的總長度 (包括所有引數和擴充的變數)，皆由 Cmd.exe 的作業系統決定。</span><span class="sxs-lookup"><span data-stu-id="0357e-415">The total length of the `sqlcmd` command line in the command environment (Cmd.exe), including all arguments and expanded variables, is that which is determined by the operating system for Cmd.exe.</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="0357e-416">變數優先順序 (由低至高)</span><span class="sxs-lookup"><span data-stu-id="0357e-416">Variable Precedence (Low to High)</span></span>  
  
1.  <span data-ttu-id="0357e-417">系統層級環境變數</span><span class="sxs-lookup"><span data-stu-id="0357e-417">System-level environmental variables.</span></span>  
  
2.  <span data-ttu-id="0357e-418">使用者層級環境變數</span><span class="sxs-lookup"><span data-stu-id="0357e-418">User-level environmental variables</span></span>  
  
3.  <span data-ttu-id="0357e-419">在執行之前，命令 shell (**set** X = Y) 設定于命令提示字元 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="0357e-419">Command shell (**SET** X=Y) set at command prompt before running `sqlcmd`.</span></span>  
  
4.  <span data-ttu-id="0357e-420">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="0357e-420">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="0357e-421">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="0357e-421">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-422">若要檢視環境變數，請在 [控制台] 中開啟 [系統] ，然後按一下 [進階]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0357e-422">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="0357e-423">sqlcmd 指令碼變數</span><span class="sxs-lookup"><span data-stu-id="0357e-423">sqlcmd Scripting Variables</span></span>  
  
|<span data-ttu-id="0357e-424">變數</span><span class="sxs-lookup"><span data-stu-id="0357e-424">Variable</span></span>|<span data-ttu-id="0357e-425">相關參數</span><span class="sxs-lookup"><span data-stu-id="0357e-425">Related switch</span></span>|<span data-ttu-id="0357e-426">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-426">R/W</span></span>|<span data-ttu-id="0357e-427">預設</span><span class="sxs-lookup"><span data-stu-id="0357e-427">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="0357e-428">SQLCMDUSER</span><span class="sxs-lookup"><span data-stu-id="0357e-428">SQLCMDUSER</span></span>|<span data-ttu-id="0357e-429">-U</span><span class="sxs-lookup"><span data-stu-id="0357e-429">-U</span></span>|<span data-ttu-id="0357e-430">R</span><span class="sxs-lookup"><span data-stu-id="0357e-430">R</span></span>|<span data-ttu-id="0357e-431">""</span><span class="sxs-lookup"><span data-stu-id="0357e-431">""</span></span>|  
|<span data-ttu-id="0357e-432">SQLCMDPASSWORD</span><span class="sxs-lookup"><span data-stu-id="0357e-432">SQLCMDPASSWORD</span></span>|<span data-ttu-id="0357e-433">-P</span><span class="sxs-lookup"><span data-stu-id="0357e-433">-P</span></span>|--|<span data-ttu-id="0357e-434">""</span><span class="sxs-lookup"><span data-stu-id="0357e-434">""</span></span>|  
|<span data-ttu-id="0357e-435">SQLCMDSERVER</span><span class="sxs-lookup"><span data-stu-id="0357e-435">SQLCMDSERVER</span></span>|<span data-ttu-id="0357e-436">-S</span><span class="sxs-lookup"><span data-stu-id="0357e-436">-S</span></span>|<span data-ttu-id="0357e-437">R</span><span class="sxs-lookup"><span data-stu-id="0357e-437">R</span></span>|<span data-ttu-id="0357e-438">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="0357e-438">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="0357e-439">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="0357e-439">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="0357e-440">-H</span><span class="sxs-lookup"><span data-stu-id="0357e-440">-H</span></span>|<span data-ttu-id="0357e-441">R</span><span class="sxs-lookup"><span data-stu-id="0357e-441">R</span></span>|<span data-ttu-id="0357e-442">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="0357e-442">"ComputerName"</span></span>|  
|<span data-ttu-id="0357e-443">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="0357e-443">SQLCMDDBNAME</span></span>|<span data-ttu-id="0357e-444">-d</span><span class="sxs-lookup"><span data-stu-id="0357e-444">-d</span></span>|<span data-ttu-id="0357e-445">R</span><span class="sxs-lookup"><span data-stu-id="0357e-445">R</span></span>|<span data-ttu-id="0357e-446">""</span><span class="sxs-lookup"><span data-stu-id="0357e-446">""</span></span>|  
|<span data-ttu-id="0357e-447">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0357e-447">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="0357e-448">-l</span><span class="sxs-lookup"><span data-stu-id="0357e-448">-l</span></span>|<span data-ttu-id="0357e-449">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-449">R/W</span></span>|<span data-ttu-id="0357e-450">"8" (秒)</span><span class="sxs-lookup"><span data-stu-id="0357e-450">"8" (seconds)</span></span>|  
|<span data-ttu-id="0357e-451">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0357e-451">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="0357e-452">-t</span><span class="sxs-lookup"><span data-stu-id="0357e-452">-t</span></span>|<span data-ttu-id="0357e-453">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-453">R/W</span></span>|<span data-ttu-id="0357e-454">"0" = 永遠等候</span><span class="sxs-lookup"><span data-stu-id="0357e-454">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="0357e-455">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="0357e-455">SQLCMDHEADERS</span></span>|<span data-ttu-id="0357e-456">-H</span><span class="sxs-lookup"><span data-stu-id="0357e-456">-h</span></span>|<span data-ttu-id="0357e-457">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-457">R/W</span></span>|<span data-ttu-id="0357e-458">"0"</span><span class="sxs-lookup"><span data-stu-id="0357e-458">"0"</span></span>|  
|<span data-ttu-id="0357e-459">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="0357e-459">SQLCMDCOLSEP</span></span>|<span data-ttu-id="0357e-460">-S</span><span class="sxs-lookup"><span data-stu-id="0357e-460">-s</span></span>|<span data-ttu-id="0357e-461">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-461">R/W</span></span>|<span data-ttu-id="0357e-462">" "</span><span class="sxs-lookup"><span data-stu-id="0357e-462">" "</span></span>|  
|<span data-ttu-id="0357e-463">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="0357e-463">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="0357e-464">-w</span><span class="sxs-lookup"><span data-stu-id="0357e-464">-w</span></span>|<span data-ttu-id="0357e-465">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-465">R/W</span></span>|<span data-ttu-id="0357e-466">"0"</span><span class="sxs-lookup"><span data-stu-id="0357e-466">"0"</span></span>|  
|<span data-ttu-id="0357e-467">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="0357e-467">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="0357e-468">-a</span><span class="sxs-lookup"><span data-stu-id="0357e-468">-a</span></span>|<span data-ttu-id="0357e-469">R</span><span class="sxs-lookup"><span data-stu-id="0357e-469">R</span></span>|<span data-ttu-id="0357e-470">"4096"</span><span class="sxs-lookup"><span data-stu-id="0357e-470">"4096"</span></span>|  
|<span data-ttu-id="0357e-471">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="0357e-471">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="0357e-472">-M</span><span class="sxs-lookup"><span data-stu-id="0357e-472">-m</span></span>|<span data-ttu-id="0357e-473">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-473">R/W</span></span>|<span data-ttu-id="0357e-474">0</span><span class="sxs-lookup"><span data-stu-id="0357e-474">0</span></span>|  
|<span data-ttu-id="0357e-475">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="0357e-475">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="0357e-476">-y</span><span class="sxs-lookup"><span data-stu-id="0357e-476">-y</span></span>|<span data-ttu-id="0357e-477">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-477">R/W</span></span>|<span data-ttu-id="0357e-478">"256"</span><span class="sxs-lookup"><span data-stu-id="0357e-478">"256"</span></span>|  
|<span data-ttu-id="0357e-479">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="0357e-479">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="0357e-480">-y</span><span class="sxs-lookup"><span data-stu-id="0357e-480">-Y</span></span>|<span data-ttu-id="0357e-481">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-481">R/W</span></span>|<span data-ttu-id="0357e-482">"0" = 無限制</span><span class="sxs-lookup"><span data-stu-id="0357e-482">"0" = unlimited</span></span>|  
|<span data-ttu-id="0357e-483">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="0357e-483">SQLCMDEDITOR</span></span>||<span data-ttu-id="0357e-484">R/W</span><span class="sxs-lookup"><span data-stu-id="0357e-484">R/W</span></span>|<span data-ttu-id="0357e-485">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="0357e-485">"edit.com"</span></span>|  
|<span data-ttu-id="0357e-486">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="0357e-486">SQLCMDINI</span></span>||<span data-ttu-id="0357e-487">R</span><span class="sxs-lookup"><span data-stu-id="0357e-487">R</span></span>|<span data-ttu-id="0357e-488">""</span><span class="sxs-lookup"><span data-stu-id="0357e-488">""</span></span>|  
  
 <span data-ttu-id="0357e-489">SQLCMDUSER、SQLCMDPASSWORD 和 SQLCMDSERVER 會在使用 **:Connect**</span><span class="sxs-lookup"><span data-stu-id="0357e-489">SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect**</span></span>  
  
 <span data-ttu-id="0357e-490">時設定。</span><span class="sxs-lookup"><span data-stu-id="0357e-490">is used.</span></span>  
  
 <span data-ttu-id="0357e-491">R 表示在程式初始化期間只能設定該值一次。</span><span class="sxs-lookup"><span data-stu-id="0357e-491">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="0357e-492">R/W 表示可以使用 **setvar** 命令修改該值，且後續的命令會受到新值的影響。</span><span class="sxs-lookup"><span data-stu-id="0357e-492">R/W indicates that the value can be modified by using the **setvar** command and subsequent commands will be influenced by the new value.</span></span>  
  
## <a name="sqlcmd-commands"></a><span data-ttu-id="0357e-493">sqlcmd 命令</span><span class="sxs-lookup"><span data-stu-id="0357e-493">sqlcmd Commands</span></span>  
 <span data-ttu-id="0357e-494">除了 `sqlcmd` 內的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式之外，您也可以使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0357e-494">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within `sqlcmd`, the following commands are also available:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0357e-495">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="0357e-495">**GO** [*count*]</span></span>|<span data-ttu-id="0357e-496">**:List**</span><span class="sxs-lookup"><span data-stu-id="0357e-496">**:List**</span></span>|  
|<span data-ttu-id="0357e-497">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="0357e-497">[**:**] **RESET**</span></span>|<span data-ttu-id="0357e-498">**:Error**</span><span class="sxs-lookup"><span data-stu-id="0357e-498">**:Error**</span></span>|  
|<span data-ttu-id="0357e-499">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="0357e-499">[**:**] **ED**</span></span>|<span data-ttu-id="0357e-500">**:Out**</span><span class="sxs-lookup"><span data-stu-id="0357e-500">**:Out**</span></span>|  
|<span data-ttu-id="0357e-501">[**:**] **!!**</span><span class="sxs-lookup"><span data-stu-id="0357e-501">[**:**] **!!**</span></span>|<span data-ttu-id="0357e-502">**:Perftrace**</span><span class="sxs-lookup"><span data-stu-id="0357e-502">**:Perftrace**</span></span>|  
|<span data-ttu-id="0357e-503">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="0357e-503">[**:**] **QUIT**</span></span>|<span data-ttu-id="0357e-504">**:Connect**</span><span class="sxs-lookup"><span data-stu-id="0357e-504">**:Connect**</span></span>|  
|<span data-ttu-id="0357e-505">[ **:** ] **EXIT**</span><span class="sxs-lookup"><span data-stu-id="0357e-505">[**:**] **EXIT**</span></span>|<span data-ttu-id="0357e-506">**:On Error**</span><span class="sxs-lookup"><span data-stu-id="0357e-506">**:On Error**</span></span>|  
|<span data-ttu-id="0357e-507">**:r**</span><span class="sxs-lookup"><span data-stu-id="0357e-507">**:r**</span></span>|<span data-ttu-id="0357e-508">**:Help**</span><span class="sxs-lookup"><span data-stu-id="0357e-508">**:Help**</span></span>|  
|<span data-ttu-id="0357e-509">**:ServerList**</span><span class="sxs-lookup"><span data-stu-id="0357e-509">**:ServerList**</span></span>|<span data-ttu-id="0357e-510">**:XML** [**ON** &#124; **OFF**]</span><span class="sxs-lookup"><span data-stu-id="0357e-510">**:XML** [**ON** &#124; **OFF**]</span></span>|  
|<span data-ttu-id="0357e-511">**:Setvar**</span><span class="sxs-lookup"><span data-stu-id="0357e-511">**:Setvar**</span></span>|<span data-ttu-id="0357e-512">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="0357e-512">**:Listvar**</span></span>|  
  
 <span data-ttu-id="0357e-513">使用 `sqlcmd` 命令時請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="0357e-513">Be aware of the following when you use `sqlcmd` commands:</span></span>  
  
-   <span data-ttu-id="0357e-514">除了 GO 之外的所有 `sqlcmd` 命令開頭都必須加上冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="0357e-514">All `sqlcmd` commands, except GO, must be prefixed by a colon (:).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="0357e-515">為了顧及與現有 **osql** 指令碼的回溯相容性，也會辨識部分沒有冒號的命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-515">To maintain backward compatibility with existing **osql** scripts, some of the commands will be recognized without the colon.</span></span> <span data-ttu-id="0357e-516">[**:**] 表示這一點。</span><span class="sxs-lookup"><span data-stu-id="0357e-516">This is indicated by the [**:**].</span></span>  
  
-   <span data-ttu-id="0357e-517">`sqlcmd` 命令必須在行首，才能夠辨識。</span><span class="sxs-lookup"><span data-stu-id="0357e-517">`sqlcmd` commands are recognized only if they appear at the start of a line.</span></span>  
  
-   <span data-ttu-id="0357e-518">所有 `sqlcmd` 命令都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0357e-518">All `sqlcmd` commands are case insensitive.</span></span>  
  
-   <span data-ttu-id="0357e-519">每個命令都必須在不同行中。</span><span class="sxs-lookup"><span data-stu-id="0357e-519">Each command must be on a separate line.</span></span> <span data-ttu-id="0357e-520">命令後面不能有 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式或另一個命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-520">A command cannot be followed by a [!INCLUDE[tsql](../includes/tsql-md.md)] statement or another command.</span></span>  
  
-   <span data-ttu-id="0357e-521">命令會立即執行，</span><span class="sxs-lookup"><span data-stu-id="0357e-521">Commands are executed immediately.</span></span> <span data-ttu-id="0357e-522">不會像 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式一樣放在執行緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="0357e-522">They are not put in the execution buffer as [!INCLUDE[tsql](../includes/tsql-md.md)] statements are.</span></span>  
  
 <span data-ttu-id="0357e-523">**編輯命令**</span><span class="sxs-lookup"><span data-stu-id="0357e-523">**Editing Commands**</span></span>  
  <span data-ttu-id="0357e-524">[ **:** ] **ED**</span><span class="sxs-lookup"><span data-stu-id="0357e-524">[**:**] **ED**</span></span>  
 <span data-ttu-id="0357e-525">啟動文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="0357e-525">Starts the text editor.</span></span> <span data-ttu-id="0357e-526">您可以利用這個編輯器編輯目前的 [!INCLUDE[tsql](../includes/tsql-md.md)] 批次，或上次執行的批次。</span><span class="sxs-lookup"><span data-stu-id="0357e-526">This editor can be used to edit the current [!INCLUDE[tsql](../includes/tsql-md.md)] batch, or the last executed batch.</span></span> <span data-ttu-id="0357e-527">若要編輯上次執行的批次，在上一個批次執行完成之後，必須立即輸入 **ED** 命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-527">To edit the last executed batch, the **ED** command must be typed immediately after the last batch has completed execution.</span></span>  
  
 <span data-ttu-id="0357e-528">文字編輯器由 SQLCMDEDITOR 環境變數來定義。</span><span class="sxs-lookup"><span data-stu-id="0357e-528">The text editor is defined by the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="0357e-529">預設編輯器是 'Edit'。</span><span class="sxs-lookup"><span data-stu-id="0357e-529">The default editor is 'Edit'.</span></span> <span data-ttu-id="0357e-530">若要變更編輯器，請設定 SQLCMDEDITOR 環境變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-530">To change the editor, set the SQLCMDEDITOR environment variable.</span></span> <span data-ttu-id="0357e-531">例如，若要將編輯器設為 [!INCLUDE[msCoName](../includes/msconame-md.md)] Notepad，請在命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-531">For example, to set the editor to [!INCLUDE[msCoName](../includes/msconame-md.md)] Notepad, at the command prompt, type:</span></span>  
  
 `SET SQLCMDEDITOR=notepad`  
  
 <span data-ttu-id="0357e-532">[ **:** ] **RESET**</span><span class="sxs-lookup"><span data-stu-id="0357e-532">[**:**] **RESET**</span></span>  
 <span data-ttu-id="0357e-533">清除陳述式快取。</span><span class="sxs-lookup"><span data-stu-id="0357e-533">Clears the statement cache.</span></span>  
  
 <span data-ttu-id="0357e-534">**:List**</span><span class="sxs-lookup"><span data-stu-id="0357e-534">**:List**</span></span>  
 <span data-ttu-id="0357e-535">列印陳述式快取內容。</span><span class="sxs-lookup"><span data-stu-id="0357e-535">Prints the content of the statement cache.</span></span>  
  
 <span data-ttu-id="0357e-536">**變數**</span><span class="sxs-lookup"><span data-stu-id="0357e-536">**Variables**</span></span>  
  <span data-ttu-id="0357e-537">**： Setvar** \<**var**>[ **"*`value`*"** ]</span><span class="sxs-lookup"><span data-stu-id="0357e-537">**:Setvar** \<**var**> [ **"*`value`*"** ]</span></span>  
 <span data-ttu-id="0357e-538">定義 `sqlcmd` 指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-538">Defines `sqlcmd` scripting variables.</span></span> <span data-ttu-id="0357e-539">指令碼變數的格式如下： `$(VARNAME)`。</span><span class="sxs-lookup"><span data-stu-id="0357e-539">Scripting variables have the following format: `$(VARNAME)`.</span></span>  
  
 <span data-ttu-id="0357e-540">變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0357e-540">Variable names are case insensitive.</span></span>  
  
 <span data-ttu-id="0357e-541">指令碼變數可以透過下列幾種方式設定：</span><span class="sxs-lookup"><span data-stu-id="0357e-541">Scripting variables can be set in the following ways:</span></span>  
  
-   <span data-ttu-id="0357e-542">隱含地使用命令列選項。</span><span class="sxs-lookup"><span data-stu-id="0357e-542">Implicitly using a command-line option.</span></span> <span data-ttu-id="0357e-543">例如， **-l**選項會設定 SQLCMDLOGINTIMEOUT `sqlcmd` 變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-543">For example, the **-l** option sets the SQLCMDLOGINTIMEOUT `sqlcmd` variable.</span></span>  
  
-   <span data-ttu-id="0357e-544">明確地利用 **:Setvar** 命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-544">Explicitly by using the **:Setvar** command.</span></span>  
  
-   <span data-ttu-id="0357e-545">在您執行 `sqlcmd` 之前，定義環境變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-545">By defining an environment variable before you run `sqlcmd`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-546">`-X` 選項會讓您無法將環境變數傳給 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-546">The `-X` option prevents environment variables from being passed on to `sqlcmd`.</span></span>  
  
 <span data-ttu-id="0357e-547">如果使用 **:Setvar** 所定義的變數和環境變數同名，則以使用 **:Setvar** 所定義的變數優先。</span><span class="sxs-lookup"><span data-stu-id="0357e-547">If a variable defined by using **:Setvar** and an environment variable have the same name, the variable defined by using **:Setvar** takes precedence.</span></span>  
  
 <span data-ttu-id="0357e-548">變數名稱不能包含空格字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-548">Variable names must not contain blank space characters.</span></span>  
  
 <span data-ttu-id="0357e-549">變數名稱的格式不能與變數運算式 (例如 $(var)) 相同。</span><span class="sxs-lookup"><span data-stu-id="0357e-549">Variable names cannot have the same form as a variable expression, such as $(var).</span></span>  
  
 <span data-ttu-id="0357e-550">如果指令碼變數的字串值包含空格，請用引號括住這個值。</span><span class="sxs-lookup"><span data-stu-id="0357e-550">If the string value of the scripting variable contains blank spaces, enclose the value in quotation marks.</span></span> <span data-ttu-id="0357e-551">如果未指定指令碼變數值，就會卸除指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="0357e-551">If a value for a scripting variable is not specified, the scripting variable is dropped.</span></span>  
  
 <span data-ttu-id="0357e-552">**:Listvar**</span><span class="sxs-lookup"><span data-stu-id="0357e-552">**:Listvar**</span></span>  
 <span data-ttu-id="0357e-553">顯示目前所設定之指令碼變數的清單。</span><span class="sxs-lookup"><span data-stu-id="0357e-553">Displays a list of the scripting variables that are currently set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-554">只會顯示由設定的腳本變數 `sqlcmd` ，以及使用 **： Setvar**命令所設定的腳本。</span><span class="sxs-lookup"><span data-stu-id="0357e-554">Only scripting variables that are set by `sqlcmd`, and those that are set using the **:Setvar** command will be displayed.</span></span>  
  
 <span data-ttu-id="0357e-555">**輸出命令**</span><span class="sxs-lookup"><span data-stu-id="0357e-555">**Output Commands**</span></span>  
  <span data-ttu-id="0357e-556">**:Error** </span><span class="sxs-lookup"><span data-stu-id="0357e-556">**:Error** </span></span>  
 <span data-ttu-id="0357e-557">**_\<_** _filename_  **_>|_ STDERR |輸出**</span><span class="sxs-lookup"><span data-stu-id="0357e-557">**_\<_** _filename_  **_>|_ STDERR|STDOUT**</span></span>  
 <span data-ttu-id="0357e-558">將所有錯誤輸出重新導向至 *filename*所指定的檔案、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-558">Redirect all error output to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="0357e-559">在指令碼中， **Error** 命令可以重複出現。</span><span class="sxs-lookup"><span data-stu-id="0357e-559">The **Error** command can appear multiple times in a script.</span></span> <span data-ttu-id="0357e-560">根據預設，錯誤輸出會傳送到 **stderr**。</span><span class="sxs-lookup"><span data-stu-id="0357e-560">By default, error output is sent to **stderr**.</span></span>  
  
 <span data-ttu-id="0357e-561">*file name*</span><span class="sxs-lookup"><span data-stu-id="0357e-561">*file name*</span></span>  
 <span data-ttu-id="0357e-562">建立和開啟用來接收輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-562">Creates and opens a file that will receive the output.</span></span> <span data-ttu-id="0357e-563">如果檔案已經存在，它會截斷成零位元組。</span><span class="sxs-lookup"><span data-stu-id="0357e-563">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="0357e-564">如果因為權限或其他原因無法使用，就不會切換輸出，輸出會送往最後指定的目的地或預設目的地。</span><span class="sxs-lookup"><span data-stu-id="0357e-564">If the file is not available because of permissions or other reasons, the output will not be switched and will be sent to the last specified or default destination.</span></span>  
  
 <span data-ttu-id="0357e-565">**STDERR**</span><span class="sxs-lookup"><span data-stu-id="0357e-565">**STDERR**</span></span>  
 <span data-ttu-id="0357e-566">將錯誤輸出切換到 **stderr** 資料流。</span><span class="sxs-lookup"><span data-stu-id="0357e-566">Switches error output to the **stderr** stream.</span></span> <span data-ttu-id="0357e-567">如果它已重新導向，資料流所重新導向的目標會接收這個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-567">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="0357e-568">**STDOUT**</span><span class="sxs-lookup"><span data-stu-id="0357e-568">**STDOUT**</span></span>  
 <span data-ttu-id="0357e-569">將錯誤輸出切換到 **stdout** 資料流。</span><span class="sxs-lookup"><span data-stu-id="0357e-569">Switches error output to the **stdout** stream.</span></span> <span data-ttu-id="0357e-570">如果它已重新導向，資料流所重新導向的目標會接收這個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-570">If this has been redirected, the target to which the stream has been redirected will receive the error output.</span></span>  
  
 <span data-ttu-id="0357e-571">\*\*： Out \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="0357e-571">**:Out \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="0357e-572">建立並將所有查詢結果重新導向至 *filename*所指定的檔案、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-572">Creates and redirects all query results to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="0357e-573">根據預設，輸出會傳送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-573">By default, output is sent to **stdout**.</span></span> <span data-ttu-id="0357e-574">如果檔案已經存在，它會截斷成零位元組。</span><span class="sxs-lookup"><span data-stu-id="0357e-574">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="0357e-575">在指令碼中， **Out** 命令可以重複出現。</span><span class="sxs-lookup"><span data-stu-id="0357e-575">The **Out** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="0357e-576">\*\*:P erftrace \<** _filename_ **> \*\* | **STDERR** | **STDOUT**</span><span class="sxs-lookup"><span data-stu-id="0357e-576">**:Perftrace \<** _filename_ **>**| **STDERR**| **STDOUT**</span></span>  
 <span data-ttu-id="0357e-577">建立並將所有效能追蹤資訊重新導向至 *filename*所指定的檔案、 **stderr** 或 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-577">Creates and redirects all performance trace information to the file specified by *file name*, to **stderr** or to **stdout**.</span></span> <span data-ttu-id="0357e-578">根據預設，效能追蹤輸出會傳送到 **stdout**。</span><span class="sxs-lookup"><span data-stu-id="0357e-578">By default performance trace output is sent to **stdout**.</span></span> <span data-ttu-id="0357e-579">如果檔案已經存在，它會截斷成零位元組。</span><span class="sxs-lookup"><span data-stu-id="0357e-579">If the file already exists, it will be truncated to zero bytes.</span></span> <span data-ttu-id="0357e-580">在指令碼中， **Perftrace** 命令可以重複出現。</span><span class="sxs-lookup"><span data-stu-id="0357e-580">The **Perftrace** command can appear multiple times in a script.</span></span>  
  
 <span data-ttu-id="0357e-581">**執行控制命令**</span><span class="sxs-lookup"><span data-stu-id="0357e-581">**Execution Control Commands**</span></span>  
  <span data-ttu-id="0357e-582">**：發生錯誤時**[ `exit`  |  `ignore` ]</span><span class="sxs-lookup"><span data-stu-id="0357e-582">**:On Error**[ `exit` | `ignore`]</span></span>  
 <span data-ttu-id="0357e-583">設定執行指令碼或批次發生錯誤時所要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="0357e-583">Sets the action to be performed when an error occurs during script or batch execution.</span></span>  
  
 <span data-ttu-id="0357e-584">使用 `exit` 選項時，`sqlcmd` 會結束作業，並會出現適當的錯誤值。</span><span class="sxs-lookup"><span data-stu-id="0357e-584">When the `exit` option is used, `sqlcmd` exits with the appropriate error value.</span></span>  
  
 <span data-ttu-id="0357e-585">使用 `ignore` 選項時，`sqlcmd` 會忽略錯誤，並繼續執行批次或指令碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-585">When the `ignore` option is used, `sqlcmd` ignores the error and continues executing the batch or script.</span></span> <span data-ttu-id="0357e-586">依預設，會列印一則錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-586">By default, an error message will be printed.</span></span>  
  
 <span data-ttu-id="0357e-587">[ **:** ] **QUIT**</span><span class="sxs-lookup"><span data-stu-id="0357e-587">[**:**] **QUIT**</span></span>  
 <span data-ttu-id="0357e-588">讓 `sqlcmd` 結束作業。</span><span class="sxs-lookup"><span data-stu-id="0357e-588">Causes `sqlcmd` to exit.</span></span>  
  
 <span data-ttu-id="0357e-589">[**:**]**EXIT**[ \*\* (*`statement`*) \*\* ]</span><span class="sxs-lookup"><span data-stu-id="0357e-589">[**:**] **EXIT**[ **(*`statement`*)** ]</span></span>  
 <span data-ttu-id="0357e-590">可讓您使用 SELECT 陳述式的結果做為 `sqlcmd` 的傳回值。</span><span class="sxs-lookup"><span data-stu-id="0357e-590">Lets you use the result of a SELECT statement as the return value from `sqlcmd`.</span></span> <span data-ttu-id="0357e-591">如果為數值，最後一個結果資料列的第一個資料行會轉換成 4 位元組的整數 (long)。</span><span class="sxs-lookup"><span data-stu-id="0357e-591">If numeric, the first column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="0357e-592">MS-DOS 會將低位元組傳給父處理序或作業系統錯誤層級。</span><span class="sxs-lookup"><span data-stu-id="0357e-592">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="0357e-593">Windows 200x 會傳遞完整的 4 位元組整數。</span><span class="sxs-lookup"><span data-stu-id="0357e-593">Windows 200x passes the whole 4-byte integer.</span></span> <span data-ttu-id="0357e-594">語法為：</span><span class="sxs-lookup"><span data-stu-id="0357e-594">The syntax is:</span></span>  
  
 `:EXIT(query)`  
  
 <span data-ttu-id="0357e-595">例如：</span><span class="sxs-lookup"><span data-stu-id="0357e-595">For example:</span></span>  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 <span data-ttu-id="0357e-596">您也可以將 **EXIT** 參數併入批次檔中。</span><span class="sxs-lookup"><span data-stu-id="0357e-596">You can also include the **EXIT** parameter as part of a batch file.</span></span> <span data-ttu-id="0357e-597">例如，在命令提示字元之下，輸入：</span><span class="sxs-lookup"><span data-stu-id="0357e-597">For example, at the command prompt, type:</span></span>  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 <span data-ttu-id="0357e-598">`sqlcmd`公用程式會將\*\* ( # B1\*\*的括弧之間的所有內容傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="0357e-598">The `sqlcmd` utility sends everything between the parentheses **()** to the server.</span></span> <span data-ttu-id="0357e-599">如果系統預存程序選取某一組，傳回某個值，此時只會傳回選取的項目。</span><span class="sxs-lookup"><span data-stu-id="0357e-599">If a system stored procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="0357e-600">括號中沒有任何內容的 EXIT **()** 陳述式，會執行批次中在它前面的任何內容，然後結束作業，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="0357e-600">The EXIT **()** statement with nothing between the parentheses executes everything before it in the batch and then exits without a return value.</span></span>  
  
 <span data-ttu-id="0357e-601">指定不正確的查詢時，`sqlcmd` 會結束作業，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="0357e-601">When an incorrect query is specified, `sqlcmd` will exit without a return value.</span></span>  
  
 <span data-ttu-id="0357e-602">以下是 EXIT 格式清單：</span><span class="sxs-lookup"><span data-stu-id="0357e-602">Here is a list of EXIT formats:</span></span>  
  
-   <span data-ttu-id="0357e-603">:EXIT</span><span class="sxs-lookup"><span data-stu-id="0357e-603">:EXIT</span></span>  
  
 <span data-ttu-id="0357e-604">不執行批次，然後立即結束，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="0357e-604">Does not execute the batch, and then quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="0357e-605">:EXIT( )</span><span class="sxs-lookup"><span data-stu-id="0357e-605">:EXIT( )</span></span>  
  
 <span data-ttu-id="0357e-606">執行批次之後，便結束作業，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="0357e-606">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="0357e-607">:EXIT(query)</span><span class="sxs-lookup"><span data-stu-id="0357e-607">:EXIT(query)</span></span>  
  
 <span data-ttu-id="0357e-608">執行包含查詢的批次，傳回查詢結果之後再結束。</span><span class="sxs-lookup"><span data-stu-id="0357e-608">Executes the batch that includes the query, and then quits after it returns the results of the query.</span></span>  
  
 <span data-ttu-id="0357e-609">如果在 `sqlcmd` 指令碼內使用 RAISERROR，且產生 127 狀態，`sqlcmd` 會結束作業，且會將訊息識別碼傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="0357e-609">If RAISERROR is used within a `sqlcmd` script and a state of 127 is raised, `sqlcmd` will quit and return the message ID back to the client.</span></span> <span data-ttu-id="0357e-610">例如：</span><span class="sxs-lookup"><span data-stu-id="0357e-610">For example:</span></span>  
  
 `RAISERROR(50001, 10, 127)`  
  
 <span data-ttu-id="0357e-611">這個錯誤會使得 `sqlcmd` 指令碼結束作業，並將訊息識別碼 50001 傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="0357e-611">This error will cause the `sqlcmd` script to end and return the message ID 50001 to the client.</span></span>  
  
 <span data-ttu-id="0357e-612">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會保留傳回值 -1 至 -99；`sqlcmd` 定義了下列其他傳回值：</span><span class="sxs-lookup"><span data-stu-id="0357e-612">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; `sqlcmd` defines the following additional return values:</span></span>  
  
|<span data-ttu-id="0357e-613">傳回值</span><span class="sxs-lookup"><span data-stu-id="0357e-613">Return Values</span></span>|<span data-ttu-id="0357e-614">描述</span><span class="sxs-lookup"><span data-stu-id="0357e-614">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="0357e-615">-100</span><span class="sxs-lookup"><span data-stu-id="0357e-615">-100</span></span>|<span data-ttu-id="0357e-616">在選取傳回值之前發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0357e-616">Error encountered prior to selecting return value.</span></span>|  
|<span data-ttu-id="0357e-617">-101</span><span class="sxs-lookup"><span data-stu-id="0357e-617">-101</span></span>|<span data-ttu-id="0357e-618">在選取傳回值時，找不到任何資料列。</span><span class="sxs-lookup"><span data-stu-id="0357e-618">No rows found when selecting return value.</span></span>|  
|<span data-ttu-id="0357e-619">-102</span><span class="sxs-lookup"><span data-stu-id="0357e-619">-102</span></span>|<span data-ttu-id="0357e-620">在選取傳回值時，發生轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="0357e-620">Conversion error occurred when selecting return value.</span></span>|  
  
 <span data-ttu-id="0357e-621">**GO** [*count*]</span><span class="sxs-lookup"><span data-stu-id="0357e-621">**GO** [*count*]</span></span>  
 <span data-ttu-id="0357e-622">GO 會發出批次結束及執行任何快取的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式的信號。</span><span class="sxs-lookup"><span data-stu-id="0357e-622">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="0357e-623">指定 *count*的值時，快取的陳述式將以單一批次執行 *count* 次。</span><span class="sxs-lookup"><span data-stu-id="0357e-623">When specifying a value for *count*, the cached statements will be executed *count* times, as a single batch.</span></span>  
  
 <span data-ttu-id="0357e-624">**其他命令**</span><span class="sxs-lookup"><span data-stu-id="0357e-624">**Miscellaneous Commands**</span></span>  
  <span data-ttu-id="0357e-625">**： r\<** _filename_ **>**</span><span class="sxs-lookup"><span data-stu-id="0357e-625">**:r \<** _filename_ **>**</span></span>  
 <span data-ttu-id="0357e-626">將 [!INCLUDE[tsql](../includes/tsql-md.md)] 指定之檔案中的其他語句和命令，剖析 `sqlcmd` **<*`filename`*>** 至語句快取。</span><span class="sxs-lookup"><span data-stu-id="0357e-626">Parses additional [!INCLUDE[tsql](../includes/tsql-md.md)] statements and `sqlcmd` commands from the file specified by **<*`filename`*>** into the statement cache.</span></span>  
  
 <span data-ttu-id="0357e-627">如果檔案包含的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式後面沒有緊接著 **GO**，您必須在 **:r** 之後的一行輸入 **GO**。</span><span class="sxs-lookup"><span data-stu-id="0357e-627">If the file contains [!INCLUDE[tsql](../includes/tsql-md.md)] statements that are not followed by **GO**, you must enter **GO** on the line that follows **:r**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-628">**\<** _filename_ **>** 會相對於執行所在的啟動目錄進行讀取 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="0357e-628">**\<** _filename_ **>** is read relative to the startup directory in which `sqlcmd` was run.</span></span>  
  
 <span data-ttu-id="0357e-629">在發現批次結束字元之後，便會讀取和執行這個檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-629">The file will be read and executed after a batch terminator is encountered.</span></span> <span data-ttu-id="0357e-630">您可以發出多個 **:r** 命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-630">You can issue multiple **:r** commands.</span></span> <span data-ttu-id="0357e-631">這個檔案可包含任何 `sqlcmd` 命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-631">The file may include any `sqlcmd` command.</span></span> <span data-ttu-id="0357e-632">其中包括批次結束字元 **GO**。</span><span class="sxs-lookup"><span data-stu-id="0357e-632">This includes the batch terminator **GO**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-633">每次發現 **:r** 命令時，以互動模式顯示的行數便會加 1。</span><span class="sxs-lookup"><span data-stu-id="0357e-633">The line count that is displayed in interactive mode will be increased by one for every **:r** command encountered.</span></span> <span data-ttu-id="0357e-634">**:r** 命令會出現在 list 命令的輸出中。</span><span class="sxs-lookup"><span data-stu-id="0357e-634">The **:r** command will appear in the output of the list command.</span></span>  
  
 <span data-ttu-id="0357e-635">**:Serverlist**</span><span class="sxs-lookup"><span data-stu-id="0357e-635">**:Serverlist**</span></span>  
 <span data-ttu-id="0357e-636">列出設定在本機的伺服器，以及在網路中進行廣播的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-636">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
 <span data-ttu-id="0357e-637">**： Connect** _server_name_[ **\\** _instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span><span class="sxs-lookup"><span data-stu-id="0357e-637">**:Connect** _server_name_[**\\**_instance_name_] [-l *timeout*] [-U *user_name* [-P *password*]]</span></span>  
 <span data-ttu-id="0357e-638">連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0357e-638">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0357e-639">此外也會關閉目前的連接。</span><span class="sxs-lookup"><span data-stu-id="0357e-639">Also closes the current connection.</span></span>  
  
 <span data-ttu-id="0357e-640">逾時選項：</span><span class="sxs-lookup"><span data-stu-id="0357e-640">Time-out options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0357e-641">0</span><span class="sxs-lookup"><span data-stu-id="0357e-641">0</span></span>|<span data-ttu-id="0357e-642">永久等候</span><span class="sxs-lookup"><span data-stu-id="0357e-642">wait forever</span></span>|  
|<span data-ttu-id="0357e-643">n>0</span><span class="sxs-lookup"><span data-stu-id="0357e-643">n>0</span></span>|<span data-ttu-id="0357e-644">等候 n 秒</span><span class="sxs-lookup"><span data-stu-id="0357e-644">wait for n seconds</span></span>|  
  
 <span data-ttu-id="0357e-645">SQLCMDSERVER 指令碼變數會反映目前作用中的連接。</span><span class="sxs-lookup"><span data-stu-id="0357e-645">The SQLCMDSERVER scripting variable will reflect the current active connection.</span></span>  
  
 <span data-ttu-id="0357e-646">如果沒有指定 *timeout* ，預設值就是 SQLCMDLOGINTIMEOUT 變數的值。</span><span class="sxs-lookup"><span data-stu-id="0357e-646">If *timeout* is not specified, the value of the SQLCMDLOGINTIMEOUT variable is the default.</span></span>  
  
 <span data-ttu-id="0357e-647">如果只指定 *user_name* (作為選項或作為環境變數)，則會提示使用者輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="0357e-647">If only *user_name* is specified (either as an option, or as an environment variable), the user will be prompted to enter a password.</span></span> <span data-ttu-id="0357e-648">如果已設定 SQLCMDUSER 或 SQLCMDPASSWORD 環境變數，就不會提示。</span><span class="sxs-lookup"><span data-stu-id="0357e-648">This is not true if the SQLCMDUSER or SQLCMDPASSWORD environment variables have been set.</span></span> <span data-ttu-id="0357e-649">如果既沒有提供選項，也沒有提供環境變數，就會利用 Windows 驗證模式來登入。</span><span class="sxs-lookup"><span data-stu-id="0357e-649">If neither options nor environment variables are provided, Windows Authentication mode is used to login.</span></span> <span data-ttu-id="0357e-650">例如，若要利用整合式安全性連接 `instance1`( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) 的執行個體 `myserver`，您將使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0357e-650">For example to connect to an instance, `instance1`, of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `myserver`, by using integrated security you would use the following:</span></span>  
  
 `:connect myserver\instance1`  
  
 <span data-ttu-id="0357e-651">若要利用指令碼變數來連接 `myserver` 的預設執行個體，您將使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0357e-651">To connect to the default instance of `myserver` using scripting variables, you would use the following:</span></span>  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 <span data-ttu-id="0357e-652">[**:**] **!!**\< *command*></span><span class="sxs-lookup"><span data-stu-id="0357e-652">[**:**] **!!**\< *command*></span></span>  
 <span data-ttu-id="0357e-653">執行作業系統命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-653">Executes operating system commands.</span></span> <span data-ttu-id="0357e-654">若要執行作業系統命令，請在行首輸入兩個驚歎號 ( **!!** )，後面再接著作業系統命令。</span><span class="sxs-lookup"><span data-stu-id="0357e-654">To execute an operating system command, start a line with two exclamation marks (**!!**) followed by the operating system command.</span></span> <span data-ttu-id="0357e-655">例如：</span><span class="sxs-lookup"><span data-stu-id="0357e-655">For example:</span></span>  
  
 `:!! Dir`  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-656">這個命令會在執行 `sqlcmd` 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0357e-656">The command is executed on the computer on which `sqlcmd` is running.</span></span>  
  
 <span data-ttu-id="0357e-657">**:XML** [**ON** | **OFF**]</span><span class="sxs-lookup"><span data-stu-id="0357e-657">**:XML** [**ON** | **OFF**]</span></span>  
 <span data-ttu-id="0357e-658">如需詳細資訊，請參閱本主題稍後的＜XML 輸出格式＞。</span><span class="sxs-lookup"><span data-stu-id="0357e-658">For more information, see "XML Output Format," later in this topic</span></span>  
  
 <span data-ttu-id="0357e-659">**:Help**</span><span class="sxs-lookup"><span data-stu-id="0357e-659">**:Help**</span></span>  
 <span data-ttu-id="0357e-660">列出 `sqlcmd` 命令及各命令的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="0357e-660">Lists `sqlcmd` commands together with a short description of each command.</span></span>  
  
### <a name="sqlcmd-file-names"></a><span data-ttu-id="0357e-661">sqlcmd 檔案名稱</span><span class="sxs-lookup"><span data-stu-id="0357e-661">sqlcmd File Names</span></span>  
 <span data-ttu-id="0357e-662">`sqlcmd`輸入檔可以使用 **-i**選項或 **： r**命令來指定。</span><span class="sxs-lookup"><span data-stu-id="0357e-662">`sqlcmd` input files can be specified with the **-i** option or the **:r** command.</span></span> <span data-ttu-id="0357e-663">輸出檔則可以使用 **-o** 選項或 **:Error**、 **:Out** 和 **:Perftrace** 命令予以指定。</span><span class="sxs-lookup"><span data-stu-id="0357e-663">Output files can be specified with the **-o** option or the **:Error**, **:Out** and **:Perftrace** commands.</span></span> <span data-ttu-id="0357e-664">以下列出使用這些檔案的幾項指導方針：</span><span class="sxs-lookup"><span data-stu-id="0357e-664">The following are some guidelines for working with these files:</span></span>  
  
-   <span data-ttu-id="0357e-665">**： Error**、 **： Out**和 **:P erftrace**應該使用不同 **<*`filename`*>** 的。</span><span class="sxs-lookup"><span data-stu-id="0357e-665">**:Error**, **:Out** and **:Perftrace** should use separate **<*`filename`*>**.</span></span> <span data-ttu-id="0357e-666">如果使用相同的 **<*`filename`*>** ，來自命令的輸入可能會混合在一起。</span><span class="sxs-lookup"><span data-stu-id="0357e-666">If the same **<*`filename`*>** is used, inputs from the commands may be intermixed.</span></span>  
  
-   <span data-ttu-id="0357e-667">如果從本機電腦的 `sqlcmd` 呼叫位於遠端伺服器上的輸入檔，且檔案中包含磁碟機檔案路徑 (例如 :out c:\OutputFile.txt)，</span><span class="sxs-lookup"><span data-stu-id="0357e-667">If an input file that is located on a remote server is called from `sqlcmd` on a local computer and the file contains a drive file path such as :out c:\OutputFile.txt.</span></span> <span data-ttu-id="0357e-668">便會在本機電腦建立輸出檔案，而不是在遠端伺服器建立。</span><span class="sxs-lookup"><span data-stu-id="0357e-668">The output file will be created on the local computer and not on the remote server.</span></span>  
  
-   <span data-ttu-id="0357e-669">有效的檔案路徑包括： C： \\ **<*`filename`*>** 、 \\ \\<Server \> \\<共用 $>\\ **<*`filename`*>** 和「C:\Some 資料夾」 \\ **<*`file name`*>** 。</span><span class="sxs-lookup"><span data-stu-id="0357e-669">Valid file paths include: C:\\**<*`filename`*>**, \\\\<Server\>\\<Share$>\\**<*`filename`*>** and "C:\Some Folder\\**<*`file name`*>**".</span></span> <span data-ttu-id="0357e-670">如果路徑中有空格，請使用引號。</span><span class="sxs-lookup"><span data-stu-id="0357e-670">If there is a space in the path, use quotation marks.</span></span>  
  
-   <span data-ttu-id="0357e-671">每個新的 `sqlcmd` 工作階段都會覆寫現有的同名檔案。</span><span class="sxs-lookup"><span data-stu-id="0357e-671">Each new `sqlcmd` session will overwrite existing files that have the same names.</span></span>  
  
### <a name="informational-messages"></a><span data-ttu-id="0357e-672">參考用訊息</span><span class="sxs-lookup"><span data-stu-id="0357e-672">Informational Messages</span></span>  
 <span data-ttu-id="0357e-673">`sqlcmd` 會列印伺服器所傳送的所有參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-673">`sqlcmd` prints any informational message that are sent by the server.</span></span> <span data-ttu-id="0357e-674">在下列範例中，執行 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式之後，會列印一則參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-674">In the following example, after the [!INCLUDE[tsql](../includes/tsql-md.md)] statements are executed, an informational message is printed.</span></span>  
  
 <span data-ttu-id="0357e-675">在命令提示字元中，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="0357e-675">At the command prompt, type the following:</span></span>  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 <span data-ttu-id="0357e-676">當您按 ENTER 時，會列印下列參考訊息：「已將資料庫內容變更為 'AdventureWorks2012'。」</span><span class="sxs-lookup"><span data-stu-id="0357e-676">When you press ENTER, the following informational message is printed: "Changed database context to 'AdventureWorks2012'."</span></span>  
  
### <a name="output-format-from-transact-sql-queries"></a><span data-ttu-id="0357e-677">Transact-SQL 查詢的輸出格式</span><span class="sxs-lookup"><span data-stu-id="0357e-677">Output Format from Transact-SQL Queries</span></span>  
 <span data-ttu-id="0357e-678">`sqlcmd` 會先列印包含選取清單中所指定之資料行名稱的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="0357e-678">`sqlcmd` first prints a column header that contains the column names specified in the select list.</span></span> <span data-ttu-id="0357e-679">資料行名稱是以 SQLCMDCOLSEP 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="0357e-679">The column names are separated by using the SQLCMDCOLSEP character.</span></span> <span data-ttu-id="0357e-680">根據預設，這是一個空格。</span><span class="sxs-lookup"><span data-stu-id="0357e-680">By default, this is a space.</span></span> <span data-ttu-id="0357e-681">如果資料行名稱長度小於資料行寬度，便會在輸出中填補空格直到下一個資料行。</span><span class="sxs-lookup"><span data-stu-id="0357e-681">If the column name is shorter than the column width, the output is padded with spaces up to the next column.</span></span>  
  
 <span data-ttu-id="0357e-682">這一行後面會接著一條由虛線字元組成的分隔線。</span><span class="sxs-lookup"><span data-stu-id="0357e-682">This line will be followed by a separator line that is a series of dash characters.</span></span> <span data-ttu-id="0357e-683">下列輸出顯示一個範例。</span><span class="sxs-lookup"><span data-stu-id="0357e-683">The following output shows an example.</span></span>  
  
 <span data-ttu-id="0357e-684">啟動 `sqlcmd`。</span><span class="sxs-lookup"><span data-stu-id="0357e-684">Start `sqlcmd`.</span></span> <span data-ttu-id="0357e-685">在 `sqlcmd` 命令提示字元處，請輸入下列項目：</span><span class="sxs-lookup"><span data-stu-id="0357e-685">At the `sqlcmd` command prompt, type the following:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="0357e-686">當您按下 ENTER，就會傳回下列結果集。</span><span class="sxs-lookup"><span data-stu-id="0357e-686">When you press ENTER, the following result set is returned.</span></span>  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 <span data-ttu-id="0357e-687">雖然 `BusinessEntityID` 資料行的寬度只有 4 個字元，但它已擴充，能夠容納較長的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="0357e-687">Although the `BusinessEntityID` column is only 4 characters wide, it has been expanded to accommodate the longer column name.</span></span> <span data-ttu-id="0357e-688">依預設，輸出的長度最多為 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="0357e-688">By default, output is terminated at 80 characters.</span></span> <span data-ttu-id="0357e-689">您可以利用 **-w** 選項或設定 SQLCMDCOLWIDTH 指令碼變數，變更此設定。</span><span class="sxs-lookup"><span data-stu-id="0357e-689">This can be changed by using the **-w** option, or by setting the SQLCMDCOLWIDTH scripting variable.</span></span>  
  
### <a name="xml-output-format"></a><span data-ttu-id="0357e-690">XML 輸出格式</span><span class="sxs-lookup"><span data-stu-id="0357e-690">XML Output Format</span></span>  
 <span data-ttu-id="0357e-691">FOR XML 子句所產生的 XML 輸出，會在連續資料流中以未格式化的形式輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-691">XML output that is the result of a FOR XML clause is output, unformatted, in a continuous stream.</span></span>  
  
 <span data-ttu-id="0357e-692">當您希望產生 XML 輸出時，請使用下列命令： `:XML ON`。</span><span class="sxs-lookup"><span data-stu-id="0357e-692">When you expect XML output, use the following command: `:XML ON`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-693">`sqlcmd` 會以一般格式傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-693">`sqlcmd` returns error messages in the usual format.</span></span> <span data-ttu-id="0357e-694">請注意，錯誤訊息也會以 XML 格式輸出至 XML 文字資料流。</span><span class="sxs-lookup"><span data-stu-id="0357e-694">Notice that the error messages are also output in the XML text stream in XML format.</span></span> <span data-ttu-id="0357e-695">如果使用 `:XML ON`，`sqlcmd` 就不會顯示參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="0357e-695">By using `:XML ON`, `sqlcmd` does not display informational messages.</span></span>  
  
 <span data-ttu-id="0357e-696">若要將 XML 模式設定為關閉，請使用下列命令： `:XML OFF`。</span><span class="sxs-lookup"><span data-stu-id="0357e-696">To set the XML mode off, use the following command: `:XML OFF`.</span></span>  
  
 <span data-ttu-id="0357e-697">在發出 XML OFF 命令之前，不應出現 GO 命令，因為 XML OFF 命令會將 `sqlcmd` 切換回資料列導向的輸出。</span><span class="sxs-lookup"><span data-stu-id="0357e-697">The GO command should not appear before the XML OFF command is issued because the XML OFF command switches `sqlcmd` back to row-oriented output.</span></span>  
  
 <span data-ttu-id="0357e-698">XML (資料流) 資料和資料列集不能混合。</span><span class="sxs-lookup"><span data-stu-id="0357e-698">XML (streamed) data and rowset data cannot be mixed.</span></span> <span data-ttu-id="0357e-699">如果在執行輸出 XML 資料流的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式之前發出 XML ON 命令，輸出會混亂。</span><span class="sxs-lookup"><span data-stu-id="0357e-699">If the XML ON command has not been issued before a [!INCLUDE[tsql](../includes/tsql-md.md)] statement that outputs XML streams is executed, the output will be garbled.</span></span> <span data-ttu-id="0357e-700">如果已發出 XML ON 命令，您就不能執行輸出正規資料列集的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0357e-700">If the XML ON command has been issued, you cannot execute [!INCLUDE[tsql](../includes/tsql-md.md)] statements that output regular row sets.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0357e-701">**:XML** 命令不支援 SET STATISTICS XML 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0357e-701">The **:XML** command does not support the SET STATISTICS XML statement.</span></span>  
  
## <a name="sqlcmd-best-practices"></a><span data-ttu-id="0357e-702">sqlcmd 最佳作法</span><span class="sxs-lookup"><span data-stu-id="0357e-702">sqlcmd Best Practices</span></span>  
 <span data-ttu-id="0357e-703">請採用下列作法以提高安全性與效率。</span><span class="sxs-lookup"><span data-stu-id="0357e-703">Use the following practices to help maximize security and efficiency.</span></span>  
  
-   <span data-ttu-id="0357e-704">使用整合式安全性。</span><span class="sxs-lookup"><span data-stu-id="0357e-704">Use integrated security.</span></span>  
  
-   <span data-ttu-id="0357e-705">在自動化環境中使用 `-X`。</span><span class="sxs-lookup"><span data-stu-id="0357e-705">Use `-X` in automated environments.</span></span>  
  
-   <span data-ttu-id="0357e-706">利用 NTFS 檔案系統權限保護輸入檔和輸出檔。</span><span class="sxs-lookup"><span data-stu-id="0357e-706">Secure input and output files by using appropriate NTFS file system permissions.</span></span>  
  
-   <span data-ttu-id="0357e-707">為提高效能，請盡可能在單一 `sqlcmd` 工作階段中執行所有工作，而不要使用一連串的工作階段。</span><span class="sxs-lookup"><span data-stu-id="0357e-707">To increase performance, do as much in one `sqlcmd` session as you can, instead of in a series of sessions.</span></span>  
  
-   <span data-ttu-id="0357e-708">將批次或查詢執行的逾時值，設定成高於您預期執行批次或查詢所需的時間值。</span><span class="sxs-lookup"><span data-stu-id="0357e-708">Set time-out values for batch or query execution higher than you expect it will take to execute the batch or query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0357e-709">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0357e-709">See Also</span></span>  
 <span data-ttu-id="0357e-710">[啟動 sqlcmd 公用程式](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-710">[Start the sqlcmd Utility](../relational-databases/scripting/sqlcmd-start-the-utility.md) </span></span>  
 <span data-ttu-id="0357e-711">[使用 sqlcmd 執行 Transact-SQL 指令碼檔案](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-711">[Run Transact-SQL Script Files Using sqlcmd](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md) </span></span>  
 <span data-ttu-id="0357e-712">[使用 sqlcmd 公用程式](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-712">[Use the sqlcmd Utility](../relational-databases/scripting/sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="0357e-713">[以指令碼變數使用 sqlcmd](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-713">[Use sqlcmd with Scripting Variables](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="0357e-714">[使用 sqlcmd 連接至 Database Engine](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-714">[Connect to the Database Engine With sqlcmd](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md) </span></span>  
 <span data-ttu-id="0357e-715">[使用查詢編輯器編輯 SQLCMD 指令碼](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-715">[Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="0357e-716">[管理作業步驟](../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="0357e-716">[Manage Job Steps](../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="0357e-717">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="0357e-717">Create a CmdExec Job Step</span></span>](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
