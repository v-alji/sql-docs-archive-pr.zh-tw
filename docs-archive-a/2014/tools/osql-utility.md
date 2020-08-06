---
title: osql 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- operating systems [SQL Server], commands
- osql utility [SQL Server]
- stored procedures [SQL Server], command prompt
- scripts [SQL Server], command prompt
- RESET command
- GO command
- command prompt utilities [SQL Server], osql
- CTRL+C command
ms.assetid: cf530d9e-0609-4528-8975-ab8e08e40b9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95782afe0de8567781316e3478d04a090f968ed5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686614"
---
# <a name="osql-utility"></a><span data-ttu-id="dbba1-102">osql 公用程式</span><span class="sxs-lookup"><span data-stu-id="dbba1-102">osql Utility</span></span>
  <span data-ttu-id="dbba1-103">**osql** 公用程式可讓您輸入 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式、系統程序和指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dbba1-103">The **osql** utility allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files.</span></span> <span data-ttu-id="dbba1-104">這個公用程式利用 ODBC 來與伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="dbba1-104">This utility uses ODBC to communicate with the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbba1-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的未來版本將移除此功能。</span><span class="sxs-lookup"><span data-stu-id="dbba1-105">This feature will be removed in a future version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbba1-106">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-106">Avoid using this feature in new development work, and plan to modify applications that currently use the feature.</span></span> <span data-ttu-id="dbba1-107">改用 **sqlcmd** 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-107">Use **sqlcmd** instead.</span></span> <span data-ttu-id="dbba1-108">如需詳細資訊，請參閱 [sqlcmd Utility](sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-108">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbba1-109">語法</span><span class="sxs-lookup"><span data-stu-id="dbba1-109">Syntax</span></span>  
  
```  
  
      osql  
[-?] |  
[-L] |  
[  
  {  
     {-Ulogin_id [-Ppassword]} | -E }  
     [-Sserver_name[\instance_name]] [-Hwksta_name] [-ddb_name]  
     [-ltime_out] [-ttime_out] [-hheaders]  
     [-scol_separator] [-wcolumn_width] [-apacket_size]  
     [-e] [-I] [-D data_source_name]  
     [-ccmd_end] [-q "query"] [-Q"query"]  
     [-n] [-merror_level] [-r {0 | 1}]  
     [-iinput_file] [-ooutput_file] [-p]  
     [-b] [-u] [-R] [-O]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="dbba1-110">引數</span><span class="sxs-lookup"><span data-stu-id="dbba1-110">Arguments</span></span>  
 <span data-ttu-id="dbba1-111">**-?**</span><span class="sxs-lookup"><span data-stu-id="dbba1-111">**-?**</span></span>  
 <span data-ttu-id="dbba1-112">顯示 **osql** 參數的語法摘要。</span><span class="sxs-lookup"><span data-stu-id="dbba1-112">Displays the syntax summary of **osql** switches.</span></span>  
  
 <span data-ttu-id="dbba1-113">**-L**</span><span class="sxs-lookup"><span data-stu-id="dbba1-113">**-L**</span></span>  
 <span data-ttu-id="dbba1-114">列出設定在本機的伺服器，以及在網路中進行廣播的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="dbba1-114">Lists the locally configured servers and the names of the servers broadcasting on the network.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-115">由於網路廣播的本質，因此 **osql** 可能不會收到所有伺服器的及時回應。</span><span class="sxs-lookup"><span data-stu-id="dbba1-115">Due to the nature of broadcasting on networks, **osql** may not receive a timely response from all servers.</span></span> <span data-ttu-id="dbba1-116">因此，這個選項各次的引動過程，傳回的伺服器清單可能各不相同。</span><span class="sxs-lookup"><span data-stu-id="dbba1-116">Therefore the list of servers returned may vary for each invocation of this option.</span></span>  
  
 <span data-ttu-id="dbba1-117">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="dbba1-117">**-U** _login_id_</span></span>  
 <span data-ttu-id="dbba1-118">這是使用者登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-118">Is the user login ID.</span></span> <span data-ttu-id="dbba1-119">登入識別碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="dbba1-119">Login IDs are case-sensitive.</span></span>  
  
 <span data-ttu-id="dbba1-120">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="dbba1-120">**-P** _password_</span></span>  
 <span data-ttu-id="dbba1-121">這是一個使用者指定的密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-121">Is a user-specified password.</span></span> <span data-ttu-id="dbba1-122">若未使用 **-P** 選項，則 **osql** 會提示輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-122">If the **-P** option is not used, **osql** prompts for a password.</span></span> <span data-ttu-id="dbba1-123">若在命令提示字元的尾端使用 **-P** 選項且無任何密碼，則 **osql** 會使用預設密碼 (NULL)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-123">If the **-P** option is used at the end of the command prompt without any password, **osql** uses the default password (NULL).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbba1-124">請勿使用空白密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-124">Do not use a blank password.</span></span> <span data-ttu-id="dbba1-125">請使用增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-125">Use a strong password.</span></span> <span data-ttu-id="dbba1-126">如需詳細資訊，請參閱 [Strong Passwords](../relational-databases/security/strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-126">For more information, see [Strong Passwords](../relational-databases/security/strong-passwords.md).</span></span>  
  
 <span data-ttu-id="dbba1-127">密碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="dbba1-127">Passwords are case-sensitive.</span></span>  
  
 <span data-ttu-id="dbba1-128">OSQLPASSWORD 環境變數可讓您設定目前工作階段的預設密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-128">The OSQLPASSWORD environment variable allows you to set a default password for the current session.</span></span> <span data-ttu-id="dbba1-129">因此，您不需要將密碼寫在批次檔中。</span><span class="sxs-lookup"><span data-stu-id="dbba1-129">Therefore, you do not have to hard code a password into batch files.</span></span>  
  
 <span data-ttu-id="dbba1-130">若您未使用 **-P** 選項指定密碼，則 **osql** 會先檢查 OSQLPASSWORD 變數。</span><span class="sxs-lookup"><span data-stu-id="dbba1-130">If you do not specify a password with the **-P** option, **osql** first checks for the OSQLPASSWORD variable.</span></span> <span data-ttu-id="dbba1-131">若未設定任何值，則 **osql** 會使用預設密碼 NULL。</span><span class="sxs-lookup"><span data-stu-id="dbba1-131">If no value is set, **osql** uses the default password, NULL.</span></span> <span data-ttu-id="dbba1-132">下列範例會在命令提示字元設定 OSQLPASSWORD 變數，然後再存取 **osql** 公用程式：</span><span class="sxs-lookup"><span data-stu-id="dbba1-132">The following example sets the OSQLPASSWORD variable at a command prompt and then accesses the **osql** utility:</span></span>  
  
```  
C:\>SET OSQLPASSWORD=abracadabra  
C:\>osql   
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbba1-133">若要遮罩您的密碼，請勿連同 **-P** 選項指定 **-U** 選項。</span><span class="sxs-lookup"><span data-stu-id="dbba1-133">To mask your password, do not specify the **-P** option along with the **-U** option.</span></span> <span data-ttu-id="dbba1-134">而是改為在搭配 **-U** 選項及其他參數 (不指定 **-P** ) 指定 **osql**後，按下 ENTER，接著 **osql** 就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-134">Instead, after specifying **osql** along with the **-U** option and other switches (do not specify **-P**), press ENTER, and **osql** will prompt you for a password.</span></span> <span data-ttu-id="dbba1-135">這個方法可確保在輸入密碼時，遮罩您的密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-135">This method ensures that your password will be masked when it is entered.</span></span>  
  
 <span data-ttu-id="dbba1-136">**-E**</span><span class="sxs-lookup"><span data-stu-id="dbba1-136">**-E**</span></span>  
 <span data-ttu-id="dbba1-137">使用信任連接，不要求密碼。</span><span class="sxs-lookup"><span data-stu-id="dbba1-137">Uses a trusted connection instead of requesting a password.</span></span>  
  
 <span data-ttu-id="dbba1-138">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="dbba1-138">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="dbba1-139">指定要連接的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbba1-139">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="dbba1-140">指定 *server_name* ，即可連接至該伺服器上之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbba1-140">Specify *server_name* to connect to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="dbba1-141">指定_server_name_ **\\** 要連接到該伺服器上之已命名實例的 server_name_instance_name_ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-141">Specify _server_name_**\\**_instance_name_ to connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on that server.</span></span> <span data-ttu-id="dbba1-142">若未指定伺服器，則 **osql** 會連接到本機電腦的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbba1-142">If no server is specified, **osql** connects to the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="dbba1-143">從網路中的遠端電腦執行 **osql** 時，需要使用此選項。</span><span class="sxs-lookup"><span data-stu-id="dbba1-143">This option is required when executing **osql** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="dbba1-144">**-H** _wksta_name_</span><span class="sxs-lookup"><span data-stu-id="dbba1-144">**-H** _wksta_name_</span></span>  
 <span data-ttu-id="dbba1-145">這是一個工作站名稱。</span><span class="sxs-lookup"><span data-stu-id="dbba1-145">Is a workstation name.</span></span> <span data-ttu-id="dbba1-146">工作站名稱儲存在 **sysprocesses.hostname** 中， **sp_who**會顯示它。</span><span class="sxs-lookup"><span data-stu-id="dbba1-146">The workstation name is stored in **sysprocesses.hostname** and is displayed by **sp_who**.</span></span> <span data-ttu-id="dbba1-147">如果未指定這個選項，就會假設目前的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="dbba1-147">If this option is not specified, the current computer name is assumed.</span></span>  
  
 <span data-ttu-id="dbba1-148">**-d** _db_name_</span><span class="sxs-lookup"><span data-stu-id="dbba1-148">**-d** _db_name_</span></span>  
 <span data-ttu-id="dbba1-149">啟動 *osql* 時發出 USE **db_name**陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-149">Issues a USE *db_name* statement when **osql**is started.</span></span>  
  
 <span data-ttu-id="dbba1-150">**-l** _time_out_</span><span class="sxs-lookup"><span data-stu-id="dbba1-150">**-l** _time_out_</span></span>  
 <span data-ttu-id="dbba1-151">指定 **osql** 登入逾時之前的秒數。**osql** 的預設登入逾時值是八秒。</span><span class="sxs-lookup"><span data-stu-id="dbba1-151">Specifies the number of seconds before an **osql** login times out. The default time-out for login to **osql** is eight seconds.</span></span>  
  
 <span data-ttu-id="dbba1-152">**-t** _time_out_</span><span class="sxs-lookup"><span data-stu-id="dbba1-152">**-t** _time_out_</span></span>  
 <span data-ttu-id="dbba1-153">指定命令逾時之前的秒數。如果未指定 *time_out* 值，命令不會逾時。</span><span class="sxs-lookup"><span data-stu-id="dbba1-153">Specifies the number of seconds before a command times out. If a *time_out* value is not specified, commands do not time out.</span></span>  
  
 <span data-ttu-id="dbba1-154">**-h** _headers_</span><span class="sxs-lookup"><span data-stu-id="dbba1-154">**-h** _headers_</span></span>  
 <span data-ttu-id="dbba1-155">指定資料行標頭之間所要列印的資料列數。</span><span class="sxs-lookup"><span data-stu-id="dbba1-155">Specifies the number of rows to print between column headings.</span></span> <span data-ttu-id="dbba1-156">預設值是每一組查詢結果各列印一次標頭。</span><span class="sxs-lookup"><span data-stu-id="dbba1-156">The default is to print headings one time for each set of query results.</span></span> <span data-ttu-id="dbba1-157">請利用 -1 來指定不列印任何標頭。</span><span class="sxs-lookup"><span data-stu-id="dbba1-157">Use -1 to specify that no headers will be printed.</span></span> <span data-ttu-id="dbba1-158">若使用 -1，則參數和設定之間不能有空格 ( **-h-1**，而非 **-h -1**)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-158">If -1 is used, there must be no space between the parameter and the setting (**-h-1**, not **-h -1**).</span></span>  
  
 <span data-ttu-id="dbba1-159">**-s** _col_separator_</span><span class="sxs-lookup"><span data-stu-id="dbba1-159">**-s** _col_separator_</span></span>  
 <span data-ttu-id="dbba1-160">指定資料行分隔字元，依預設，它是一個空格。</span><span class="sxs-lookup"><span data-stu-id="dbba1-160">Specifies the column-separator character, which is a blank space by default.</span></span> <span data-ttu-id="dbba1-161">若要使用對作業系統有特殊意義的字元 (例如，|;& \< >) 中，以雙引號括住字元 ( ") 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-161">To use characters that have special meaning to the operating system (for example, | ; & \< >), enclose the character in double quotation marks (").</span></span>  
  
 <span data-ttu-id="dbba1-162">**-w** _column_width_</span><span class="sxs-lookup"><span data-stu-id="dbba1-162">**-w** _column_width_</span></span>  
 <span data-ttu-id="dbba1-163">可讓使用者設定輸出的螢幕寬度。</span><span class="sxs-lookup"><span data-stu-id="dbba1-163">Allows the user to set the screen width for output.</span></span> <span data-ttu-id="dbba1-164">預設值是 80 個字元。</span><span class="sxs-lookup"><span data-stu-id="dbba1-164">The default is 80 characters.</span></span> <span data-ttu-id="dbba1-165">當輸出行到達最大螢幕寬度時，它會折成多行。</span><span class="sxs-lookup"><span data-stu-id="dbba1-165">When an output line has reached its maximum screen width, it is broken into multiple lines.</span></span>  
  
 <span data-ttu-id="dbba1-166">**-a** _packet_size_</span><span class="sxs-lookup"><span data-stu-id="dbba1-166">**-a** _packet_size_</span></span>  
 <span data-ttu-id="dbba1-167">可讓您要求不同大小的封包。</span><span class="sxs-lookup"><span data-stu-id="dbba1-167">Allows you to request a different-sized packet.</span></span> <span data-ttu-id="dbba1-168">*packet_size* 的有效值為 512 到 65535。</span><span class="sxs-lookup"><span data-stu-id="dbba1-168">The valid values for *packet_size* are 512 through 65535.</span></span> <span data-ttu-id="dbba1-169">預設值 **osql** 為伺服器預設值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-169">The default value **osql** is the server default.</span></span> <span data-ttu-id="dbba1-170">增加的封包大小可加強較大指令碼執行 (其中 GO 命令之間的 SQL 陳述式數量很大) 的效能。</span><span class="sxs-lookup"><span data-stu-id="dbba1-170">Increased packet size can enhance performance on larger script execution where the amount of SQL statements between GO commands is substantial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="dbba1-171">測試指出 8192 通常是大量複製作業的最快設定。</span><span class="sxs-lookup"><span data-stu-id="dbba1-171">testing indicates that 8192 is typically the fastest setting for bulk copy operations.</span></span> <span data-ttu-id="dbba1-172">您可以要求較大的封包，但如果無法授與要求，則 **osql** 會預設為伺服器預設值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-172">A larger packet size can be requested, but **osql** defaults to the server default if the request cannot be granted.</span></span>  
  
 <span data-ttu-id="dbba1-173">**-e**</span><span class="sxs-lookup"><span data-stu-id="dbba1-173">**-e**</span></span>  
 <span data-ttu-id="dbba1-174">回應輸入。</span><span class="sxs-lookup"><span data-stu-id="dbba1-174">Echoes input.</span></span>  
  
 <span data-ttu-id="dbba1-175">**-I**</span><span class="sxs-lookup"><span data-stu-id="dbba1-175">**-I**</span></span>  
 <span data-ttu-id="dbba1-176">將 QUOTED_IDENTIFIER 連接選項設為開啟。</span><span class="sxs-lookup"><span data-stu-id="dbba1-176">Sets the QUOTED_IDENTIFIER connection option on.</span></span>  
  
 <span data-ttu-id="dbba1-177">**-D** _data_source_name_</span><span class="sxs-lookup"><span data-stu-id="dbba1-177">**-D** _data_source_name_</span></span>  
 <span data-ttu-id="dbba1-178">連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的 ODBC 驅動程式所定義的 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="dbba1-178">Connects to an ODBC data source that is defined using the ODBC driver for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dbba1-179">**osql** 連接會使用資料來源所指定的選項。</span><span class="sxs-lookup"><span data-stu-id="dbba1-179">The **osql** connection uses the options specified in the data source.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-180">這個選項不會使用定義給其他驅動程式的資料來源。</span><span class="sxs-lookup"><span data-stu-id="dbba1-180">This option does not work with data sources defined for other drivers.</span></span>  
  
 <span data-ttu-id="dbba1-181">**-c** _cmd_end_</span><span class="sxs-lookup"><span data-stu-id="dbba1-181">**-c** _cmd_end_</span></span>  
 <span data-ttu-id="dbba1-182">指定命令結束字元。</span><span class="sxs-lookup"><span data-stu-id="dbba1-182">Specifies the command terminator.</span></span> <span data-ttu-id="dbba1-183">依預設，在一行中單獨輸入 GO，便會終止命令，並將命令傳給 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-183">By default, commands are terminated and sent to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by entering GO on a line by itself.</span></span> <span data-ttu-id="dbba1-184">當您重設命令結束字元時，請勿使用對作業系統有特殊意義的 [!INCLUDE[tsql](../includes/tsql-md.md)] 保留字或字元，不論前面是否附加了反斜線，都是一樣。</span><span class="sxs-lookup"><span data-stu-id="dbba1-184">When you reset the command terminator, do not use [!INCLUDE[tsql](../includes/tsql-md.md)] reserved words or characters that have special meaning to the operating system, whether preceded by a backslash or not.</span></span>  
  
 <span data-ttu-id="dbba1-185">**-q "** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="dbba1-185">**-q "** _query_ **"**</span></span>  
 <span data-ttu-id="dbba1-186">啟動 **osql** 時便執行查詢，但查詢完成時 **osql** 不會結束。</span><span class="sxs-lookup"><span data-stu-id="dbba1-186">Executes a query when **osql** starts, but does not exit **osql** when the query completes.</span></span> <span data-ttu-id="dbba1-187">(請注意，查詢陳述式不應包含 GO)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-187">(Note that the query statement should not include GO).</span></span> <span data-ttu-id="dbba1-188">如果您是從批次檔中發出查詢，請使用變數 (%variables) 或環境變數 (%variables%)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-188">If you issue a query from a batch file, use %variables, or environment %variables%.</span></span> <span data-ttu-id="dbba1-189">例如：</span><span class="sxs-lookup"><span data-stu-id="dbba1-189">For example:</span></span>  
  
```  
SET table=sys.objects  
osql -E -q "select name, object_id from %table%"  
```  
  
 <span data-ttu-id="dbba1-190">請利用雙引號括住查詢，利用單引號括住內嵌在查詢中的任何項目。</span><span class="sxs-lookup"><span data-stu-id="dbba1-190">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="dbba1-191">**-Q"** _query_ **"**</span><span class="sxs-lookup"><span data-stu-id="dbba1-191">**-Q"** _query_ **"**</span></span>  
 <span data-ttu-id="dbba1-192">執行查詢並立即結束 **osql**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-192">Executes a query and immediately exits **osql**.</span></span> <span data-ttu-id="dbba1-193">請利用雙引號括住查詢，利用單引號括住內嵌在查詢中的任何項目。</span><span class="sxs-lookup"><span data-stu-id="dbba1-193">Use double quotation marks around the query and single quotation marks around anything embedded in the query.</span></span>  
  
 <span data-ttu-id="dbba1-194">**-n**</span><span class="sxs-lookup"><span data-stu-id="dbba1-194">**-n**</span></span>  
 <span data-ttu-id="dbba1-195">從輸入行中，移除編號和提示符號 (>)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-195">Removes numbering and the prompt symbol (>) from input lines.</span></span>  
  
 <span data-ttu-id="dbba1-196">**-m** _error_level_</span><span class="sxs-lookup"><span data-stu-id="dbba1-196">**-m** _error_level_</span></span>  
 <span data-ttu-id="dbba1-197">自訂錯誤訊息的顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="dbba1-197">Customizes the display of error messages.</span></span> <span data-ttu-id="dbba1-198">在指定嚴重性層級或以上的錯誤，會顯示訊息編號、狀態和錯誤層級。</span><span class="sxs-lookup"><span data-stu-id="dbba1-198">The message number, state, and error level are displayed for errors of the specified severity level or higher.</span></span> <span data-ttu-id="dbba1-199">在指定層級以下的錯誤不會顯示任何資訊。</span><span class="sxs-lookup"><span data-stu-id="dbba1-199">Nothing is displayed for errors of levels lower than the specified level.</span></span> <span data-ttu-id="dbba1-200">請利用 **-1** 來指定訊息傳回所有標頭，即使參考訊息也是如此。</span><span class="sxs-lookup"><span data-stu-id="dbba1-200">Use **-1** to specify that all headers are returned with messages, even informational messages.</span></span> <span data-ttu-id="dbba1-201">若使用 **-1**，則參數與設定之間不能有空格 ( **-m-1**而非 **-m -1**)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-201">If using **-1**, there must be no space between the parameter and the setting (**-m-1**, not **-m -1**).</span></span>  
  
 <span data-ttu-id="dbba1-202">**-r** { **0**| **1**}</span><span class="sxs-lookup"><span data-stu-id="dbba1-202">**-r** { **0**| **1**}</span></span>  
 <span data-ttu-id="dbba1-203">將訊息輸出重新導向至畫面 (**stderr**)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-203">Redirects message output to the screen (**stderr**).</span></span> <span data-ttu-id="dbba1-204">如果您沒有指定參數，或您指定 **0**，便只會重新導向嚴重性層級 11 或以上的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="dbba1-204">If you do not specify a parameter, or if you specify **0**, only error messages with a severity level 11 or higher are redirected.</span></span> <span data-ttu-id="dbba1-205">如果您指定 **1**，便會重新導向所有訊息輸出 (包括 "print")。</span><span class="sxs-lookup"><span data-stu-id="dbba1-205">If you specify **1**, all message output (including "print") is redirected.</span></span>  
  
 <span data-ttu-id="dbba1-206">**-i** _input_file_</span><span class="sxs-lookup"><span data-stu-id="dbba1-206">**-i** _input_file_</span></span>  
 <span data-ttu-id="dbba1-207">識別包含 SQL 陳述式或預存程序的批次之檔案。</span><span class="sxs-lookup"><span data-stu-id="dbba1-207">Identifies the file that contains a batch of SQL statements or stored procedures.</span></span> <span data-ttu-id="dbba1-208">小於 ( **\<** ) 比較運算子可用來代替 **-i**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-208">The less than (**\<**) comparison operator can be used in place of **-i**.</span></span>  
  
 <span data-ttu-id="dbba1-209">**-o** _output_file_</span><span class="sxs-lookup"><span data-stu-id="dbba1-209">**-o** _output_file_</span></span>  
 <span data-ttu-id="dbba1-210">識別用來接收 **osql**輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="dbba1-210">Identifies the file that receives output from **osql**.</span></span> <span data-ttu-id="dbba1-211">大於 ( **>** ) 比較運算子可用來代替 **-o**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-211">The greater than (**>**) comparison operator can be used in place of **-o**.</span></span>  
  
 <span data-ttu-id="dbba1-212">若 *input_file* 不是 Unicode 且未指定 **-u** ，則會以 OEM 格式儲存 *output_file* 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-212">If *input_file* is not Unicode and **-u** is not specified, *output_file* is stored in OEM format.</span></span> <span data-ttu-id="dbba1-213">若 *input_file* 是 Unicode 或指定 **-u** ，則會以 Unicode 格式儲存 *output_file* 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-213">If *input_file* is Unicode or **-u** is specified, *output_file* is stored in Unicode format.</span></span>  
  
 <span data-ttu-id="dbba1-214">**-p**</span><span class="sxs-lookup"><span data-stu-id="dbba1-214">**-p**</span></span>  
 <span data-ttu-id="dbba1-215">列印效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="dbba1-215">Prints performance statistics.</span></span>  
  
 <span data-ttu-id="dbba1-216">**-b**</span><span class="sxs-lookup"><span data-stu-id="dbba1-216">**-b**</span></span>  
 <span data-ttu-id="dbba1-217">指定在發生錯誤時， **osql** 會結束作業並傳回 DOS ERRORLEVEL 值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-217">Specifies that **osql** exits and returns a DOS ERRORLEVEL value when an error occurs.</span></span> <span data-ttu-id="dbba1-218">當 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 錯誤訊息的嚴重性層級大於或等於 11 時，傳回 DOS ERRORLEVEL 變數的值是 1；否則，傳回的值是 0。</span><span class="sxs-lookup"><span data-stu-id="dbba1-218">The value returned to the DOS ERRORLEVEL variable is 1 when the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] error message has a severity of 11 or greater; otherwise, the value returned is 0.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="dbba1-219">MS-DOS 批次檔可以測試 DOS ERRORLEVEL 的值，而且能夠適當處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbba1-219">MS-DOS batch files can test the value of DOS ERRORLEVEL and handle the error appropriately.</span></span>  
  
 <span data-ttu-id="dbba1-220">**-u**</span><span class="sxs-lookup"><span data-stu-id="dbba1-220">**-u**</span></span>  
 <span data-ttu-id="dbba1-221">指定無論 *input_file* 的格式為何， *output_file*均以 Unicode 格式儲存。</span><span class="sxs-lookup"><span data-stu-id="dbba1-221">Specifies that *output_file* is stored in Unicode format, regardless of the format of the *input_file*.</span></span>  
  
 <span data-ttu-id="dbba1-222">**-R**</span><span class="sxs-lookup"><span data-stu-id="dbba1-222">**-R**</span></span>  
 <span data-ttu-id="dbba1-223">指定在將貨幣、日期和時間資料轉換成字元資料時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 驅動程式要使用用戶端設定。</span><span class="sxs-lookup"><span data-stu-id="dbba1-223">Specifies that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver use client settings when converting currency, date, and time data to character data.</span></span>  
  
 <span data-ttu-id="dbba1-224">**-O**</span><span class="sxs-lookup"><span data-stu-id="dbba1-224">**-O**</span></span>  
 <span data-ttu-id="dbba1-225">指定停用某些 **osql** 功能，以符合舊版 **isql**的行為。</span><span class="sxs-lookup"><span data-stu-id="dbba1-225">Specifies that certain **osql** features be deactivated to match the behavior of earlier versions of **isql**.</span></span> <span data-ttu-id="dbba1-226">停用的功能如下：</span><span class="sxs-lookup"><span data-stu-id="dbba1-226">These features are deactivated:</span></span>  
  
-   <span data-ttu-id="dbba1-227">EOF 批次處理</span><span class="sxs-lookup"><span data-stu-id="dbba1-227">EOF batch processing</span></span>  
  
-   <span data-ttu-id="dbba1-228">自動調整主控台寬度</span><span class="sxs-lookup"><span data-stu-id="dbba1-228">Automatic console width scaling</span></span>  
  
-   <span data-ttu-id="dbba1-229">寬字訊息</span><span class="sxs-lookup"><span data-stu-id="dbba1-229">Wide messages</span></span>  
  
 <span data-ttu-id="dbba1-230">它也會將預設的 DOS ERRORLEVEL 值設為 -1。</span><span class="sxs-lookup"><span data-stu-id="dbba1-230">It also sets the default DOS ERRORLEVEL value to -1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-231">**osql**已不再支援 **-n** 、 **-O** 和 **-D**選項。</span><span class="sxs-lookup"><span data-stu-id="dbba1-231">The **-n**, **-O** and **-D** options are no longer supported by **osql**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbba1-232">備註</span><span class="sxs-lookup"><span data-stu-id="dbba1-232">Remarks</span></span>  
 <span data-ttu-id="dbba1-233">**osql** 公用程式會在已設定此處所列之區分大小寫選項的情況下，直接從作業系統中啟動。</span><span class="sxs-lookup"><span data-stu-id="dbba1-233">The **osql** utility is started directly from the operating system with the case-sensitive options listed here.</span></span> <span data-ttu-id="dbba1-234">啟動 **osql**後，其會接受 SQL 陳述式並以互動方式傳送至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dbba1-234">After **osql**starts, it accepts SQL statements and sends them to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] interactively.</span></span> <span data-ttu-id="dbba1-235">結果會格式化，顯示在畫面中 (**stdout**)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-235">The results are formatted and displayed on the screen (**stdout**).</span></span> <span data-ttu-id="dbba1-236">使用 QUIT 或 EXIT 來結束 **osql**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-236">Use QUIT or EXIT to exit from **osql**.</span></span>  
  
 <span data-ttu-id="dbba1-237">如果您在啟動**osql**時未指定使用者名稱，則會 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 檢查環境變數並使用它們，例如， \**osqluser = (*`user`*) **或**osqlserver = (*`server`\*) \*\*。</span><span class="sxs-lookup"><span data-stu-id="dbba1-237">If you do not specify a user name when you start **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] checks for the environment variables and uses those, for example, **osqluser=(*`user`*)** or **osqlserver=(*`server`*)**.</span></span> <span data-ttu-id="dbba1-238">如果未設定任何環境變數，就會使用工作站使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="dbba1-238">If no environment variables are set, the workstation user name is used.</span></span> <span data-ttu-id="dbba1-239">如果您沒有指定伺服器，就會使用工作站的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbba1-239">If you do not specify a server, the name of the workstation is used.</span></span>  
  
 <span data-ttu-id="dbba1-240">若 **-U** 或 **-P** 選項皆未使用，則 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會嘗試使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 驗證模式執行連接。</span><span class="sxs-lookup"><span data-stu-id="dbba1-240">If neither the **-U** or **-P** options are used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attempts to connect using [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication Mode.</span></span> <span data-ttu-id="dbba1-241">這項驗證是以執行 [!INCLUDE[msCoName](../includes/msconame-md.md)] osql **使用者的**Windows 帳戶為基礎。</span><span class="sxs-lookup"><span data-stu-id="dbba1-241">Authentication is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows account of the user running **osql**.</span></span>  
  
 <span data-ttu-id="dbba1-242">**osql** 公用程式會使用 ODBC API。</span><span class="sxs-lookup"><span data-stu-id="dbba1-242">The **osql** utility uses the ODBC API.</span></span> <span data-ttu-id="dbba1-243">這個公用程式使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO 連接選項的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC 驅動程式預設值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-243">The utility uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ODBC driver default settings for the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ISO connection options.</span></span> <span data-ttu-id="dbba1-244">如需詳細資訊，請參閱＜ANSI 選項的作用＞。</span><span class="sxs-lookup"><span data-stu-id="dbba1-244">For more information, see Effects of ANSI Options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-245">**osql** 公用程式不支援 CLR 使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="dbba1-245">The **osql** utility does not support CLR user-defined data types.</span></span> <span data-ttu-id="dbba1-246">若要處理這些資料類型，您必須使用 **sqlcmd** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-246">To process these data types, you must use the **sqlcmd** utility.</span></span> <span data-ttu-id="dbba1-247">如需詳細資訊，請參閱 [sqlcmd Utility](sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-247">For more information, see [sqlcmd Utility](sqlcmd-utility.md).</span></span>  
  
## <a name="osql-commands"></a><span data-ttu-id="dbba1-248">OSQL 命令</span><span class="sxs-lookup"><span data-stu-id="dbba1-248">OSQL Commands</span></span>  
 <span data-ttu-id="dbba1-249">除了 [!INCLUDE[tsql](../includes/tsql-md.md)] osql **內的**陳述式，您也可以使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="dbba1-249">In addition to [!INCLUDE[tsql](../includes/tsql-md.md)] statements within **osql**, these commands are also available.</span></span>  
  
|<span data-ttu-id="dbba1-250">Command</span><span class="sxs-lookup"><span data-stu-id="dbba1-250">Command</span></span>|<span data-ttu-id="dbba1-251">描述</span><span class="sxs-lookup"><span data-stu-id="dbba1-251">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbba1-252">GO</span><span class="sxs-lookup"><span data-stu-id="dbba1-252">GO</span></span>|<span data-ttu-id="dbba1-253">執行在上一個 GO 之後輸入的所有陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-253">Executes all statements entered after the last GO.</span></span>|  
|<span data-ttu-id="dbba1-254">RESET</span><span class="sxs-lookup"><span data-stu-id="dbba1-254">RESET</span></span>|<span data-ttu-id="dbba1-255">清除您已輸入的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-255">Clears any statements you have entered.</span></span>|  
|<span data-ttu-id="dbba1-256">QUIT 或 EXIT( )</span><span class="sxs-lookup"><span data-stu-id="dbba1-256">QUIT or EXIT( )</span></span>|<span data-ttu-id="dbba1-257">結束 **osql**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-257">Exits from **osql**.</span></span>|  
|<span data-ttu-id="dbba1-258">CTRL+C</span><span class="sxs-lookup"><span data-stu-id="dbba1-258">CTRL+C</span></span>|<span data-ttu-id="dbba1-259">結束查詢，但不結束 **osql**。</span><span class="sxs-lookup"><span data-stu-id="dbba1-259">Ends a query without exiting from **osql**.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-260">!!</span><span class="sxs-lookup"><span data-stu-id="dbba1-260">The !!</span></span> <span data-ttu-id="dbba1-261">和 ED 命令不再受到 **osql**支援。</span><span class="sxs-lookup"><span data-stu-id="dbba1-261">and ED commands are no longer supported by **osql**.</span></span>  
  
 <span data-ttu-id="dbba1-262">命令結束字元 GO (預設)、RESET EXIT、QUIT 和 CTRL+C 必須在行首並緊接在 **osql** 提示之後，才能夠辨識。</span><span class="sxs-lookup"><span data-stu-id="dbba1-262">The command terminators GO (by default), RESET EXIT, QUIT, and CTRL+C, are recognized only if they appear at the beginning of a line, immediately following the **osql** prompt.</span></span>  
  
 <span data-ttu-id="dbba1-263">GO 會發出批次結束及執行任何快取的 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式的信號。</span><span class="sxs-lookup"><span data-stu-id="dbba1-263">GO signals both the end of a batch and the execution of any cached [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="dbba1-264">您在每個輸入行結束而按下 ENTER 時， **osql** 會快取這一行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-264">When you press ENTER at the end of each input line, **osql** caches the statements on that line.</span></span> <span data-ttu-id="dbba1-265">當您在輸入 GO 之後按下 ENTER 鍵時，會將目前所快取的所有陳述式做為單一批次傳給 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dbba1-265">When you press ENTER after typing GO, all of the currently cached statements are sent as a batch to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="dbba1-266">目前 **osql** 公用程式的運作方式，如同在任何執行的指令碼尾端有隱含的 GO，因此會執行指令碼中的所有陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-266">The current **osql** utility works as if there is an implied GO at the end of any script executed, therefore all statements in the script execute.</span></span>  
  
 <span data-ttu-id="dbba1-267">請在行首輸入命令結束字元來結束命令。</span><span class="sxs-lookup"><span data-stu-id="dbba1-267">End a command by typing a line beginning with a command terminator.</span></span> <span data-ttu-id="dbba1-268">您可以在命令結束字元之後，輸入一個整數來指定命令應該執行的次數。</span><span class="sxs-lookup"><span data-stu-id="dbba1-268">You can follow the command terminator with an integer to specify how many times the command should be run.</span></span> <span data-ttu-id="dbba1-269">例如，若要執行這個命令 100 次，請輸入：</span><span class="sxs-lookup"><span data-stu-id="dbba1-269">For example, to execute this command 100 times, type:</span></span>  
  
```  
SELECT x = 1  
GO 100  
```  
  
 <span data-ttu-id="dbba1-270">執行結束時，會列印結果一次。</span><span class="sxs-lookup"><span data-stu-id="dbba1-270">The results are printed once at the end of execution.</span></span> <span data-ttu-id="dbba1-271">**osql** 不接受每行超出 1,000 個字元。</span><span class="sxs-lookup"><span data-stu-id="dbba1-271">**osql** does not accept more than 1,000 characters per line.</span></span> <span data-ttu-id="dbba1-272">大型陳述式應該分成幾行。</span><span class="sxs-lookup"><span data-stu-id="dbba1-272">Large statements should be spread across multiple lines.</span></span>  
  
 <span data-ttu-id="dbba1-273">Windows 的命令重新呼叫功能可用來重新呼叫及修改 **osql** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dbba1-273">The command recall facilities of Windows can be used to recall and modify **osql** statements.</span></span> <span data-ttu-id="dbba1-274">您可以輸入 RESET 來清除現有的查詢緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dbba1-274">The existing query buffer can be cleared by typing RESET.</span></span>  
  
 <span data-ttu-id="dbba1-275">執行預存程序時， **osql** 會在批次的各組結果之間，列印一空白行。</span><span class="sxs-lookup"><span data-stu-id="dbba1-275">When running stored procedures, **osql** prints a blank line between each set of results in a batch.</span></span> <span data-ttu-id="dbba1-276">另外，當「0 個資料列受影響」的訊息不適合執行的陳述式時，便不會出現這則訊息。</span><span class="sxs-lookup"><span data-stu-id="dbba1-276">In addition, the "0 rows affected" message does not appear when it does not apply to the statement executed.</span></span>  
  
## <a name="using-osql-interactively"></a><span data-ttu-id="dbba1-277">以互動方式使用 osql</span><span class="sxs-lookup"><span data-stu-id="dbba1-277">Using osql Interactively</span></span>  
 <span data-ttu-id="dbba1-278">若要以互動方式來使用 **osql** ，請在命令提示字元之下，輸入 **osql** 命令 (及任何選項)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-278">To use **osql** interactively, type the **osql** command (and any of the options) at a command prompt.</span></span>  
  
 <span data-ttu-id="dbba1-279">您可以輸入類似下列的命令來讀取包含查詢 (如 Stores.qry) 的檔案，供 **osql** 執行：</span><span class="sxs-lookup"><span data-stu-id="dbba1-279">You can read in a file containing a query (such as Stores.qry) for execution by **osql** by typing a command similar to this:</span></span>  
  
```  
osql -E -i stores.qry  
```  
  
 <span data-ttu-id="dbba1-280">您可以輸入類似下列中的命令來讀取包含查詢 (如 Titles.qry) 的檔案，以及將結果導向另一個檔案：</span><span class="sxs-lookup"><span data-stu-id="dbba1-280">You can read in a file containing a query (such as Titles.qry) and direct the results to another file by typing a command similar to this:</span></span>  
  
```  
osql -E -i titles.qry -o titles.res  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dbba1-281">可能的話，請使用 **-E**選項 (信任連接)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-281">When possible, use the **-E**option (trusted connection).</span></span>  
  
 <span data-ttu-id="dbba1-282">以互動方式使用**osql**時，您可以使用 **： r**_file_name_，將作業系統檔案讀入命令緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="dbba1-282">When using **osql** interactively, you can read an operating-system file into the command buffer with **:r**_file_name_.</span></span> <span data-ttu-id="dbba1-283">這會將 *file_name* 中的 SQL 指令碼當作單一批次直接傳給伺服器。</span><span class="sxs-lookup"><span data-stu-id="dbba1-283">This sends the SQL script in *file_name* directly to the server as a single batch.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-284">當使用 **osql**時，如果批次分隔字元 GO 出現在 SQL 指令碼檔案中， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 會將其視為語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbba1-284">When using **osql**, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] treats the batch separator GO, if it appears in a SQL script file, as a syntax error.</span></span>  
  
## <a name="inserting-comments"></a><span data-ttu-id="dbba1-285">插入註解</span><span class="sxs-lookup"><span data-stu-id="dbba1-285">Inserting Comments</span></span>  
 <span data-ttu-id="dbba1-286">您可以在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] osql **提交給**的 Transact-SQL 陳述式中併入註解。</span><span class="sxs-lookup"><span data-stu-id="dbba1-286">You can include comments in a Transact-SQL statement submitted to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by **osql**.</span></span> <span data-ttu-id="dbba1-287">可用的註解樣式有兩種：-- 和 /\*...\*/。</span><span class="sxs-lookup"><span data-stu-id="dbba1-287">Two types of commenting styles are allowed: -- and /\*...\*/.</span></span>  
  
## <a name="using-exit-to-return-results-in-osql"></a><span data-ttu-id="dbba1-288">在 osql 中利用 EXIT 傳回結果</span><span class="sxs-lookup"><span data-stu-id="dbba1-288">Using EXIT to Return Results in osql</span></span>  
 <span data-ttu-id="dbba1-289">您可以利用 SELECT 陳述式的結果來做為 **osql**的傳回值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-289">You can use the result of a SELECT statement as the return value from **osql**.</span></span> <span data-ttu-id="dbba1-290">如果為數值，則最後一個結果資料列的最後一個資料行會轉換成 4 位元組的整數 (long)。</span><span class="sxs-lookup"><span data-stu-id="dbba1-290">If it is numeric, the last column of the last result row is converted to a 4-byte integer (long).</span></span> <span data-ttu-id="dbba1-291">MS-DOS 會將低位元組傳給父處理序或作業系統錯誤層級。</span><span class="sxs-lookup"><span data-stu-id="dbba1-291">MS-DOS passes the low byte to the parent process or operating system error level.</span></span> <span data-ttu-id="dbba1-292">Windows 會傳遞整個 4 位元組整數。</span><span class="sxs-lookup"><span data-stu-id="dbba1-292">Windows passes the entire 4-byte integer.</span></span> <span data-ttu-id="dbba1-293">語法為：</span><span class="sxs-lookup"><span data-stu-id="dbba1-293">The syntax is:</span></span>  
  
```  
EXIT ( < query > )  
```  
  
 <span data-ttu-id="dbba1-294">例如：</span><span class="sxs-lookup"><span data-stu-id="dbba1-294">For example:</span></span>  
  
```  
EXIT(SELECT @@ROWCOUNT)  
```  
  
 <span data-ttu-id="dbba1-295">您也可以將 EXIT 參數併入批次檔中。</span><span class="sxs-lookup"><span data-stu-id="dbba1-295">You can also include the EXIT parameter as part of a batch file.</span></span> <span data-ttu-id="dbba1-296">例如：</span><span class="sxs-lookup"><span data-stu-id="dbba1-296">For example:</span></span>  
  
```  
osql -E -Q "EXIT(SELECT COUNT(*) FROM '%1')"  
```  
  
 <span data-ttu-id="dbba1-297">**osql** 公用程式會將 **()** 括號之間的任何內容，完全照原本輸入的內容傳給伺服器。</span><span class="sxs-lookup"><span data-stu-id="dbba1-297">The **osql** utility passes everything between the parentheses **()** to the server exactly as entered.</span></span> <span data-ttu-id="dbba1-298">如果預存的系統程序選取某一組，傳回某個值，此時只會傳回選取的項目。</span><span class="sxs-lookup"><span data-stu-id="dbba1-298">If a stored system procedure selects a set and returns a value, only the selection is returned.</span></span> <span data-ttu-id="dbba1-299">括號之間沒有任何內容的 EXIT **()** 陳述式，會執行批次中在它前面的任何內容，之後，便結束作業，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-299">The EXIT **()** statement with nothing between the parentheses executes everything preceding it in the batch and then exits with no return value.</span></span>  
  
 <span data-ttu-id="dbba1-300">EXIT 有四種格式：</span><span class="sxs-lookup"><span data-stu-id="dbba1-300">There are four EXIT formats:</span></span>  
  
-   <span data-ttu-id="dbba1-301">EXIT</span><span class="sxs-lookup"><span data-stu-id="dbba1-301">EXIT</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-302">不執行批次；立即結束，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-302">Does not execute the batch; quits immediately and returns no value.</span></span>  
  
-   <span data-ttu-id="dbba1-303">EXIT **()**</span><span class="sxs-lookup"><span data-stu-id="dbba1-303">EXIT **()**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-304">執行批次之後，便結束作業，不傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-304">Executes the batch, and then quits and returns no value.</span></span>  
  
-   <span data-ttu-id="dbba1-305">結束\*\* (*`query`*) \*\*</span><span class="sxs-lookup"><span data-stu-id="dbba1-305">EXIT **(*`query`*)**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-306">執行包含查詢的批次，傳回查詢結果之後，便告結束。</span><span class="sxs-lookup"><span data-stu-id="dbba1-306">Executes the batch, including the query, and then quits after returning the results of the query.</span></span>  
  
-   <span data-ttu-id="dbba1-307">狀態為 127 的 RAISERROR</span><span class="sxs-lookup"><span data-stu-id="dbba1-307">RAISERROR with a state of 127</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dbba1-308">若在 **osql** 指令碼內使用 RAISERROR，且產生 127 狀態，則 **osql** 會結束作業，且會將訊息識別碼傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="dbba1-308">If RAISERROR is used within an **osql** script and a state of 127 is raised, **osql** will quit and return the message ID back to the client.</span></span> <span data-ttu-id="dbba1-309">例如：</span><span class="sxs-lookup"><span data-stu-id="dbba1-309">For example:</span></span>  
  
```  
RAISERROR(50001, 10, 127)  
```  
  
 <span data-ttu-id="dbba1-310">此錯誤會使得 **osql** 指令碼結束作業，並將訊息識別碼 50001 傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="dbba1-310">This error will cause the **osql** script to end and the message ID 50001 will be returned to the client.</span></span>  
  
 <span data-ttu-id="dbba1-311">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]保留傳回值 -1 至 -99； **osql** 定義了下列值：</span><span class="sxs-lookup"><span data-stu-id="dbba1-311">The return values -1 to -99 are reserved by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]; **osql** defines these values:</span></span>  
  
-   <span data-ttu-id="dbba1-312">-100</span><span class="sxs-lookup"><span data-stu-id="dbba1-312">-100</span></span>  
  
     <span data-ttu-id="dbba1-313">在選取傳回值之前發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbba1-313">Error encountered prior to selecting return value.</span></span>  
  
-   <span data-ttu-id="dbba1-314">-101</span><span class="sxs-lookup"><span data-stu-id="dbba1-314">-101</span></span>  
  
     <span data-ttu-id="dbba1-315">在選取傳回值時，找不到任何資料列。</span><span class="sxs-lookup"><span data-stu-id="dbba1-315">No rows found when selecting return value.</span></span>  
  
-   <span data-ttu-id="dbba1-316">-102</span><span class="sxs-lookup"><span data-stu-id="dbba1-316">-102</span></span>  
  
     <span data-ttu-id="dbba1-317">在選取傳回值時，發生轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbba1-317">Conversion error occurred when selecting return value.</span></span>  
  
## <a name="displaying-money-and-smallmoney-data-types"></a><span data-ttu-id="dbba1-318">顯示 money 和 smallmoney 資料類型</span><span class="sxs-lookup"><span data-stu-id="dbba1-318">Displaying money and smallmoney Data Types</span></span>  
 <span data-ttu-id="dbba1-319">**osql**會顯示 `money` `smallmoney` 兩個小數位數的和資料類型，不過，會 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在內部使用四個小數位數來儲存值。</span><span class="sxs-lookup"><span data-stu-id="dbba1-319">**osql** displays the `money` and `smallmoney` data types with two decimal places although [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stores the value internally with four decimal places.</span></span> <span data-ttu-id="dbba1-320">請設想下列範例：</span><span class="sxs-lookup"><span data-stu-id="dbba1-320">Consider the example:</span></span>  
  
```  
SELECT CAST(CAST(10.3496 AS money) AS decimal(6, 4))  
GO  
```  
  
 <span data-ttu-id="dbba1-321">這個陳述式會產生 `10.3496`的結果，這表示在儲存值時，所有小數點保留不動。</span><span class="sxs-lookup"><span data-stu-id="dbba1-321">This statement produces a result of `10.3496`, which indicates that the value is stored with all decimal places intact.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbba1-322">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbba1-322">See Also</span></span>  
 <span data-ttu-id="dbba1-323">[註解 &#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="dbba1-323">[Comment &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="dbba1-324">[-- &#40;註解&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span><span class="sxs-lookup"><span data-stu-id="dbba1-324">[-- &#40;Comment&#41; &#40;MDX&#41;](/sql/mdx/comment-mdx) </span></span>  
 <span data-ttu-id="dbba1-325">[CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dbba1-325">[CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql) </span></span>  
 [<span data-ttu-id="dbba1-326">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dbba1-326">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
