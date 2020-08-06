---
title: sqlmaint 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- database maintenance plans [SQL Server]
- sqlmaint utility
- maintaining databases [SQL Server]
- backups [SQL Server], sqlmaint utility
- command prompt utilities [SQL Server], sqlmaint
- maintenance plans [SQL Server], command prompt
- backing up [SQL Server], sqlmaint utility
ms.assetid: 937a9932-4aed-464b-b97a-a5acfe6a50de
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80e60b75305ee91e8b62a201d9c86af301326789
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686573"
---
# <a name="sqlmaint-utility"></a><span data-ttu-id="c7e40-102">sqlmaint 公用程式</span><span class="sxs-lookup"><span data-stu-id="c7e40-102">sqlmaint Utility</span></span>
  <span data-ttu-id="c7e40-103">如果**sqlmaint** 公用程式會在一或多個資料庫上，執行一組指定的維護作業。</span><span class="sxs-lookup"><span data-stu-id="c7e40-103">The**sqlmaint** utility performs a specified set of maintenance operations on one or more databases.</span></span> <span data-ttu-id="c7e40-104">利用 **sqlmaint** 來執行 DBCC 檢查、備份資料庫及其交易記錄、更新統計資料，以及重建索引。</span><span class="sxs-lookup"><span data-stu-id="c7e40-104">Use **sqlmaint** to run DBCC checks, back up a database and its transaction log, update statistics, and rebuild indexes.</span></span> <span data-ttu-id="c7e40-105">所有資料庫維護活動都會產生一份可傳給指定文字檔、HTML 檔或電子郵件帳戶的報表。</span><span class="sxs-lookup"><span data-stu-id="c7e40-105">All database maintenance activities generate a report that can be sent to a designated text file, HTML file, or e-mail account.</span></span> <span data-ttu-id="c7e40-106">**sqlmaint** 會執行舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]所建立的資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="c7e40-106">**sqlmaint** executes database maintenance plans created with previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7e40-107">若要從命令提示字元執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 維護計畫，請使用 [dtexec 公用程式](../integration-services/packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-107">To run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plans from the command prompt, use the [dtexec Utility](../integration-services/packages/dtexec-utility.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../includes/ssnotedepnextavoid-md.md)] <span data-ttu-id="c7e40-108">請改用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 維護計畫功能。</span><span class="sxs-lookup"><span data-stu-id="c7e40-108">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] maintenance plan feature instead.</span></span> <span data-ttu-id="c7e40-109">如需維護計畫的詳細資訊，請參閱 [維護計畫](../relational-databases/maintenance-plans/maintenance-plans.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-109">For more information on maintenance plans, see [Maintenance Plans](../relational-databases/maintenance-plans/maintenance-plans.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e40-110">語法</span><span class="sxs-lookup"><span data-stu-id="c7e40-110">Syntax</span></span>  
  
```  
  
      sqlmaint   
[-?] |  
[  
     [-Sserver_name[\instance_name]]  
     [-Ulogin_ID [-Ppassword]]  
     {  
          [-Ddatabase_name | -PlanNamename | -PlanIDguid ]  
          [-Rpttext_file]  
          [-Tooperator_name]  
          [-HtmlRpthtml_file [-DelHtmlRpt <time_period>] ]  
          [-RmUnusedSpacethreshold_percentfree_percent]  
          [-CkDB | -CkDBNoIdx]  
          [-CkAl | -CkAlNoIdx]  
          [-CkCat]  
          [-UpdOptiStatssample_percent]  
          [-RebldIdxfree_space]  
          [-SupportComputedColumn]  
          [-WriteHistory]  
          [  
               {-BkUpDB [backup_path] | -BkUpLog [backup_path] }  
               {-BkUpMedia  
                    {DISK [  
                           [-DelBkUps<time_period>]   
                           [-CrBkSubDir ]   
                           [-UseDefDir ]   
                          ]  
                     | TAPE   
                    }  
               }  
               [-BkUpOnlyIfClean]  
               [-VrfyBackup]  
          ]  
     }  
]  
<time_period> ::=  
number[minutes | hours | days | weeks | months]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7e40-111">引數</span><span class="sxs-lookup"><span data-stu-id="c7e40-111">Arguments</span></span>  
 <span data-ttu-id="c7e40-112">參數和值必須用空格分隔。</span><span class="sxs-lookup"><span data-stu-id="c7e40-112">The parameters and their values must be separated by a space.</span></span> <span data-ttu-id="c7e40-113">例如， **-S** 和 *server_name*之間必須有一個空格。</span><span class="sxs-lookup"><span data-stu-id="c7e40-113">For example, there must be a space between **-S** and *server_name*.</span></span>  
  
 <span data-ttu-id="c7e40-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="c7e40-114">**-?**</span></span>  
 <span data-ttu-id="c7e40-115">指定傳回 **sqlmaint** 的語法圖。</span><span class="sxs-lookup"><span data-stu-id="c7e40-115">Specifies that the syntax diagram for **sqlmaint** be returned.</span></span> <span data-ttu-id="c7e40-116">這個參數必須單獨使用。</span><span class="sxs-lookup"><span data-stu-id="c7e40-116">This parameter must be used alone.</span></span>  
  
 <span data-ttu-id="c7e40-117">**-S** _server_name_[ **\\** _instance_name_]</span><span class="sxs-lookup"><span data-stu-id="c7e40-117">**-S** _server_name_[ **\\**_instance_name_]</span></span>  
 <span data-ttu-id="c7e40-118">指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7e40-118">Specifies the target instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c7e40-119">指定 *server_name* ，即可連接至該伺服器上之 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7e40-119">Specify *server_name* to connect to the default instance of [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on that server.</span></span> <span data-ttu-id="c7e40-120">指定要連接到該伺服器上之已命名實例的*server_name **_\\_** instance_name* [!INCLUDE[ssDE](../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c7e40-120">Specify *server_name\*\*_\\_*\* instance_name\* to connect to a named instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on that server.</span></span> <span data-ttu-id="c7e40-121">如果未指定伺服器， **sqlmaint** 會連接到本機電腦中 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7e40-121">If no server is specified, **sqlmaint** connects to the default instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] on the local computer.</span></span>  
  
 <span data-ttu-id="c7e40-122">**-U** _login_ID_</span><span class="sxs-lookup"><span data-stu-id="c7e40-122">**-U** _login_ID_</span></span>  
 <span data-ttu-id="c7e40-123">指定連接伺服器時所用的登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="c7e40-123">Specifies the login ID to use when connecting to the server.</span></span> <span data-ttu-id="c7e40-124">如果未提供， **sqlmaint** 會嘗試使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c7e40-124">If not supplied, **sqlmaint** attempts to use [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span> <span data-ttu-id="c7e40-125">如果 *login_ID* 包含特殊字元，則必須以雙引號 (") 括住；否則可省略雙引號。</span><span class="sxs-lookup"><span data-stu-id="c7e40-125">If *login_ID* contains special characters, it must be enclosed in double quotation marks ("); otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7e40-126">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c7e40-126">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="c7e40-127">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="c7e40-127">**-P** _password_</span></span>  
 <span data-ttu-id="c7e40-128">指定登入識別碼的密碼。</span><span class="sxs-lookup"><span data-stu-id="c7e40-128">Specifies the password for the login ID.</span></span> <span data-ttu-id="c7e40-129">只有在同時提供 **-U** 參數時，這才有效。</span><span class="sxs-lookup"><span data-stu-id="c7e40-129">Only valid if the **-U** parameter is also supplied.</span></span> <span data-ttu-id="c7e40-130">如果 *password* 包含特殊字元，則必須將此引數括在雙引號內，否則可省略雙引號。</span><span class="sxs-lookup"><span data-stu-id="c7e40-130">If *password* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7e40-131">密碼不會有遮罩。</span><span class="sxs-lookup"><span data-stu-id="c7e40-131">The password is not masked.</span></span> <span data-ttu-id="c7e40-132">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c7e40-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="c7e40-133">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="c7e40-133">**-D** _database_name_</span></span>  
 <span data-ttu-id="c7e40-134">指定要執行維護作業的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-134">Specifies the name of the database in which to perform the maintenance operation.</span></span> <span data-ttu-id="c7e40-135">如果 *database_name* 包含特殊字元，則必須以雙引號括住；否則可省略雙引號。</span><span class="sxs-lookup"><span data-stu-id="c7e40-135">If *database_name* contains special characters, it must be enclosed in double quotation marks; otherwise, the double quotation marks are optional.</span></span>  
  
 <span data-ttu-id="c7e40-136">**-PlanName** _name_</span><span class="sxs-lookup"><span data-stu-id="c7e40-136">**-PlanName** _name_</span></span>  
 <span data-ttu-id="c7e40-137">指定利用資料庫維護計畫精靈定義的資料庫維護計畫名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-137">Specifies the name of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="c7e40-138">**sqlmaint** 所用的計畫資訊，只有計畫中的資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="c7e40-138">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="c7e40-139">您在其他 **sqlmaint** 參數中指定的任何維護活動，都會套用到此資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="c7e40-139">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span>  
  
 <span data-ttu-id="c7e40-140">**-PlanID** _guid_</span><span class="sxs-lookup"><span data-stu-id="c7e40-140">**-PlanID** _guid_</span></span>  
 <span data-ttu-id="c7e40-141">指定利用資料庫維護計畫精靈定義之資料庫維護計畫的全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-141">Specifies the globally unique identifier (GUID) of a database maintenance plan defined using the Database Maintenance Plan Wizard.</span></span> <span data-ttu-id="c7e40-142">**sqlmaint** 所用的計畫資訊，只有計畫中的資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="c7e40-142">The only information **sqlmaint** uses from the plan is the list of the databases in the plan.</span></span> <span data-ttu-id="c7e40-143">您在其他 **sqlmaint** 參數中指定的任何維護活動，都會套用到此資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="c7e40-143">Any maintenance activities you specify in the other **sqlmaint** parameters are applied to this list of databases.</span></span> <span data-ttu-id="c7e40-144">這必須符合 msdb.dbo.sysdbmaintplans 中的 plan_id 值。</span><span class="sxs-lookup"><span data-stu-id="c7e40-144">This must match a plan_id value in msdb.dbo.sysdbmaintplans.</span></span>  
  
 <span data-ttu-id="c7e40-145">**-Rpt** _text_file_</span><span class="sxs-lookup"><span data-stu-id="c7e40-145">**-Rpt** _text_file_</span></span>  
 <span data-ttu-id="c7e40-146">指定要產生報表之檔案的完整路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-146">Specifies the full path and name of the file into which the report is to be generated.</span></span> <span data-ttu-id="c7e40-147">報表也會出現在畫面中。</span><span class="sxs-lookup"><span data-stu-id="c7e40-147">The report is also generated on the screen.</span></span> <span data-ttu-id="c7e40-148">這份報表會在檔案名稱中附加日期來維護版本資訊。</span><span class="sxs-lookup"><span data-stu-id="c7e40-148">The report maintains version information by adding a date to the file name.</span></span> <span data-ttu-id="c7e40-149">日期的產生方式如下：在檔案名稱的尾端、英文句點的前面，格式如下：_*yyyyMMddhhmm*。</span><span class="sxs-lookup"><span data-stu-id="c7e40-149">The date is generated as follows: at the end of the file name but before the period, in the form _*yyyyMMddhhmm*.</span></span> <span data-ttu-id="c7e40-150">*yyyy* = 年、 *MM* = 月、 *dd* = 日、 *hh* = 時、 *mm* = 分。</span><span class="sxs-lookup"><span data-stu-id="c7e40-150">*yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, *mm* = minute.</span></span>  
  
 <span data-ttu-id="c7e40-151">如果您在</span><span class="sxs-lookup"><span data-stu-id="c7e40-151">If you run the utility at 10:23 A.M.</span></span> <span data-ttu-id="c7e40-152">1996 年 12 月 1 日上午 10:23 執行這個公用程式，則 *text_file* 值如下：</span><span class="sxs-lookup"><span data-stu-id="c7e40-152">on December 1, 1996, and this is the *text_file* value:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.rpt  
```  
  
 <span data-ttu-id="c7e40-153">產生的檔案名稱如下：</span><span class="sxs-lookup"><span data-stu-id="c7e40-153">The generated file name is:</span></span>  
  
```  
c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint_199612011023.rpt  
```  
  
 <span data-ttu-id="c7e40-154">當 *sqlmaint* 存取遠端伺服器時，需要 **text_file** 的完整通用命名慣例 (UNC) 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-154">The full Universal Naming Convention (UNC) file name is required for *text_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="c7e40-155">**-To** _operator_name_</span><span class="sxs-lookup"><span data-stu-id="c7e40-155">**-To** _operator_name_</span></span>  
 <span data-ttu-id="c7e40-156">指定將接收 SQL Mail 所產生之報表的操作員。</span><span class="sxs-lookup"><span data-stu-id="c7e40-156">Specifies the operator to whom the generated report is sent through SQL Mail.</span></span>  
  
 <span data-ttu-id="c7e40-157">**-HtmlRpt** _html_file_</span><span class="sxs-lookup"><span data-stu-id="c7e40-157">**-HtmlRpt** _html_file_</span></span>  
 <span data-ttu-id="c7e40-158">指定要產生 HTML 報表之檔案的完整路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-158">Specifies the full path and name of the file into which an HTML report is to be generated.</span></span> <span data-ttu-id="c7e40-159">**sqlmaint** 也會在檔案名稱中附加 _*yyyyMMddhhmm* 格式的字串來產生檔案名稱，就像其對 **-Rpt** 參數所做的。</span><span class="sxs-lookup"><span data-stu-id="c7e40-159">**sqlmaint** generates the file name by appending a string of the format _*yyyyMMddhhmm* to the file name, just as it does for the **-Rpt** parameter.</span></span>  
  
 <span data-ttu-id="c7e40-160">當 *sqlmaint* 存取遠端伺服器時，需要 **html_file** 的完整 UNC 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-160">The full UNC file name is required for *html_file* when **sqlmaint** accesses a remote server.</span></span>  
  
 <span data-ttu-id="c7e40-161">**-DelHtmlRpt** \<*time_period*></span><span class="sxs-lookup"><span data-stu-id="c7e40-161">**-DelHtmlRpt** \<*time_period*></span></span>  
 <span data-ttu-id="c7e40-162">指定如果建立報表檔之後的時間間隔超出 \<*time_period*>，便刪除報表目錄中的任何 HTML 報表。</span><span class="sxs-lookup"><span data-stu-id="c7e40-162">Specifies that any HTML report in the report directory be deleted if the time interval after the creation of the report file exceeds \<*time_period*>.</span></span> <span data-ttu-id="c7e40-163">**-DelHtmlRpt** 會尋找名稱符合 *html_file* 參數所產生之模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="c7e40-163">**-DelHtmlRpt** looks for files whose name fits the pattern generated from the *html_file* parameter.</span></span> <span data-ttu-id="c7e40-164">如果 *html_file* 是 c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm，則 **-DelHtmlRpt** 會導致 **sqlmaint** 刪除名稱符合 C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm 模式，而且比指定的 \<*time_period*> 還舊的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="c7e40-164">If *html_file* is c:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint.htm, then **-DelHtmlRpt** causes **sqlmaint** to delete any files whose names match the pattern C:\Program Files\Microsoft SQL Server\Mssql\Backup\AdventureWorks2012_maint\*.htm and that are older than the specified \<*time_period*>.</span></span>  
  
 <span data-ttu-id="c7e40-165">**-RmUnusedSpace** _threshold_percent free_percent_</span><span class="sxs-lookup"><span data-stu-id="c7e40-165">**-RmUnusedSpace** _threshold_percent free_percent_</span></span>  
 <span data-ttu-id="c7e40-166">指定從 **-D**指定的資料庫中移除未使用的空間。</span><span class="sxs-lookup"><span data-stu-id="c7e40-166">Specifies that unused space be removed from the database specified in **-D**.</span></span> <span data-ttu-id="c7e40-167">這個選項只適用於定義成自動成長的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7e40-167">This option is only useful for databases that are defined to grow automatically.</span></span> <span data-ttu-id="c7e40-168">*Threshold_percent* 會以 MB 為單位來指定大小，一旦資料庫到達此大小之後， **sqlmaint** 便會嘗試移除未使用的資料空間。</span><span class="sxs-lookup"><span data-stu-id="c7e40-168">*Threshold_percent* specifies in megabytes the size that the database must reach before **sqlmaint** attempts to remove unused data space.</span></span> <span data-ttu-id="c7e40-169">在資料庫大小小於 *threshold_percent*時，則不會採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="c7e40-169">If the database is smaller than the *threshold_percent*, no action is taken.</span></span> <span data-ttu-id="c7e40-170">*Free_percent* 會指定必須保留在資料庫中的未使用空間大小，指定的方式是資料庫最終大小的百分比。</span><span class="sxs-lookup"><span data-stu-id="c7e40-170">*Free_percent* specifies how much unused space must remain in the database, specified as a percentage of the final size of the database.</span></span> <span data-ttu-id="c7e40-171">例如，如果 200 MB 資料庫包含 100 MB 的資料， *free_percent* 指定 10 會使最終資料庫大小成為 110 MB。</span><span class="sxs-lookup"><span data-stu-id="c7e40-171">For example, if a 200-MB database contains 100 MB of data, specifying 10 for *free_percent* results in the final database size being 110 MB.</span></span> <span data-ttu-id="c7e40-172">請注意，如果資料庫小於 *free_percent* 加上資料庫中的資料量，就不會擴充資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7e40-172">Note that a database is not expanded if it is smaller than *free_percent* plus the amount of data in the database.</span></span> <span data-ttu-id="c7e40-173">例如，如果 108 MB 的資料庫包含 100 MB 的資料， *free_percent* 指定 10 並不會將資料庫擴充成 110 MB；它會保持 108 MB。</span><span class="sxs-lookup"><span data-stu-id="c7e40-173">For example, if a 108-MB database has 100 MB of data, specifying 10 for *free_percent* does not expand the database to 110 MB; it remains at 108 MB.</span></span>  
  
 <span data-ttu-id="c7e40-174">**-CkDB** |  **-CkDBNoIdx**</span><span class="sxs-lookup"><span data-stu-id="c7e40-174">**-CkDB** | **-CkDBNoIdx**</span></span>  
 <span data-ttu-id="c7e40-175">指定在 **-D**所指定的資料庫中，執行設定了 NOINDEX 選項的 DBCC CHECKDB 陳述式或 DBCC CHECKDB 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7e40-175">Specifies that a DBCC CHECKDB statement or a DBCC CHECKDB statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="c7e40-176">如需詳細資訊，請參閱 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="c7e40-176">For more information, see DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="c7e40-177">如果執行 *sqlmaint* 時資料庫正在使用中，就會在 **text_file** 中寫入一則警告。</span><span class="sxs-lookup"><span data-stu-id="c7e40-177">A warning is written to *text_file* if the database is in use when **sqlmaint** runs.</span></span>  
  
 <span data-ttu-id="c7e40-178">**-CkAl** |  **-CkAlNoIdx**</span><span class="sxs-lookup"><span data-stu-id="c7e40-178">**-CkAl** | **-CkAlNoIdx**</span></span>  
 <span data-ttu-id="c7e40-179">指定在 **-D**所指定的資料庫中，執行設定了 NOINDEX 選項的 DBCC CHECKALLOC 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7e40-179">Specifies that a DBCC CHECKALLOC statement with the NOINDEX option be run in the database specified in **-D**.</span></span> <span data-ttu-id="c7e40-180">如需詳細資訊，請參閱 [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-180">For more information, see [DBCC CHECKALLOC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkalloc-transact-sql).</span></span>  
  
 <span data-ttu-id="c7e40-181">**-CkCat**</span><span class="sxs-lookup"><span data-stu-id="c7e40-181">**-CkCat**</span></span>  
 <span data-ttu-id="c7e40-182">指定在 **-D** 所指定的資料庫中，執行 DBCC CHECKCATALOG (Transact-SQL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c7e40-182">Specifies that a DBCC CHECKCATALOG (Transact-SQL) statement be run in the database specified in **-D**.</span></span> <span data-ttu-id="c7e40-183">如需詳細資訊，請參閱 [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-183">For more information, see [DBCC CHECKCATALOG &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkcatalog-transact-sql).</span></span>  
  
 <span data-ttu-id="c7e40-184">**-UpdOptiStats** _sample_percent_</span><span class="sxs-lookup"><span data-stu-id="c7e40-184">**-UpdOptiStats** _sample_percent_</span></span>  
 <span data-ttu-id="c7e40-185">指定在資料庫的各份資料表上，執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="c7e40-185">Specifies that the following statement be run on each table in the database:</span></span>  
  
```  
UPDATE STATISTICS table WITH SAMPLE sample_percent PERCENT;  
```  
  
 <span data-ttu-id="c7e40-186">如果資料表包含計算資料行，當您使用 **-UpdOptiStats** 時，也必須指定 **-SupportedComputedColumn**引數。</span><span class="sxs-lookup"><span data-stu-id="c7e40-186">If the tables contain computed columns, you must also specify the **-SupportedComputedColumn** argument when you use **-UpdOptiStats**.</span></span>  
  
 <span data-ttu-id="c7e40-187">如需詳細資訊，請參閱 [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql)所建立的資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="c7e40-187">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql).</span></span>  
  
 <span data-ttu-id="c7e40-188">**-RebldIdx** _free_space_</span><span class="sxs-lookup"><span data-stu-id="c7e40-188">**-RebldIdx** _free_space_</span></span>  
 <span data-ttu-id="c7e40-189">指定應該利用 *free_space* 百分比值作為填滿因數的反項，藉以重建目標資料庫中各資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="c7e40-189">Specifies that indexes on tables in the target database should be rebuilt by using the *free_space* percent value as the inverse of the fill factor.</span></span> <span data-ttu-id="c7e40-190">例如，如果 *free_space* 百分比是 30，則使用的填滿因數就是 70。</span><span class="sxs-lookup"><span data-stu-id="c7e40-190">For example, if *free_space* percentage is 30, then the fill factor used is 70.</span></span> <span data-ttu-id="c7e40-191">如果將 *free_space* 百分比值指定為 100，則會使用原始的填滿因數值來重建索引。</span><span class="sxs-lookup"><span data-stu-id="c7e40-191">If a *free_space* percentage value of 100 is specified, then the indexes are rebuilt with the original fill factor value.</span></span>  
  
 <span data-ttu-id="c7e40-192">如果索引位於計算資料行上，當您使用 **-RebldIdx** 時，也必須指定 **-SupportComputedColumn**引數。</span><span class="sxs-lookup"><span data-stu-id="c7e40-192">If the indexes are on computed columns, you must also specify the **-SupportComputedColumn** argument when you use **-RebldIdx**.</span></span>  
  
 <span data-ttu-id="c7e40-193">**-RebldIdx**</span><span class="sxs-lookup"><span data-stu-id="c7e40-193">**-SupportComputedColumn**</span></span>  
 <span data-ttu-id="c7e40-194">必須指定此引數，才能在計算資料行上，利用 **sqlmaint** 來執行 DBCC 維護命令。</span><span class="sxs-lookup"><span data-stu-id="c7e40-194">Must be specified to run DBCC maintenance commands with **sqlmaint** on computed columns.</span></span>  
  
 <span data-ttu-id="c7e40-195">**-WriteHistory**</span><span class="sxs-lookup"><span data-stu-id="c7e40-195">**-WriteHistory**</span></span>  
 <span data-ttu-id="c7e40-196">指定在 msdb.dbo.sysdbmaintplan_history 中， **sqlmaint**所執行的每個維護動作都要建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="c7e40-196">Specifies that an entry be made in msdb.dbo.sysdbmaintplan_history for each maintenance action performed by **sqlmaint**.</span></span> <span data-ttu-id="c7e40-197">如果指定了 **-PlanName** 或 **-PlanID** ，sysdbmaintplan_history 中的項目便會使用指定計畫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c7e40-197">If **-PlanName** or **-PlanID** is specified, the entries in sysdbmaintplan_history use the ID of the specified plan.</span></span> <span data-ttu-id="c7e40-198">如果指定了 **-D** ，就會用幾個零做為計畫識別碼來建立 sysdbmaintplan_history 中的項目。</span><span class="sxs-lookup"><span data-stu-id="c7e40-198">If **-D** is specified, the entries in sysdbmaintplan_history are made with zeroes for the plan ID.</span></span>  
  
 <span data-ttu-id="c7e40-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span><span class="sxs-lookup"><span data-stu-id="c7e40-199">**-BkUpDB** [ *backup_path*] |  **-BkUpLog** [ *backup_path* ]</span></span>  
 <span data-ttu-id="c7e40-200">指定備份動作。</span><span class="sxs-lookup"><span data-stu-id="c7e40-200">Specifies a backup action.</span></span> <span data-ttu-id="c7e40-201">**-BkUpDb** 會備份整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7e40-201">**-BkUpDb** backs up the entire database.</span></span> <span data-ttu-id="c7e40-202">**-BkUpLog** 只會備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="c7e40-202">**-BkUpLog** backs up only the transaction log.</span></span>  
  
 <span data-ttu-id="c7e40-203">*backup_path* 會指定備份目錄。</span><span class="sxs-lookup"><span data-stu-id="c7e40-203">*backup_path* specifies the directory for the backup.</span></span> <span data-ttu-id="c7e40-204">如果也指定了*backup_path* ，便不需要 **backup_path** ，如果同時指定這兩者， **backup_path** 就會覆寫 backup_path。</span><span class="sxs-lookup"><span data-stu-id="c7e40-204">*backup_path* is not needed if **-UseDefDir** is also specified, and is overridden by **-UseDefDir** if both are specified.</span></span> <span data-ttu-id="c7e40-205">備份可以放在目錄或磁帶裝置位址 (例如 \\\\.\TAPE0) 中。</span><span class="sxs-lookup"><span data-stu-id="c7e40-205">The backup can be placed in a directory or a tape device address (for example, \\\\.\TAPE0).</span></span> <span data-ttu-id="c7e40-206">資料庫備份的檔案名稱會依照下列方式自動產生：</span><span class="sxs-lookup"><span data-stu-id="c7e40-206">The file name for a database backup is generated automatically as follows:</span></span>  
  
```  
dbname_db_yyyyMMddhhmm.BAK  
  
```  
  
 <span data-ttu-id="c7e40-207">其中</span><span class="sxs-lookup"><span data-stu-id="c7e40-207">where</span></span>  
  
-   <span data-ttu-id="c7e40-208">*dbname* 是正在備份的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c7e40-208">*dbname* is the name of the database being backed up.</span></span>  
  
-   <span data-ttu-id="c7e40-209">*yyyyMMddhhmm* 是備份作業的時間， *yyyy* = 年、 *MM* = 月、 *dd* = 日、 *hh* = 時，以及 *mm* = 分。</span><span class="sxs-lookup"><span data-stu-id="c7e40-209">*yyyyMMddhhmm* is the time of the backup operation with *yyyy* = year, *MM* = month, *dd* = day, *hh* = hour, and *mm* = minute.</span></span>  
  
 <span data-ttu-id="c7e40-210">交易備份的檔案名稱也會利用類似的格式自動產生：</span><span class="sxs-lookup"><span data-stu-id="c7e40-210">The file name for a transaction backup is generated automatically with a similar format:</span></span>  
  
```  
dbname_log_yyyymmddhhmm.BAK  
  
```  
  
 <span data-ttu-id="c7e40-211">如果您使用 **-BkUpDB** 參數，也必須使用 **-BkUpMedia** 參數來指定媒體。</span><span class="sxs-lookup"><span data-stu-id="c7e40-211">If you use the **-BkUpDB** parameter, you must also specify the media by using the **-BkUpMedia** parameter.</span></span>  
  
 <span data-ttu-id="c7e40-212">**-BkUpMedia**</span><span class="sxs-lookup"><span data-stu-id="c7e40-212">**-BkUpMedia**</span></span>  
 <span data-ttu-id="c7e40-213">指定備份的媒體類型為 DISK 或 TAPE。</span><span class="sxs-lookup"><span data-stu-id="c7e40-213">Specifies the media type of the backup, either DISK or TAPE.</span></span>  
  
 <span data-ttu-id="c7e40-214">**DISK**</span><span class="sxs-lookup"><span data-stu-id="c7e40-214">**DISK**</span></span>  
 <span data-ttu-id="c7e40-215">指定備份媒體是磁碟。</span><span class="sxs-lookup"><span data-stu-id="c7e40-215">Specifies that the backup medium is disk.</span></span>  
  
 <span data-ttu-id="c7e40-216">**-DelBkUps**\< *time_period* ></span><span class="sxs-lookup"><span data-stu-id="c7e40-216">**-DelBkUps**\< *time_period* ></span></span>  
 <span data-ttu-id="c7e40-217">針對磁碟備份，指定如果建立備份之後的時間間隔超出 \<*time_period*>，便會刪除備份目錄中的任何備份檔案。</span><span class="sxs-lookup"><span data-stu-id="c7e40-217">For disk backups, specifies that any backup file in the backup directory be deleted if the time interval after the creation of the backup exceeds the \<*time_period*>.</span></span>  
  
 <span data-ttu-id="c7e40-218">**-CrBkSubDir**</span><span class="sxs-lookup"><span data-stu-id="c7e40-218">**-CrBkSubDir**</span></span>  
 <span data-ttu-id="c7e40-219">對於磁碟備份，指定如果也指定了 *-UseDefDir*，便會在 [ **backup_path** ] 目錄或預設備份目錄中建立一個子目錄。</span><span class="sxs-lookup"><span data-stu-id="c7e40-219">For disk backups, specifies that a subdirectory be created in the [*backup_path*] directory or in the default backup directory if **-UseDefDir** is also specified.</span></span> <span data-ttu-id="c7e40-220">子目錄的名稱是從 **-D**指定的資料庫名稱所產生。</span><span class="sxs-lookup"><span data-stu-id="c7e40-220">The name of the subdirectory is generated from the database name specified in **-D**.</span></span> <span data-ttu-id="c7e40-221">**-CrBkSubDir** 提供一種簡單的方式，讓您不需要變更 *backup_path* 參數，就能將不同資料庫的所有備份放在個別子目錄中。</span><span class="sxs-lookup"><span data-stu-id="c7e40-221">**-CrBkSubDir** offers an easy way to put all the backups for different databases into separate subdirectories without having to change the *backup_path* parameter.</span></span>  
  
 <span data-ttu-id="c7e40-222">**backup_path**</span><span class="sxs-lookup"><span data-stu-id="c7e40-222">**-UseDefDir**</span></span>  
 <span data-ttu-id="c7e40-223">對於磁碟備份，指定在預設備份目錄中建立備份檔。</span><span class="sxs-lookup"><span data-stu-id="c7e40-223">For disk backups, specifies that the backup file be created in the default backup directory.</span></span> <span data-ttu-id="c7e40-224">如果同時指定這兩者，則**UseDefDir** 會覆寫 *backup_path* 。</span><span class="sxs-lookup"><span data-stu-id="c7e40-224">**UseDefDir** overrides *backup_path* if both are specified.</span></span> <span data-ttu-id="c7e40-225">當採用預設的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝時，預設備份目錄是 C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup。</span><span class="sxs-lookup"><span data-stu-id="c7e40-225">With a default [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] setup, the default backup directory is C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\Backup.</span></span>  
  
 <span data-ttu-id="c7e40-226">**TAPE**</span><span class="sxs-lookup"><span data-stu-id="c7e40-226">**TAPE**</span></span>  
 <span data-ttu-id="c7e40-227">指定備份媒體是磁帶。</span><span class="sxs-lookup"><span data-stu-id="c7e40-227">Specifies that the backup medium is tape.</span></span>  
  
 <span data-ttu-id="c7e40-228">**-BkUpOnlyIfClean**</span><span class="sxs-lookup"><span data-stu-id="c7e40-228">**-BkUpOnlyIfClean**</span></span>  
 <span data-ttu-id="c7e40-229">指定只有在任何指定的 **-Ck** 檢查確定資料都沒問題時，才會進行備份。</span><span class="sxs-lookup"><span data-stu-id="c7e40-229">Specifies that the backup occur only if any specified **-Ck** checks did not find problems with the data.</span></span> <span data-ttu-id="c7e40-230">維護動作會依照它們在命令提示字元下所呈現的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="c7e40-230">Maintenance actions run in the same sequence as they appear in the command prompt.</span></span> <span data-ttu-id="c7e40-231">如果您還要指定 **-BkUpOnlyIfClean**，或者不論檢查是否報告問題都要執行備份，可在 **-BkUpDB**-BkUpLog **參數之前指定**-CkDB **、** -CkDBNoIdx **、** -CkAl **、** -CkAlNoIdx **、** / **-CkTxtAl** 或 **-CkCat**參數。</span><span class="sxs-lookup"><span data-stu-id="c7e40-231">Specify the parameters **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** before the **-BkUpDB**/**-BkUpLog** parameter(s) if you are also going to specify **-BkUpOnlyIfClean**, or the backup occurs whether or not the check reports problems.</span></span>  
  
 <span data-ttu-id="c7e40-232">**-VrfyBackup**</span><span class="sxs-lookup"><span data-stu-id="c7e40-232">**-VrfyBackup**</span></span>  
 <span data-ttu-id="c7e40-233">指定在備份完成時執行 RESTORE VERIFYONLY。</span><span class="sxs-lookup"><span data-stu-id="c7e40-233">Specifies that RESTORE VERIFYONLY be run on the backup when it completes.</span></span>  
  
 <span data-ttu-id="c7e40-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span><span class="sxs-lookup"><span data-stu-id="c7e40-234">*number*[**minutes**| **hours**| **day**| **weeks**| **months**]</span></span>  
 <span data-ttu-id="c7e40-235">指定一個時間間隔來決定報表或備份檔經過多久時間之後便可刪除。</span><span class="sxs-lookup"><span data-stu-id="c7e40-235">Specifies the time interval used to determine if a report or backup file is old enough to be deleted.</span></span> <span data-ttu-id="c7e40-236">*number* 是後面接著時間單位的一個整數 (不含空格)。</span><span class="sxs-lookup"><span data-stu-id="c7e40-236">*number* is an integer followed (without a space) by a unit of time.</span></span> <span data-ttu-id="c7e40-237">有效範例：</span><span class="sxs-lookup"><span data-stu-id="c7e40-237">Valid examples:</span></span>  
  
-   <span data-ttu-id="c7e40-238">**12weeks**</span><span class="sxs-lookup"><span data-stu-id="c7e40-238">**12weeks**</span></span>  
  
-   <span data-ttu-id="c7e40-239">**3months**</span><span class="sxs-lookup"><span data-stu-id="c7e40-239">**3months**</span></span>  
  
-   <span data-ttu-id="c7e40-240">**15days**</span><span class="sxs-lookup"><span data-stu-id="c7e40-240">**15days**</span></span>  
  
 <span data-ttu-id="c7e40-241">如果只指定 *number* ，預設的日期部分是 **weeks**。</span><span class="sxs-lookup"><span data-stu-id="c7e40-241">If only *number* is specified, the default date part is **weeks**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7e40-242">備註</span><span class="sxs-lookup"><span data-stu-id="c7e40-242">Remarks</span></span>  
 <span data-ttu-id="c7e40-243">**sqlmaint** 公用程式會在一或多個資料庫上執行維護作業。</span><span class="sxs-lookup"><span data-stu-id="c7e40-243">The **sqlmaint** utility performs maintenance operations on one or more databases.</span></span> <span data-ttu-id="c7e40-244">如果指定了 **-D** ，就只會在指定的資料庫上執行其餘參數所指定的作業。</span><span class="sxs-lookup"><span data-stu-id="c7e40-244">If **-D** is specified, the operations specified in the remaining switches are performed only on the specified database.</span></span> <span data-ttu-id="c7e40-245">如果指定了 **-PlanName** 或 **-PlanID** ， **sqlmaint** 從指定的維護計畫中擷取的唯一資訊就是計畫中的資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="c7e40-245">If **-PlanName** or **-PlanID** are specified, the only information **sqlmaint** retrieves from the specified maintenance plan is the list of databases in the plan.</span></span> <span data-ttu-id="c7e40-246">從計畫中取得的清單所列出的每個資料庫，都會套用其餘 **sqlmaint** 參數所指定的所有作業。</span><span class="sxs-lookup"><span data-stu-id="c7e40-246">All operations specified in the remaining **sqlmaint** parameters are applied against each database in the list obtained from the plan.</span></span> <span data-ttu-id="c7e40-247">**sqlmaint** 公用程式不會套用計畫本身所定義的任何維護活動。</span><span class="sxs-lookup"><span data-stu-id="c7e40-247">The **sqlmaint** utility does not apply any of the maintenance activities defined in the plan itself.</span></span>  
  
 <span data-ttu-id="c7e40-248">如果 **sqlmaint** 公用程式順利執行，就會傳回 0，如果失敗，則傳回 1。</span><span class="sxs-lookup"><span data-stu-id="c7e40-248">The **sqlmaint** utility returns 0 if it runs successfully or 1 if it fails.</span></span> <span data-ttu-id="c7e40-249">在下列情況下，會發出失敗報告：</span><span class="sxs-lookup"><span data-stu-id="c7e40-249">Failure is reported:</span></span>  
  
-   <span data-ttu-id="c7e40-250">如果任何維護動作失敗。</span><span class="sxs-lookup"><span data-stu-id="c7e40-250">If any of the maintenance actions fail.</span></span>  
  
-   <span data-ttu-id="c7e40-251">如果 **-CkDB**、 **-CkDBNoIdx**、 **-CkAl**、 **-CkAlNoIdx**、 **-CkTxtAl**或 **-CkCat** 檢查發現資料發生問題。</span><span class="sxs-lookup"><span data-stu-id="c7e40-251">If **-CkDB**, **-CkDBNoIdx**, **-CkAl**, **-CkAlNoIdx**, **-CkTxtAl**, or **-CkCat** checks find problems with the data.</span></span>  
  
-   <span data-ttu-id="c7e40-252">如果發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="c7e40-252">If a general failure is encountered.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c7e40-253">權限</span><span class="sxs-lookup"><span data-stu-id="c7e40-253">Permissions</span></span>  
 <span data-ttu-id="c7e40-254">**sqlmaint** 公用程式可以由任何對於 **具有** 讀取和執行 `sqlmaint.exe`權限的 Windows 使用者執行，依預設，其會儲存於 `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="c7e40-254">The **sqlmaint** utility can be executed by any Windows user with **Read and Execute** permission on `sqlmaint.exe`, which by default is stored in the `x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER1\MSSQL\Binn` folder.</span></span> <span data-ttu-id="c7e40-255">另外，以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -login_ID **指定的** 登入必須擁有執行指定動作的必要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 權限。</span><span class="sxs-lookup"><span data-stu-id="c7e40-255">Additionally, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login specified with **-login_ID** must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span> <span data-ttu-id="c7e40-256">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的連接是使用 Windows 驗證，則對應到已驗證之 Windows 使用者的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入必須有執行指定動作的必要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 權限。</span><span class="sxs-lookup"><span data-stu-id="c7e40-256">If the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses Windows Authentication, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login mapped to the authenticated Windows user must have the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] permissions required to perform the specified action.</span></span>  
  
 <span data-ttu-id="c7e40-257">例如，使用 **-BkUpDB** 需要有執行 BACKUP 陳述式的權限。</span><span class="sxs-lookup"><span data-stu-id="c7e40-257">For example, using the **-BkUpDB** requires permission to execute the BACKUP statement.</span></span> <span data-ttu-id="c7e40-258">使用 **-UpdOptiStats** 引數需要有執行 UPDATE STATISTICS 陳述式的權限。</span><span class="sxs-lookup"><span data-stu-id="c7e40-258">And using the **-UpdOptiStats** argument requires permission to execute the UPDATE STATISTICS statement.</span></span> <span data-ttu-id="c7e40-259">如需詳細資訊，請參閱線上叢書中對應主題的＜權限＞章節。</span><span class="sxs-lookup"><span data-stu-id="c7e40-259">For more information, see the "Permissions" sections of the corresponding topics in Books Online.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c7e40-260">範例</span><span class="sxs-lookup"><span data-stu-id="c7e40-260">Examples</span></span>  
  
### <a name="a-performing-dbcc-checks-on-a-database"></a><span data-ttu-id="c7e40-261">A.</span><span class="sxs-lookup"><span data-stu-id="c7e40-261">A.</span></span> <span data-ttu-id="c7e40-262">在資料庫中執行 DBCC 檢查</span><span class="sxs-lookup"><span data-stu-id="c7e40-262">Performing DBCC checks on a database</span></span>  
  
```  
sqlmaint -S MyServer -D AdventureWorks2012 -CkDB -CkAl -CkCat -Rpt C:\MyReports\AdvWks_chk.rpt  
```  
  
### <a name="b-updating-statistics-using-a-15-sample-in-all-databases-in-a-plan-also-shrink-any-of-the-database-that-have-reached-110-mb-to-having-only-10-free-space"></a><span data-ttu-id="c7e40-263">B.</span><span class="sxs-lookup"><span data-stu-id="c7e40-263">B.</span></span> <span data-ttu-id="c7e40-264">在計畫的所有資料庫中，利用 15% 取樣來更新統計資料。</span><span class="sxs-lookup"><span data-stu-id="c7e40-264">Updating statistics using a 15% sample in all databases in a plan.</span></span> <span data-ttu-id="c7e40-265">另外，將到達 110 MB 的任何資料庫壓縮成只有 10% 的可用空間</span><span class="sxs-lookup"><span data-stu-id="c7e40-265">Also, shrink any of the database that have reached 110 MB to having only 10% free space</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -UpdOptiStats 15 -RmUnusedSpace 110 10  
```  
  
### <a name="c-backing-up-all-the-databases-in-a-plan-to-their-individual-subdirectories-in-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory-also-delete-any-backups-older-than-2-weeks"></a><span data-ttu-id="c7e40-266">C.</span><span class="sxs-lookup"><span data-stu-id="c7e40-266">C.</span></span> <span data-ttu-id="c7e40-267">在預設的 x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup 目錄中，將計畫中的所有資料庫分別備份在它們的個別子目錄中。</span><span class="sxs-lookup"><span data-stu-id="c7e40-267">Backing up all the databases in a plan to their individual subdirectories in the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span> <span data-ttu-id="c7e40-268">另外，如果備份比 2 星期還要舊，便予以刪除</span><span class="sxs-lookup"><span data-stu-id="c7e40-268">Also, delete any backups older than 2 weeks</span></span>  
  
```  
sqlmaint -S MyServer -PlanName MyUserDBPlan -BkUpDB -BkUpMedia DISK -UseDefDir -CrBkSubDir -DelBkUps 2weeks  
```  
  
### <a name="d-backing-up-a-database-to-the-default-xprogram-filesmicrosoft-sql-servermssql12mssqlservermssqlbackup-directory"></a><span data-ttu-id="c7e40-269">D.</span><span class="sxs-lookup"><span data-stu-id="c7e40-269">D.</span></span> <span data-ttu-id="c7e40-270">將資料庫備份至預設的 x:\Program Files\Microsoft SQL Server\MSSQL12。MSSQLSERVER\MSSQL\Backup 目錄。 </span><span class="sxs-lookup"><span data-stu-id="c7e40-270">Backing up a database to the default x:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup directory.</span></span>\  
  
```  
sqlmaint -S MyServer -BkUpDB -BkUpMedia DISK -UseDefDir  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7e40-271">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7e40-271">See Also</span></span>  
 <span data-ttu-id="c7e40-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c7e40-272">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="c7e40-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7e40-273">UPDATE STATISTICS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/update-statistics-transact-sql)  
  
  
