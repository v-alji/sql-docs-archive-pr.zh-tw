---
title: SSMS 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0cfc9469e49e6ce3839d02a61477b8957fbc13e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606015"
---
# <a name="ssms-utility"></a><span data-ttu-id="5cce3-102">Ssms 公用程式</span><span class="sxs-lookup"><span data-stu-id="5cce3-102">Ssms Utility</span></span>
  <span data-ttu-id="5cce3-103">**Ssms** 公用程式會開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5cce3-103">The **Ssms**utility opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5cce3-104">如果有指定， **Ssms** 也會建立伺服器的連接，且會開啟查詢、指令碼、檔案、專案和方案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-104">If specified, **Ssms** also establishes a connection to a server, and opens queries, scripts, files, projects, and solutions.</span></span>  
  
 <span data-ttu-id="5cce3-105">您可以指定包含查詢、專案或方案的檔案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-105">You can specify files that contain queries, projects, or solutions.</span></span> <span data-ttu-id="5cce3-106">如果提供了連接資訊，且檔案類型與這個類型的伺服器相關聯，包含查詢的檔案會自動連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="5cce3-106">Files that contain queries are automatically connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="5cce3-107">例如，.sql 檔會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟一個 [SQL 查詢編輯器] 視窗，.mdx 檔會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟一個 [MDX 查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5cce3-107">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5cce3-108">而**SQL Server 方案和專案** 會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟。</span><span class="sxs-lookup"><span data-stu-id="5cce3-108">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5cce3-109">**Ssms** 公用程式不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="5cce3-109">The **Ssms** utility does not run queries.</span></span> <span data-ttu-id="5cce3-110">若要從命令列中執行查詢，請使用 **sqlcmd** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="5cce3-110">To run queries from the command line, use the **sqlcmd** utility.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cce3-111">語法</span><span class="sxs-lookup"><span data-stu-id="5cce3-111">Syntax</span></span>  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5cce3-112">引數</span><span class="sxs-lookup"><span data-stu-id="5cce3-112">Arguments</span></span>  
 <span data-ttu-id="5cce3-113">*scriptfile*</span><span class="sxs-lookup"><span data-stu-id="5cce3-113">*scriptfile*</span></span>  
 <span data-ttu-id="5cce3-114">指定一個或多個要開啟的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-114">Specifies one or more script files to open.</span></span> <span data-ttu-id="5cce3-115">這個參數必須包含檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5cce3-115">The parameter must contain the full path to the files.</span></span>  
  
 <span data-ttu-id="5cce3-116">*projectfile*</span><span class="sxs-lookup"><span data-stu-id="5cce3-116">*projectfile*</span></span>  
 <span data-ttu-id="5cce3-117">指定要開啟的指令碼專案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-117">Specifies a script project to open.</span></span> <span data-ttu-id="5cce3-118">這個參數必須包含指令碼專案檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5cce3-118">The parameter must contain the full path to the script project file.</span></span>  
  
 <span data-ttu-id="5cce3-119">*solutionfile*</span><span class="sxs-lookup"><span data-stu-id="5cce3-119">*solutionfile*</span></span>  
 <span data-ttu-id="5cce3-120">指定要開啟的方案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-120">Specifies a solution to open.</span></span> <span data-ttu-id="5cce3-121">這個參數必須包含方案檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="5cce3-121">The parameter must contain the full path to the solution file.</span></span>  
  
 <span data-ttu-id="5cce3-122">[**-S** _servername_]</span><span class="sxs-lookup"><span data-stu-id="5cce3-122">[**-S** _servername_]</span></span>  
 <span data-ttu-id="5cce3-123">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="5cce3-123">Server name</span></span>  
  
 <span data-ttu-id="5cce3-124">[**-d** _databasename_]</span><span class="sxs-lookup"><span data-stu-id="5cce3-124">[**-d** _databasename_]</span></span>  
 <span data-ttu-id="5cce3-125">資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="5cce3-125">Database name</span></span>  
  
 <span data-ttu-id="5cce3-126">[**-U** _username_]</span><span class="sxs-lookup"><span data-stu-id="5cce3-126">[**-U** _username_]</span></span>  
 <span data-ttu-id="5cce3-127">利用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證來連接時的使用者名稱</span><span class="sxs-lookup"><span data-stu-id="5cce3-127">User name when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="5cce3-128">[**-P** _密碼_]</span><span class="sxs-lookup"><span data-stu-id="5cce3-128">[**-P** _password_]</span></span>  
 <span data-ttu-id="5cce3-129">利用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證來連接時的密碼</span><span class="sxs-lookup"><span data-stu-id="5cce3-129">Password when connecting with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication</span></span>  
  
 <span data-ttu-id="5cce3-130">[**-E**]</span><span class="sxs-lookup"><span data-stu-id="5cce3-130">[**-E**]</span></span>  
 <span data-ttu-id="5cce3-131">使用 Windows 驗證進行連接</span><span class="sxs-lookup"><span data-stu-id="5cce3-131">Connect using Windows Authentication</span></span>  
  
 <span data-ttu-id="5cce3-132">[**-nosplash**]</span><span class="sxs-lookup"><span data-stu-id="5cce3-132">[**-nosplash**]</span></span>  
 <span data-ttu-id="5cce3-133">在開啟時，使 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 不呈現開頭顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="5cce3-133">Prevents [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from displaying the splash screen graphic while opening.</span></span> <span data-ttu-id="5cce3-134">當您利用頻寬有限的連接，透過「終端機服務」來連接執行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的電腦時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="5cce3-134">Use this option when connecting to the computer running [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by means of Terminal Services over a connection with a limited bandwidth.</span></span> <span data-ttu-id="5cce3-135">這個引數不區分大小寫，可出現在其他引數的前後。</span><span class="sxs-lookup"><span data-stu-id="5cce3-135">This argument is not case-sensitive and may appear before or after other arguments</span></span>  
  
 <span data-ttu-id="5cce3-136">[**-log**_[filename]？_]</span><span class="sxs-lookup"><span data-stu-id="5cce3-136">[**-log**_[filename]?_]</span></span>  
 <span data-ttu-id="5cce3-137">將 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 活動記錄到指定的檔案以利於進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="5cce3-137">Logs [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] activity to the specified file for troubleshooting</span></span>  
  
 <span data-ttu-id="5cce3-138">[**-?**]</span><span class="sxs-lookup"><span data-stu-id="5cce3-138">[**-?**]</span></span>  
 <span data-ttu-id="5cce3-139">顯示命令列說明</span><span class="sxs-lookup"><span data-stu-id="5cce3-139">Displays command line help</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cce3-140">備註</span><span class="sxs-lookup"><span data-stu-id="5cce3-140">Remarks</span></span>  
 <span data-ttu-id="5cce3-141">所有參數都是選擇性的，除了用逗號來分隔的檔案之外，您必須用空格來分隔它們。</span><span class="sxs-lookup"><span data-stu-id="5cce3-141">All of the switches are optional and separated by a space except files which are separated by commas.</span></span> <span data-ttu-id="5cce3-142">如果您沒有指定任何參數，**Ssms** 會依照 [工具]\*\*\*\* 功能表上，[選項]\*\*\*\* 設定中所指定的內容來開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5cce3-142">If you do not specify any switches, **Ssms** opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] as specified in the **Options** settings on the **Tools** menu.</span></span> <span data-ttu-id="5cce3-143">例如，如果 [環境/一般]\*\*\*\* 頁面的 [啟動時]\*\*\*\* 選項指定 [開啟新增查詢視窗]\*\*\*\*，**Ssms** 會以空白的查詢編輯器開啟。</span><span class="sxs-lookup"><span data-stu-id="5cce3-143">For example, if the **Environment/General** page **At startup** option specifies **Open new query window**, **Ssms** will open with a blank Query Editor.</span></span>  
  
 <span data-ttu-id="5cce3-144">**-Log**參數必須出現在命令列的結尾，在所有其他參數之後。</span><span class="sxs-lookup"><span data-stu-id="5cce3-144">The **-log** switch must appear at the end of the command line, after all other switches.</span></span> <span data-ttu-id="5cce3-145">檔名引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="5cce3-145">The filename argument is optional.</span></span> <span data-ttu-id="5cce3-146">如果指定了檔名，但該檔案不存在，便會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-146">If a filename is specified, and the file does not exist, the file is created.</span></span> <span data-ttu-id="5cce3-147">若因寫入權限不足等緣故而無法建立檔案，則會改將記錄寫入未當地語系化的 APPDATA 位置 (請參閱下文)。</span><span class="sxs-lookup"><span data-stu-id="5cce3-147">If the file cannot be created - for example, due to insufficient write access, the log is written to the nonlocalized APPDATA location instead (See below).</span></span> <span data-ttu-id="5cce3-148">如果未指定檔名引數，便會將兩個檔案寫入至目前使用者的未當地語系化應用程式儲存資料夾。</span><span class="sxs-lookup"><span data-stu-id="5cce3-148">If the filename argument is not specified, two files are written to the current user's nonlocalized application data folder.</span></span> <span data-ttu-id="5cce3-149">SQL Server 的未當地語系化應用程式儲存資料夾可以由 APPDATA 環境變數查知。</span><span class="sxs-lookup"><span data-stu-id="5cce3-149">The nonlocalized application data folder for SQL Server can be found from the APPDATA environment variable.</span></span> <span data-ttu-id="5cce3-150">例如，針對 SQL Server 2012，資料夾為 \<system drive> ： \Users \\<username \> \AppData\Roaming\Microsoft\AppEnv\10.0 \\ 。</span><span class="sxs-lookup"><span data-stu-id="5cce3-150">For example, for SQL Server 2012, the folder is \<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\\.</span></span> <span data-ttu-id="5cce3-151">兩個檔案依預設將名為 ActivityLog.xml 和 ActivityLog.xsl。</span><span class="sxs-lookup"><span data-stu-id="5cce3-151">The two files are, by default, named ActivityLog.xml and ActivityLog.xsl.</span></span> <span data-ttu-id="5cce3-152">前者包含活動記錄資料，後者則是 XML 樣式表以讓您更方便檢視此 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5cce3-152">The former contains the activity log data and the latter is an XML style sheet which provides a more convenient way to view the XML file.</span></span> <span data-ttu-id="5cce3-153">使用下列步驟，在您的預設 XML 檢視器中查看記錄檔，例如 Internet Explorer：依序按一下 [開始]、[執行 ...]，然後 \<system drive> 在提供的欄位中輸入 "： \Users \\<username \>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml"，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="5cce3-153">Use the following steps to view the log file in your default XML viewer, like Internet Explorer:  Click Start, then click Run...", then type "\<system drive>:\Users\\<username\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml" into the field provided, and then press Enter.</span></span>  
  
 <span data-ttu-id="5cce3-154">如果提供了連接資訊，且檔案類型與這個類型的伺服器相關聯，便會發出包含查詢的檔案連接到伺服器的提示。</span><span class="sxs-lookup"><span data-stu-id="5cce3-154">Files that contain queries will prompt to be connected to a server if connection information is provided and the file type is associated with that type of server.</span></span> <span data-ttu-id="5cce3-155">例如，.sql 檔會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟一個 [SQL 查詢編輯器] 視窗，.mdx 檔會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟一個 [MDX 查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="5cce3-155">For instance, .sql files will open a SQL Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and .mdx files will open an MDX Query Editor window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="5cce3-156">而**SQL Server 方案和專案** 會在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中開啟。</span><span class="sxs-lookup"><span data-stu-id="5cce3-156">**SQL Server Solutions and Projects** will open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="5cce3-157">下表將伺服器類型對應至副檔名。</span><span class="sxs-lookup"><span data-stu-id="5cce3-157">The following table maps server types to file extensions.</span></span>  
  
|<span data-ttu-id="5cce3-158">伺服器類型</span><span class="sxs-lookup"><span data-stu-id="5cce3-158">Server type</span></span>|<span data-ttu-id="5cce3-159">分機</span><span class="sxs-lookup"><span data-stu-id="5cce3-159">Extension</span></span>|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|<span data-ttu-id="5cce3-160">.sql</span><span class="sxs-lookup"><span data-stu-id="5cce3-160">.sql</span></span>|  
|<span data-ttu-id="5cce3-161">SQL Server Analysis Services</span><span class="sxs-lookup"><span data-stu-id="5cce3-161">SQL Server Analysis Services</span></span>|<span data-ttu-id="5cce3-162">.mdx</span><span class="sxs-lookup"><span data-stu-id="5cce3-162">.mdx</span></span><br /><br /> <span data-ttu-id="5cce3-163">.xmla</span><span class="sxs-lookup"><span data-stu-id="5cce3-163">.xmla</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="5cce3-164">範例</span><span class="sxs-lookup"><span data-stu-id="5cce3-164">Examples</span></span>  
 <span data-ttu-id="5cce3-165">下列指令碼會在命令提示字元之下，利用預設值來開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="5cce3-165">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt with the default settings:</span></span>  
  
```  
Ssms  
  
```  
  
 <span data-ttu-id="5cce3-166">下列指令碼會在命令提示字元之下，將程式碼編輯器設為伺服器 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，在不呈現開頭顯示畫面的情況下，利用 Windows 驗證來開啟 `ACCTG and the database AdventureWorks2012,` ：</span><span class="sxs-lookup"><span data-stu-id="5cce3-166">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, with Windows Authentication, with the Code Editor set to the server `ACCTG and the database AdventureWorks2012,` without showing the splash screen:</span></span>  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 <span data-ttu-id="5cce3-167">下列指令碼會在命令提示字元之下開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，且會開啟 MonthEndQuery 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5cce3-167">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthEndQuery script.</span></span>  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 <span data-ttu-id="5cce3-168">下列指令碼會在命令提示字元之下開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，且會在名稱為 `developer`的電腦上開啟 NewReportsProject 專案：</span><span class="sxs-lookup"><span data-stu-id="5cce3-168">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the NewReportsProject project on the computer named `developer`:</span></span>  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 <span data-ttu-id="5cce3-169">下列指令碼會在命令提示字元之下開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，且會開啟 MonthlyReports 方案：</span><span class="sxs-lookup"><span data-stu-id="5cce3-169">The following script opens [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt, and opens the MonthlyReports solution:</span></span>  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cce3-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cce3-170">See Also</span></span>  
 [<span data-ttu-id="5cce3-171">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5cce3-171">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
