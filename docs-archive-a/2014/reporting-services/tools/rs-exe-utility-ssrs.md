---
title: RS.exe 公用程式 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bcf21a1bf2453d2bd1f0644e31ca46f3f94e6884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704825"
---
# <a name="rsexe-utility-ssrs"></a><span data-ttu-id="5f778-102">RS.exe Utility (SSRS)</span><span class="sxs-lookup"><span data-stu-id="5f778-102">RS.exe Utility (SSRS)</span></span>
  <span data-ttu-id="5f778-103">rs.exe 公用程式會處理您在輸入檔中所提供的指令碼。</span><span class="sxs-lookup"><span data-stu-id="5f778-103">The rs.exe utility processes script that you provide in an input file.</span></span> <span data-ttu-id="5f778-104">使用此公用程式可自動化報表伺服器部署和管理工作。</span><span class="sxs-lookup"><span data-stu-id="5f778-104">Use this utility to automate report server deployment and administration tasks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5f778-105">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]開始，可支援 **rs** 公用程式，運作於設定 SharePoint 整合模式的報表伺服器以及以原生模式設定的伺服器中。</span><span class="sxs-lookup"><span data-stu-id="5f778-105">Beginning with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], the **rs** utility is supported against report servers that are configured for SharePoint integrated mode as well as servers configured in native mode.</span></span> <span data-ttu-id="5f778-106">之前舊版只支援原生模式設定。</span><span class="sxs-lookup"><span data-stu-id="5f778-106">Previous versions only supported native mode configurations.</span></span>  
  
 <span data-ttu-id="5f778-107">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="5f778-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="5f778-108">檔案位置</span><span class="sxs-lookup"><span data-stu-id="5f778-108">File Location</span></span>](#bkmk_filelocation)  
  
-   [<span data-ttu-id="5f778-109">引數</span><span class="sxs-lookup"><span data-stu-id="5f778-109">Arguments</span></span>](#bkmk_arguments)  
  
-   [<span data-ttu-id="5f778-110">權限</span><span class="sxs-lookup"><span data-stu-id="5f778-110">Permissions</span></span>](#bkmk_permissions)  
  
-   [<span data-ttu-id="5f778-111">範例</span><span class="sxs-lookup"><span data-stu-id="5f778-111">Examples</span></span>](#bkmk_examples)  
  
## <a name="syntax"></a><span data-ttu-id="5f778-112">語法</span><span class="sxs-lookup"><span data-stu-id="5f778-112">Syntax</span></span>  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> <span data-ttu-id="5f778-113">檔案位置</span><span class="sxs-lookup"><span data-stu-id="5f778-113">File Location</span></span>  
 <span data-ttu-id="5f778-114">**RS.exe** 位在 **\Program Files\Microsoft SQL Server\110\Tools\Binn**。</span><span class="sxs-lookup"><span data-stu-id="5f778-114">**RS.exe** is located at **\Program Files\Microsoft SQL Server\110\Tools\Binn**.</span></span> <span data-ttu-id="5f778-115">您可以從檔案系統上的任何資料夾執行此公用程式。</span><span class="sxs-lookup"><span data-stu-id="5f778-115">You can run the utility from any folder on your file system.</span></span>  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a> <span data-ttu-id="5f778-116">引數</span><span class="sxs-lookup"><span data-stu-id="5f778-116">Arguments</span></span>  
 <span data-ttu-id="5f778-117">**-?**</span><span class="sxs-lookup"><span data-stu-id="5f778-117">**-?**</span></span>  
 <span data-ttu-id="5f778-118">(選擇性) 顯示 **rs** 引數的語法。</span><span class="sxs-lookup"><span data-stu-id="5f778-118">(Optional) Displays the syntax of **rs** arguments.</span></span>  
  
 <span data-ttu-id="5f778-119">`-i`*input_file*</span><span class="sxs-lookup"><span data-stu-id="5f778-119">`-i` *input_file*</span></span>  
 <span data-ttu-id="5f778-120">(必要) 指定要執行的 .rss 檔案。</span><span class="sxs-lookup"><span data-stu-id="5f778-120">(Required) Specifies the .rss file to execute.</span></span> <span data-ttu-id="5f778-121">這個值可以是 .rss 檔案的相對路徑或完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5f778-121">This value can be a relative or fully qualified path to the .rss file.</span></span>  
  
 <span data-ttu-id="5f778-122">`-s`*serverURL*</span><span class="sxs-lookup"><span data-stu-id="5f778-122">`-s` *serverURL*</span></span>  
 <span data-ttu-id="5f778-123">(必要) 指定要對其執行檔案的 Web 伺服器名稱和報表伺服器虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="5f778-123">(Required) Specifies the Web server name and report server virtual directory name to execute the file against.</span></span> <span data-ttu-id="5f778-124">報表伺服器 URL 的範例為 `http://examplewebserver/reportserver`。</span><span class="sxs-lookup"><span data-stu-id="5f778-124">An example of a report server URL is `http://examplewebserver/reportserver`.</span></span> <span data-ttu-id="5f778-125">伺服器名稱開頭的前置詞 http:// 或 https:// 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5f778-125">The prefix http:// or https:// at the beginning of the server name is optional.</span></span> <span data-ttu-id="5f778-126">如果您省略前置詞，報表伺服器 Script Host 會先嘗試使用 https，而且如果 https 無法運作，則會使用 http。</span><span class="sxs-lookup"><span data-stu-id="5f778-126">If you omit the prefix, the report server script host tries to use https first, and then uses http if https does not work.</span></span>  
  
 <span data-ttu-id="5f778-127">`-u`[*網域* \\ ]使用者*名稱*</span><span class="sxs-lookup"><span data-stu-id="5f778-127">`-u` [*domain*\\]*username*</span></span>  
 <span data-ttu-id="5f778-128">(選擇性) 指定用來連接到報表伺服器的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f778-128">(Optional) Specifies a user account used to connect to the report server.</span></span> <span data-ttu-id="5f778-129">如果省略 `-u` 和 `-p`，則會使用目前的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5f778-129">If `-u` and `-p` are omitted, the current Windows user account is used.</span></span>  
  
 <span data-ttu-id="5f778-130">`-p`*密碼*</span><span class="sxs-lookup"><span data-stu-id="5f778-130">`-p` *password*</span></span>  
 <span data-ttu-id="5f778-131">(如果已指定 `-u` 則是必要的) 指定要與 `-u` 引數一起使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="5f778-131">(Required if `-u` is specified) Specifies the password to use with the `-u` argument.</span></span> <span data-ttu-id="5f778-132">此值區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5f778-132">This value is case-sensitive.</span></span>  
  
 `-e`  
 <span data-ttu-id="5f778-133">(選擇性) 指定要在其上執行指令碼的 SOAP 結束點。</span><span class="sxs-lookup"><span data-stu-id="5f778-133">(Optional) Specifies the SOAP endpoint against which the script should run.</span></span> <span data-ttu-id="5f778-134">有效的值如下：</span><span class="sxs-lookup"><span data-stu-id="5f778-134">Valid values are the following:</span></span>  
  
-   <span data-ttu-id="5f778-135">Mgmt2010</span><span class="sxs-lookup"><span data-stu-id="5f778-135">Mgmt2010</span></span>  
  
-   <span data-ttu-id="5f778-136">Mgmt2006</span><span class="sxs-lookup"><span data-stu-id="5f778-136">Mgmt2006</span></span>  
  
-   <span data-ttu-id="5f778-137">Mgmt2005</span><span class="sxs-lookup"><span data-stu-id="5f778-137">Mgmt2005</span></span>  
  
-   <span data-ttu-id="5f778-138">Exec2005</span><span class="sxs-lookup"><span data-stu-id="5f778-138">Exec2005</span></span>  
  
 <span data-ttu-id="5f778-139">如果未指定值，則會使用 Mgmt2005 端點。</span><span class="sxs-lookup"><span data-stu-id="5f778-139">If a value is not specified, the Mgmt2005 endpoint is used.</span></span> <span data-ttu-id="5f778-140">如需有關 SOAP 端點的詳細資訊，請參閱＜ [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f778-140">For more information about the SOAP endpoints, see [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).</span></span>  
  
 <span data-ttu-id="5f778-141">`-l`*time_out*</span><span class="sxs-lookup"><span data-stu-id="5f778-141">`-l` *time_out*</span></span>  
 <span data-ttu-id="5f778-142"> (選擇性) 指定連接到伺服器超時之前經過的秒數。預設值為60秒。</span><span class="sxs-lookup"><span data-stu-id="5f778-142">(Optional) Specifies the number of seconds that elapse before the connection to the server times out. The default is 60 seconds.</span></span> <span data-ttu-id="5f778-143">若未指定逾時值，則使用預設值。</span><span class="sxs-lookup"><span data-stu-id="5f778-143">If you do not specify a time-out value, the default is used.</span></span> <span data-ttu-id="5f778-144">`0` 的值指定連接永不逾時。</span><span class="sxs-lookup"><span data-stu-id="5f778-144">A value of `0` specifies that the connection never times out.</span></span>  
  
 <span data-ttu-id="5f778-145">**-b**</span><span class="sxs-lookup"><span data-stu-id="5f778-145">**-b**</span></span>  
 <span data-ttu-id="5f778-146">(選擇性) 指定以批次方式執行指令碼檔案中的命令。</span><span class="sxs-lookup"><span data-stu-id="5f778-146">(Optional) Specifies that the commands in the script file run in a batch.</span></span> <span data-ttu-id="5f778-147">若有任何命令失敗，便會回復此批次。</span><span class="sxs-lookup"><span data-stu-id="5f778-147">If any commands fail, the batch is rolled back.</span></span> <span data-ttu-id="5f778-148">有些命令無法批次處理，而會依平常方式執行。</span><span class="sxs-lookup"><span data-stu-id="5f778-148">Some commands cannot be batched, and those run as usual.</span></span> <span data-ttu-id="5f778-149">只有在指令碼中發生未處理的例外狀況會導致批次復原。</span><span class="sxs-lookup"><span data-stu-id="5f778-149">Only exceptions that are thrown and are not handled within the script result in a rollback.</span></span> <span data-ttu-id="5f778-150">如果指令碼處理例外狀況並從 `Main` 正常地傳回，則會認可該批次。</span><span class="sxs-lookup"><span data-stu-id="5f778-150">If the script handles an exception and returns normally from `Main`, the batch is committed.</span></span> <span data-ttu-id="5f778-151">如果忽略此參數，則會執行此命令而不會建立批次。</span><span class="sxs-lookup"><span data-stu-id="5f778-151">If you omit this parameter, the commands run without creating a batch.</span></span> <span data-ttu-id="5f778-152">如需詳細資訊，請參閱 [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="5f778-152">For more information, see [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).</span></span>  
  
 <span data-ttu-id="5f778-153">`-v`*expr.globalvar*</span><span class="sxs-lookup"><span data-stu-id="5f778-153">`-v` *globalvar*</span></span>  
 <span data-ttu-id="5f778-154">(選擇性) 指定在指令碼中使用的全域變數。</span><span class="sxs-lookup"><span data-stu-id="5f778-154">(Optional) Specifies global variables that are used in the script.</span></span> <span data-ttu-id="5f778-155">如果指令碼使用全域變數，則必須指定此引數。</span><span class="sxs-lookup"><span data-stu-id="5f778-155">If the script uses global variables, you must specify this argument.</span></span> <span data-ttu-id="5f778-156">指定的值必須是 .rss 檔案中所定義的全域變數之有效值。</span><span class="sxs-lookup"><span data-stu-id="5f778-156">The value that you specify must be valid for global variable defined in the .rss file.</span></span> <span data-ttu-id="5f778-157">您必須為每個 **-v**引數指定一個全域變數。</span><span class="sxs-lookup"><span data-stu-id="5f778-157">You must specify one global variable for each **-v** argument.</span></span>  
  
 <span data-ttu-id="5f778-158">會在命令列上指定 `-v` 引數，以及用於設定在執行階段定義於指令碼中的全域變數值。</span><span class="sxs-lookup"><span data-stu-id="5f778-158">The `-v` argument is specified on the command line and is used to set the value for a global variable that is defined in your script at run time.</span></span> <span data-ttu-id="5f778-159">例如，如果您的指令碼包含名為 *parentFolder*的變數，您就可以在命令列上指定該資料夾的名稱：</span><span class="sxs-lookup"><span data-stu-id="5f778-159">For example, if your script contains a variable named *parentFolder*, you can specify a name for that folder on the command line:</span></span>  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 <span data-ttu-id="5f778-160">全域變數會使用給定的名稱來建立並設定為所提供的值。</span><span class="sxs-lookup"><span data-stu-id="5f778-160">Global variables are created with the names given and set to the values supplied.</span></span> <span data-ttu-id="5f778-161">例如， **-v a =**" `1` " **-v b =**"" 會 `2` 產生名為的變數，其值為 `a` " `1` "，而變數**b**的值為 " `2` "。</span><span class="sxs-lookup"><span data-stu-id="5f778-161">For example, **-v a=**"`1`" **-v b=**"`2`" results in a variable named `a` with a value of"`1`" and a variable **b** with a value of "`2`".</span></span>  
  
 <span data-ttu-id="5f778-162">指令碼中的任何函數均可使用全域變數。</span><span class="sxs-lookup"><span data-stu-id="5f778-162">Global variables are available to any function in the script.</span></span> <span data-ttu-id="5f778-163">反斜線和引號 (「 \*\* \\ \*\*) 會被視為雙引號。</span><span class="sxs-lookup"><span data-stu-id="5f778-163">A backslash and quotation mark (**\\"**) is interpreted as a double quotation mark.</span></span> <span data-ttu-id="5f778-164">只有當字串含有空格時才需要引號。</span><span class="sxs-lookup"><span data-stu-id="5f778-164">The quotation marks are required only if the string contains a space.</span></span> <span data-ttu-id="5f778-165">變數名稱必須是有效的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ; 它們必須以字母字元或底線開頭，而且包含字母字元、數位或底線。</span><span class="sxs-lookup"><span data-stu-id="5f778-165">Variable names must be valid for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]; they must start with alphabetical character or underscore and contain alphabetical characters, digits, or underscores.</span></span> <span data-ttu-id="5f778-166">保留字不可以當做變數名稱使用。</span><span class="sxs-lookup"><span data-stu-id="5f778-166">Reserved words cannot be used as variable names.</span></span> <span data-ttu-id="5f778-167">如需使用全域變數的詳細資訊，請參閱[運算式中的內建集合 &#40;報表產生器及 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="5f778-167">For more information about using global variables, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
 <span data-ttu-id="5f778-168">**-t**</span><span class="sxs-lookup"><span data-stu-id="5f778-168">**-t**</span></span>  
 <span data-ttu-id="5f778-169">(選擇性) 追蹤記錄的輸出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5f778-169">(Optional) Outputs error messages to the trace log.</span></span> <span data-ttu-id="5f778-170">此引數沒有取得值。</span><span class="sxs-lookup"><span data-stu-id="5f778-170">This argument does not take a value.</span></span> <span data-ttu-id="5f778-171">如需詳細資訊，請參閱 [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md)。</span><span class="sxs-lookup"><span data-stu-id="5f778-171">For more information, see [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).</span></span>  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> <span data-ttu-id="5f778-172">權限</span><span class="sxs-lookup"><span data-stu-id="5f778-172">Permissions</span></span>  
 <span data-ttu-id="5f778-173">若要執行工具，您必須有足夠的權限，可以連接到要對其執行指令碼的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f778-173">To run the tool, you must have permission to connect to the report server instance you are running the script against.</span></span> <span data-ttu-id="5f778-174">您可以執行指令碼在本機電腦或遠端電腦執行變更。</span><span class="sxs-lookup"><span data-stu-id="5f778-174">You can run scripts to make changes to the local computer or a remote computer.</span></span> <span data-ttu-id="5f778-175">若要對安裝在遠端電腦上的報表伺服器執行變更，請在 `-s` 引數中指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="5f778-175">To make changes to a report server installed on a remote computer, specify the remote computer in the `-s` argument.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="5f778-176">範例</span><span class="sxs-lookup"><span data-stu-id="5f778-176">Examples</span></span>  
 <span data-ttu-id="5f778-177">下列範例說明如何指定指令碼檔案，其中包含您要執行的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 指令碼和 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="5f778-177">The following example illustrates how to specify the script file that contains [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET script and Web service methods that you want to execute.</span></span>  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
 <span data-ttu-id="5f778-178"> 如需詳細的範例，請參閱＜ [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f778-178">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="5f778-179">如需其他範例，請參閱 [執行 Reporting Services 指令碼檔案](run-a-reporting-services-script-file.md)</span><span class="sxs-lookup"><span data-stu-id="5f778-179">For additional examples, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f778-180">備註</span><span class="sxs-lookup"><span data-stu-id="5f778-180">Remarks</span></span>  
 <span data-ttu-id="5f778-181">您可以定義指令碼來設定系統屬性、發行報表等等。</span><span class="sxs-lookup"><span data-stu-id="5f778-181">You can define scripts to set system properties, publish reports, and so forth.</span></span> <span data-ttu-id="5f778-182">您可以建立的指令碼包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API 的任何方法。</span><span class="sxs-lookup"><span data-stu-id="5f778-182">The scripts that you create can include any methods of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API.</span></span> <span data-ttu-id="5f778-183">如需有關可供您使用的方法和屬性之詳細資訊，請參閱＜ [Report Server Web Service](../report-server-web-service/report-server-web-service.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f778-183">For more information about the methods and properties available to you, see [Report Server Web Service](../report-server-web-service/report-server-web-service.md).</span></span>  
  
 <span data-ttu-id="5f778-184">指令碼必須以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET 程式碼撰寫，然後使用 .rss 副檔名將指令碼儲存在 Unicode 或 UTF-8 文字檔中。</span><span class="sxs-lookup"><span data-stu-id="5f778-184">The script must be written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET code, and stored in a Unicode or UTF-8 text file with an .rss file name extension.</span></span> <span data-ttu-id="5f778-185">您不可以使用 **rs** 公用程式來偵錯指令碼。</span><span class="sxs-lookup"><span data-stu-id="5f778-185">You cannot debug scripts with the **rs** utility.</span></span> <span data-ttu-id="5f778-186">若要對腳本進行偵錯工具，請在中執行程式碼 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5f778-186">To debug a script, run the code within [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="5f778-187"> 如需詳細的範例，請參閱＜ [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5f778-187">For a detailed example, see [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f778-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f778-188">See Also</span></span>  
 <span data-ttu-id="5f778-189">[執行 Reporting Services 指令檔](run-a-reporting-services-script-file.md) </span><span class="sxs-lookup"><span data-stu-id="5f778-189">[Run a Reporting Services Script File](run-a-reporting-services-script-file.md) </span></span>  
 <span data-ttu-id="5f778-190">[編寫部署和管理工作的腳本](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="5f778-190">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="5f778-191">[使用 rs.exe 公用程式與 Web 服務編寫腳本](script-with-the-rs-exe-utility-and-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="5f778-191">[Script with the rs.exe Utility and the Web Service](script-with-the-rs-exe-utility-and-the-web-service.md) </span></span>  
 [<span data-ttu-id="5f778-192">報表伺服器命令提示字元公用程式 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5f778-192">Report Server Command Prompt Utilities &#40;SSRS&#41;</span></span>](report-server-command-prompt-utilities-ssrs.md)  
  
  
