---
title: Profiler 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], profiler90 utility
- profiler90 utility
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: e91c30a9-0d29-4f84-bcb8-e8fb62afadda
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8df3e8557bb52839d17291bae0c5ba507d0a671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686611"
---
# <a name="profiler-utility"></a><span data-ttu-id="7503b-102">Profiler 公用程式</span><span class="sxs-lookup"><span data-stu-id="7503b-102">Profiler Utility</span></span>
  <span data-ttu-id="7503b-103">**profiler** 公用程式會啟動 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 工具。</span><span class="sxs-lookup"><span data-stu-id="7503b-103">The **profiler** utility launches the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tool.</span></span> <span data-ttu-id="7503b-104">這個主題稍後列出的選擇性引數可讓您控制應用程式啟動的方式。</span><span class="sxs-lookup"><span data-stu-id="7503b-104">The optional arguments listed later in this topic allow you to control how the application starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7503b-105">**profiler** 公用程式的用途不在於編寫追蹤的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7503b-105">The **profiler** utility is not intended for scripting traces.</span></span> <span data-ttu-id="7503b-106">如需詳細資訊，請參閱 [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="7503b-106">For more information, see [SQL Server Profiler](sql-server-profiler/sql-server-profiler.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7503b-107">語法</span><span class="sxs-lookup"><span data-stu-id="7503b-107">Syntax</span></span>  
  
```  
  
      profiler  
          [ /? ] |  
[  
{  
{ /U login_id [ /P password ] }  
| /E  
}  
{[ /S sql_server_name ] | [ /A analysis_services_server_name ] }  
[ /D database ]  
[ /T "template_name" ]  
[ /B { "trace_table_name" } ]  
{ [/F "filename" ] | [ /O "filename" ] }  
[ /L locale_ID ]  
[ /M "MM-DD-YY hh:mm:ss" ]  
[ /R ]  
[ /Z file_size ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7503b-108">引數</span><span class="sxs-lookup"><span data-stu-id="7503b-108">Arguments</span></span>  
 <span data-ttu-id="7503b-109">**/?**</span><span class="sxs-lookup"><span data-stu-id="7503b-109">**/?**</span></span>  
 <span data-ttu-id="7503b-110">顯示 **profiler** 引數的語法摘要。</span><span class="sxs-lookup"><span data-stu-id="7503b-110">Displays the syntax summary of **profiler** arguments.</span></span>  
  
 <span data-ttu-id="7503b-111">**/U** *login_id*</span><span class="sxs-lookup"><span data-stu-id="7503b-111">**/U** *login_id*</span></span>  
 <span data-ttu-id="7503b-112">這是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證的使用者登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="7503b-112">Is the user login ID for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="7503b-113">登入識別碼會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7503b-113">Login IDs are case sensitive.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]<span data-ttu-id="7503b-114">.</span><span class="sxs-lookup"><span data-stu-id="7503b-114">.</span></span>  
  
 <span data-ttu-id="7503b-115">**/P** *password*</span><span class="sxs-lookup"><span data-stu-id="7503b-115">**/P** *password*</span></span>  
 <span data-ttu-id="7503b-116">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之使用者指定的密碼。</span><span class="sxs-lookup"><span data-stu-id="7503b-116">Specifies a user-specified password for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="7503b-117">**/E**</span><span class="sxs-lookup"><span data-stu-id="7503b-117">**/E**</span></span>  
 <span data-ttu-id="7503b-118">利用目前使用者的認證來指定以 Windows 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="7503b-118">Specifies connecting with Windows Authentication with the current user's credentials.</span></span>  
  
 <span data-ttu-id="7503b-119">**/S**  *sql_server_name*</span><span class="sxs-lookup"><span data-stu-id="7503b-119">**/S**  *sql_server_name*</span></span>  
 <span data-ttu-id="7503b-120">指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7503b-120">Specifies an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7503b-121">Profiler 會利用 **/U** 和 **/P** 參數或 **/E** 參數所指定的驗證資訊，自動連接指定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7503b-121">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="7503b-122">若要連線到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的具名執行個體，請使用 **/S** *sql_server_name*\\*instance_name*。</span><span class="sxs-lookup"><span data-stu-id="7503b-122">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use **/S** *sql_server_name*\\*instance_name*.</span></span>  
  
 <span data-ttu-id="7503b-123">**/A**  *analysis_services_server_name*</span><span class="sxs-lookup"><span data-stu-id="7503b-123">**/A**  *analysis_services_server_name*</span></span>  
 <span data-ttu-id="7503b-124">指定 Analysis Services 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7503b-124">Specifies an instance of Analysis Services.</span></span> <span data-ttu-id="7503b-125">Profiler 會利用 **/U** 和 **/P** 參數或 **/E** 參數所指定的驗證資訊，自動連接指定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7503b-125">Profiler will automatically connect to the specified server using the authentication information specified in the **/U** and **/P** switches or the **/E** switch.</span></span> <span data-ttu-id="7503b-126">若要連線到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的具名執行個體，請使用 **/A** *analysis_services_server_name\instance_name*。</span><span class="sxs-lookup"><span data-stu-id="7503b-126">To connect to a named instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] use **/A** *analysis_services_server_name\instance_name*.</span></span>  
  
 <span data-ttu-id="7503b-127">**/D** *database*</span><span class="sxs-lookup"><span data-stu-id="7503b-127">**/D** *database*</span></span>  
 <span data-ttu-id="7503b-128">指定連接要用的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="7503b-128">Specifies the name of the database to be used with the connection.</span></span> <span data-ttu-id="7503b-129">如果未指定任何資料庫，這個選項會選取指定使用者的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="7503b-129">This option will select the default database for the specified user if no database is specified.</span></span>  
  
 <span data-ttu-id="7503b-130">**/B "** *trace_table_name* **"**</span><span class="sxs-lookup"><span data-stu-id="7503b-130">**/B "** *trace_table_name* **"**</span></span>  
 <span data-ttu-id="7503b-131">指定啟動 Profiler 時所載入的追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="7503b-131">Specifies a trace table to load when the profiler is launched.</span></span> <span data-ttu-id="7503b-132">您必須指定資料庫、使用者或結構描述，以及資料表。</span><span class="sxs-lookup"><span data-stu-id="7503b-132">You must specify the database, the user or schema, and the table.</span></span>  
  
 <span data-ttu-id="7503b-133">**/T"** *template_name* **"**</span><span class="sxs-lookup"><span data-stu-id="7503b-133">**/T"** *template_name* **"**</span></span>  
 <span data-ttu-id="7503b-134">指定將載入來設定追蹤的範本。</span><span class="sxs-lookup"><span data-stu-id="7503b-134">Specifies the template that will be loaded to configure the trace.</span></span> <span data-ttu-id="7503b-135">範本名稱必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="7503b-135">The template name must be in quotes.</span></span> <span data-ttu-id="7503b-136">範本名稱必須在系統範本目錄中，或在使用者範本目錄中。</span><span class="sxs-lookup"><span data-stu-id="7503b-136">The template name must be in either the system template directory or the user template directory.</span></span> <span data-ttu-id="7503b-137">如果兩個目錄中有同名的兩個範本存在，就會載入系統目錄中的範本。</span><span class="sxs-lookup"><span data-stu-id="7503b-137">If two templates with the same name exist in both directories, the template from the system directory will be loaded.</span></span> <span data-ttu-id="7503b-138">如果沒有含指定名稱的範本，便會載入標準範本。</span><span class="sxs-lookup"><span data-stu-id="7503b-138">If no template with the specified name exists, the standard template will be loaded.</span></span> <span data-ttu-id="7503b-139">請注意，在 <範本名稱> 中，不應指定範本的副檔名 (.tdf)。</span><span class="sxs-lookup"><span data-stu-id="7503b-139">Note that the file extension for the template (.tdf) should not be specified as part of the *template_name*.</span></span> <span data-ttu-id="7503b-140">例如：</span><span class="sxs-lookup"><span data-stu-id="7503b-140">For example:</span></span>  
  
```  
/T "standard"  
```  
  
 <span data-ttu-id="7503b-141">**/F"** *filename* **"**</span><span class="sxs-lookup"><span data-stu-id="7503b-141">**/F"** *filename* **"**</span></span>  
 <span data-ttu-id="7503b-142">指定啟動 Profiler 時所載入之追蹤檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7503b-142">Specifies the path and filename of a trace file to load when profiler is launched.</span></span> <span data-ttu-id="7503b-143">整個路徑和檔案名稱必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="7503b-143">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="7503b-144">這個選項不能搭配 **/O**一起使用。</span><span class="sxs-lookup"><span data-stu-id="7503b-144">This option cannot be used with **/O**.</span></span>  
  
 <span data-ttu-id="7503b-145">**/O "** *filename*  **"**</span><span class="sxs-lookup"><span data-stu-id="7503b-145">**/O "** *filename*  **"**</span></span>  
 <span data-ttu-id="7503b-146">指定應該寫入追蹤結果之檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7503b-146">Specifies the path and filename of a file to which trace results should be written.</span></span> <span data-ttu-id="7503b-147">整個路徑和檔案名稱必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="7503b-147">The entire path and filename must be in quotes.</span></span> <span data-ttu-id="7503b-148">這個選項不能搭配 **/F**一起使用。</span><span class="sxs-lookup"><span data-stu-id="7503b-148">This option cannot be used with **/F.**</span></span>  
  
 <span data-ttu-id="7503b-149">**/L** *locale_ID*</span><span class="sxs-lookup"><span data-stu-id="7503b-149">**/L** *locale_ID*</span></span>  
 <span data-ttu-id="7503b-150">無法使用。</span><span class="sxs-lookup"><span data-stu-id="7503b-150">Not available.</span></span>  
  
 <span data-ttu-id="7503b-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span><span class="sxs-lookup"><span data-stu-id="7503b-151">**/M "** *MM-DD-YY hh:mm:ss* **"**</span></span>  
 <span data-ttu-id="7503b-152">指定停止追蹤的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7503b-152">Specifies the date and time for the trace to stop.</span></span> <span data-ttu-id="7503b-153">停止時間必須用引號括住。</span><span class="sxs-lookup"><span data-stu-id="7503b-153">The stop time must be in quotes.</span></span> <span data-ttu-id="7503b-154">請根據下表中的參數來指定停止時間：</span><span class="sxs-lookup"><span data-stu-id="7503b-154">Specify the stop time according to the parameters in the table below:</span></span>  
  
|<span data-ttu-id="7503b-155">參數</span><span class="sxs-lookup"><span data-stu-id="7503b-155">Parameter</span></span>|<span data-ttu-id="7503b-156">定義</span><span class="sxs-lookup"><span data-stu-id="7503b-156">Definition</span></span>|  
|---------------|----------------|  
|<span data-ttu-id="7503b-157">MM</span><span class="sxs-lookup"><span data-stu-id="7503b-157">MM</span></span>|<span data-ttu-id="7503b-158">兩位數的月份</span><span class="sxs-lookup"><span data-stu-id="7503b-158">Two-digit month</span></span>|  
|<span data-ttu-id="7503b-159">DD</span><span class="sxs-lookup"><span data-stu-id="7503b-159">DD</span></span>|<span data-ttu-id="7503b-160">兩位數的日期</span><span class="sxs-lookup"><span data-stu-id="7503b-160">Two-digit day</span></span>|  
|<span data-ttu-id="7503b-161">YY</span><span class="sxs-lookup"><span data-stu-id="7503b-161">YY</span></span>|<span data-ttu-id="7503b-162">兩位數的年份</span><span class="sxs-lookup"><span data-stu-id="7503b-162">Two-digit year</span></span>|  
|<span data-ttu-id="7503b-163">hh</span><span class="sxs-lookup"><span data-stu-id="7503b-163">hh</span></span>|<span data-ttu-id="7503b-164">兩位數的小時 (24 小時制)</span><span class="sxs-lookup"><span data-stu-id="7503b-164">Two-digit hour on a 24-hour clock</span></span>|  
|<span data-ttu-id="7503b-165">mm</span><span class="sxs-lookup"><span data-stu-id="7503b-165">mm</span></span>|<span data-ttu-id="7503b-166">兩位數的分鐘</span><span class="sxs-lookup"><span data-stu-id="7503b-166">Two-digit minute</span></span>|  
|<span data-ttu-id="7503b-167">ss</span><span class="sxs-lookup"><span data-stu-id="7503b-167">ss</span></span>|<span data-ttu-id="7503b-168">兩位數的秒鐘</span><span class="sxs-lookup"><span data-stu-id="7503b-168">Two-digit second</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7503b-169">只有當 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中已啟用 [使用地區設定顯示日期與時間值] 選項時，才能使用 "MM-DD-YY hh:mm:ss" 格式。</span><span class="sxs-lookup"><span data-stu-id="7503b-169">The "MM-DD-YY hh:mm:ss" format can only be used if the **Use regional settings to display date and time values** option is enabled in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="7503b-170">如果這個選項未啟用，您必須使用 "YYYY-MM-DD hh:mm:ss" 日期和時間格式。</span><span class="sxs-lookup"><span data-stu-id="7503b-170">If this option is not enabled, you must use the "YYYY-MM-DD hh:mm:ss" date and time format.</span></span>  
  
 <span data-ttu-id="7503b-171">**/R**</span><span class="sxs-lookup"><span data-stu-id="7503b-171">**/R**</span></span>  
 <span data-ttu-id="7503b-172">啟用追蹤檔的換用。</span><span class="sxs-lookup"><span data-stu-id="7503b-172">Enables trace file rollover.</span></span>  
  
 <span data-ttu-id="7503b-173">**/Z**  *file_size*</span><span class="sxs-lookup"><span data-stu-id="7503b-173">**/Z**  *file_size*</span></span>  
 <span data-ttu-id="7503b-174">指定追蹤檔的大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="7503b-174">Specifies the size of the trace file in megabytes (MB).</span></span> <span data-ttu-id="7503b-175">預設大小是 5 MB。</span><span class="sxs-lookup"><span data-stu-id="7503b-175">The default size is 5 MB.</span></span> <span data-ttu-id="7503b-176">如果啟用換用，所有換用檔案都不能超出這個引數所指定的值。</span><span class="sxs-lookup"><span data-stu-id="7503b-176">If rollover is enabled, all rollover files will be limited to the value specified in this argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7503b-177">備註</span><span class="sxs-lookup"><span data-stu-id="7503b-177">Remarks</span></span>  
 <span data-ttu-id="7503b-178">若要利用特定範本啟動追蹤，請同時使用 **/S** 和 **/T** 選項。</span><span class="sxs-lookup"><span data-stu-id="7503b-178">To start a trace with a specific template, use the **/S** and **/T** options together.</span></span> <span data-ttu-id="7503b-179">例如，若要利用 MyServer\MyInstance 上的 Standard 範本啟動追蹤，請在命令提示字元之下輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="7503b-179">For example, to start a trace using the Standard template on MyServer\MyInstance, enter the following at the command prompt:</span></span>  
  
```  
profiler /S MyServer\MyInstance /T "Standard"  
```  
  
## <a name="see-also"></a><span data-ttu-id="7503b-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7503b-180">See Also</span></span>  
 [<span data-ttu-id="7503b-181">命令提示字元公用程式參考 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="7503b-181">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
