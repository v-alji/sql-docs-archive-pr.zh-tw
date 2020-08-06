---
title: SQLdiag 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], SQLdiag
- stopping diagnostic collection
- storing diagnostic information
- performance [SQL Server], diagnostic collection
- diagnostic records [SQL Server]
- scripts [SQL Server], diagnostic collection
- logs [SQL Server], diagnostic collection
- starting diagnostic collection
- clustered instance of SQL Server
- monitoring performance [SQL Server], diagnostic collection
- security [SQL Server], diagnostic collection
- SQLDIAG service
- space [SQL Server], diagnostic collection
- SQLdiag utility
- disk space [SQL Server], diagnostic collection
- configuration files [SQL Server]
- automatic diagnostic collection
- clusters [SQL Server], diagnostic collection
ms.assetid: 45ba1307-33d1-431e-872c-a6e4556f5ff2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0559e0b2261ed5ba1c9c384608d04194d685f695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686586"
---
# <a name="sqldiag-utility"></a><span data-ttu-id="6f446-102">SQLdiag 公用程式</span><span class="sxs-lookup"><span data-stu-id="6f446-102">SQLdiag Utility</span></span>
  <span data-ttu-id="6f446-103">**SQLdiag** 公用程式是一種可當做主控台應用程式或服務加以執行的一般用途診斷集合公用程式。</span><span class="sxs-lookup"><span data-stu-id="6f446-103">The **SQLdiag** utility is a general purpose diagnostics collection utility that can be run as a console application or as a service.</span></span> <span data-ttu-id="6f446-104">您可以使用 **SQLdiag** ，從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 和其他類型的伺服器收集記錄檔案和資料檔案，並使用其監視一段時間的伺服器，或對伺服器的特定問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="6f446-104">You can use **SQLdiag** to collect logs and data files from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="6f446-105">**SQLdiag** 的用途是為了加速及簡化 [!INCLUDE[msCoName](../includes/msconame-md.md)] 客戶支援服務的診斷資訊收集工作。</span><span class="sxs-lookup"><span data-stu-id="6f446-105">**SQLdiag** is intended to expedite and simplify diagnostic information gathering for [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-106">此公用程式可能會變更，而且依賴其命令列引數或行為的應用程式或指令碼，在未來版本中可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="6f446-106">This utility may be changed, and applications or scripts that rely on its command line arguments or behavior may not work correctly in future releases.</span></span>  
  
 <span data-ttu-id="6f446-107">**SQLdiag** 可以收集下列類型的診斷資訊：</span><span class="sxs-lookup"><span data-stu-id="6f446-107">**SQLdiag** can collect the following types of diagnostic information:</span></span>  
  
-   <span data-ttu-id="6f446-108">Windows 效能記錄</span><span class="sxs-lookup"><span data-stu-id="6f446-108">Windows performance logs</span></span>  
  
-   <span data-ttu-id="6f446-109">Windows 事件記錄</span><span class="sxs-lookup"><span data-stu-id="6f446-109">Windows event logs</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="6f446-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="6f446-110">traces</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6f446-111">封鎖資訊</span><span class="sxs-lookup"><span data-stu-id="6f446-111">blocking information</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="6f446-112">組態資訊</span><span class="sxs-lookup"><span data-stu-id="6f446-112">configuration information</span></span>  
  
 <span data-ttu-id="6f446-113">您可以編輯組態檔 SQLDiag.xml，指定您希望 **SQLdiag** 收集的資訊類型，後續的章節會有相關說明。</span><span class="sxs-lookup"><span data-stu-id="6f446-113">You can specify what types of information you want **SQLdiag** to collect by editing the configuration file SQLDiag.xml, which is described in a following section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f446-114">語法</span><span class="sxs-lookup"><span data-stu-id="6f446-114">Syntax</span></span>  
  
```  
  
      sqldiag   
     { [/?] }  
     |  
     { [/I configuration_file]  
       [/O output_folder_path]  
       [/Psupport_folder_path]  
       [/Noutput_folder_management_option]  
       [/Mmachine1 [ machine2machineN]| @machinelistfile]  
       [/Cfile_compression_type]  
       [/B [+]start_time]  
       [/E [+]stop_time]  
       [/ASQLdiag_application_name]  
       [/T { tcp [ ,port ] | np | lpc } ]  
       [/Q] [/G] [/R] [/U] [/L] [/X] }  
     |  
     { [START | STOP | STOP_ABORT] }  
     |  
     { [START | STOP | STOP_ABORT] /ASQLdiag_application_name }  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f446-115">引數</span><span class="sxs-lookup"><span data-stu-id="6f446-115">Arguments</span></span>  
 <span data-ttu-id="6f446-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="6f446-116">**/?**</span></span>  
 <span data-ttu-id="6f446-117">顯示使用資訊。</span><span class="sxs-lookup"><span data-stu-id="6f446-117">Displays usage information.</span></span>  
  
 <span data-ttu-id="6f446-118">**/I** _configuration_file_</span><span class="sxs-lookup"><span data-stu-id="6f446-118">**/I** _configuration_file_</span></span>  
 <span data-ttu-id="6f446-119">設定 **SQLdiag** 要使用的組態檔。</span><span class="sxs-lookup"><span data-stu-id="6f446-119">Sets the configuration file for **SQLdiag** to use.</span></span> <span data-ttu-id="6f446-120">依預設， **/I** 會設為 SQLDiag.Xml。</span><span class="sxs-lookup"><span data-stu-id="6f446-120">By default, **/I** is set to SQLDiag.Xml.</span></span>  
  
 <span data-ttu-id="6f446-121">**/O** _output_folder_path_</span><span class="sxs-lookup"><span data-stu-id="6f446-121">**/O** _output_folder_path_</span></span>  
 <span data-ttu-id="6f446-122">將 **SQLdiag** 輸出重新導向至指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-122">Redirects **SQLdiag** output to the specified folder.</span></span> <span data-ttu-id="6f446-123">如果未指定 **/O** 選項， **SQLdiag** 輸出會寫入 **SQLdiag** 啟動資料夾之下名稱為 SQLDIAG 的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6f446-123">If the **/O** option is not specified, **SQLdiag** output is written to a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="6f446-124">如果 [SQLDIAG] 資料夾不存在， **SQLdiag** 會嘗試建立它。</span><span class="sxs-lookup"><span data-stu-id="6f446-124">If the SQLDIAG folder does not exist, **SQLdiag** attempts to create it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-125">輸出資料夾位置相對於可以使用 **/P**指定的支援資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="6f446-125">The output folder location is relative to the support folder location that can be specified with **/P**.</span></span> <span data-ttu-id="6f446-126">若要為輸出資料夾設定完全不同的位置，請對 **/O**指定完整的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="6f446-126">To set an entirely different location for the output folder, specify the full directory path for **/O**.</span></span>  
  
 <span data-ttu-id="6f446-127">**/P** _support_folder_path_</span><span class="sxs-lookup"><span data-stu-id="6f446-127">**/P** _support_folder_path_</span></span>  
 <span data-ttu-id="6f446-128">設定支援資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="6f446-128">Sets the support folder path.</span></span> <span data-ttu-id="6f446-129">依預設， **/P** 會設為 **SQLdiag** 可執行檔所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-129">By default, **/P** is set to the folder where the **SQLdiag** executable resides.</span></span> <span data-ttu-id="6f446-130">此支援資料夾包含 **SQLdiag** 支援檔案，例如 XML 組態檔、Transact-SQL 指令碼與公用程式在診斷收集期間所使用的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="6f446-130">The support folder contains **SQLdiag** support files, such as the XML configuration file, Transact-SQL scripts, and other files that the utility uses during diagnostics collection.</span></span> <span data-ttu-id="6f446-131">如果您使用此選項指定替代支援檔案路徑， **SQLdiag** 會將它需要的支援檔案自動複製到指定的資料夾 (如果它們尚不存在)。</span><span class="sxs-lookup"><span data-stu-id="6f446-131">If you use this option to specify an alternate support files path, **SQLdiag** will automatically copy the support files it requires to the specified folder if they do not already exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-132">若要將目前資料夾設為支援路徑，請在命令列上指定 **%cd%** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f446-132">To set your current folder as the support path, specify **%cd%** on the command line as follows:</span></span>  
>   
>  <span data-ttu-id="6f446-133">**SQLDIAG /P %cd%**</span><span class="sxs-lookup"><span data-stu-id="6f446-133">**SQLDIAG /P %cd%**</span></span>  
  
 <span data-ttu-id="6f446-134">**/N** _output_folder_management_option_</span><span class="sxs-lookup"><span data-stu-id="6f446-134">**/N** _output_folder_management_option_</span></span>  
 <span data-ttu-id="6f446-135">設定 **SQLdiag** 在啟動時，是要覆寫或重新命名輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-135">Sets whether **SQLdiag** overwrites or renames the output folder when it starts up.</span></span> <span data-ttu-id="6f446-136">可用選項：</span><span class="sxs-lookup"><span data-stu-id="6f446-136">Available options:</span></span>  
  
 <span data-ttu-id="6f446-137">1 = 覆寫輸出資料夾 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6f446-137">1 = Overwrites the output folder (default)</span></span>  
  
 <span data-ttu-id="6f446-138">2 = 當 **SQLdiag** 啟動時，它會將輸出資料夾重新命名為 SQLDIAG_00001、SQLDIAG_00002 等。</span><span class="sxs-lookup"><span data-stu-id="6f446-138">2 = When **SQLdiag** starts up, it renames the output folder to SQLDIAG_00001, SQLDIAG_00002, and so on.</span></span> <span data-ttu-id="6f446-139">在重新命名目前的輸出資料夾之後， **SQLdiag** 會將輸出寫入預設輸出資料夾 SQLDIAG 中。</span><span class="sxs-lookup"><span data-stu-id="6f446-139">After renaming the current output folder, **SQLdiag** writes output to the default output folder SQLDIAG.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-140">**SQLdiag** 在啟動時不會將輸出附加至目前的輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-140">**SQLdiag** does not append output to the current output folder when it starts up.</span></span> <span data-ttu-id="6f446-141">它只能覆寫預設輸出資料夾 (選項 1)，或重新命名資料夾 (選項 2)，然後將輸出寫入新的預設輸出資料夾 SQLDIAG 中。</span><span class="sxs-lookup"><span data-stu-id="6f446-141">It can only overwrite the default output folder (option 1) or rename the folder (option 2), and then it writes output to the new default output folder named SQLDIAG.</span></span>  
  
 <span data-ttu-id="6f446-142">**/M** _machine1_ [ *machine2 \* \* machineN*] |*@machinelistfile*</span><span class="sxs-lookup"><span data-stu-id="6f446-142">**/M** _machine1_ [ *machine2\*\*machineN*] | *@machinelistfile*</span></span>  
 <span data-ttu-id="6f446-143">覆寫組態檔中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="6f446-143">Overrides the machines specified in the configuration file.</span></span> <span data-ttu-id="6f446-144">依預設，組態檔是 SQLDiag.Xml，或是以 **/I** 參數來設定。</span><span class="sxs-lookup"><span data-stu-id="6f446-144">By default the configuration file is SQLDiag.Xml, or is set with the **/I** parameter.</span></span> <span data-ttu-id="6f446-145">當指定一部以上的電腦時，請用空格隔開每一個電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-145">When specifying more than one machine, separate each machine name with a space.</span></span>  
  
 <span data-ttu-id="6f446-146">使用 *@machinelistfile* 指定要儲存在設定檔中的電腦清單檔案名。</span><span class="sxs-lookup"><span data-stu-id="6f446-146">Using *@machinelistfile* specifies a machine list filename to be stored in the configuration file.</span></span>  
  
 <span data-ttu-id="6f446-147">**/C** _file_compression_type_</span><span class="sxs-lookup"><span data-stu-id="6f446-147">**/C** _file_compression_type_</span></span>  
 <span data-ttu-id="6f446-148">設定 **SQLdiag** 輸出資料夾檔案所用的檔案壓縮類型。</span><span class="sxs-lookup"><span data-stu-id="6f446-148">Sets the type of file compression used on the **SQLdiag** output folder files.</span></span> <span data-ttu-id="6f446-149">可用選項：</span><span class="sxs-lookup"><span data-stu-id="6f446-149">Available options:</span></span>  
  
 <span data-ttu-id="6f446-150">0 = 無 (預設值)</span><span class="sxs-lookup"><span data-stu-id="6f446-150">0 = none (default)</span></span>  
  
 <span data-ttu-id="6f446-151">1 = 使用 NTFS 壓縮</span><span class="sxs-lookup"><span data-stu-id="6f446-151">1 = uses NTFS compression</span></span>  
  
 <span data-ttu-id="6f446-152">**/B** [ **+** ]*start_time*</span><span class="sxs-lookup"><span data-stu-id="6f446-152">**/B** [**+**]*start_time*</span></span>  
 <span data-ttu-id="6f446-153">依照下列格式來指定開始收集診斷資料的日期和時間：</span><span class="sxs-lookup"><span data-stu-id="6f446-153">Specifies the date and time to start collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="6f446-154">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="6f446-154">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="6f446-155">時間使用 24 小時標記法指定。</span><span class="sxs-lookup"><span data-stu-id="6f446-155">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="6f446-156">例如，下午 2:00</span><span class="sxs-lookup"><span data-stu-id="6f446-156">For example, 2:00 P.M.</span></span> <span data-ttu-id="6f446-157">應該指定為 **14:00:00**。</span><span class="sxs-lookup"><span data-stu-id="6f446-157">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="6f446-158">請利用 **+** (不含日期 (只有 HH:MM:SS)) 來指定相對於目前日期和時間的時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-158">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="6f446-159">例如，如果您指定 **/B +02:00:00**， **SQLdiag** 會等候 2 小時，再開始收集資訊。</span><span class="sxs-lookup"><span data-stu-id="6f446-159">For example, if you specify **/B +02:00:00**, **SQLdiag** will wait 2 hours before it starts collecting information.</span></span>  
  
 <span data-ttu-id="6f446-160">請勿在 **+** 和指定的 *start_time*之間插入空格。</span><span class="sxs-lookup"><span data-stu-id="6f446-160">Do not insert a space between **+** and the specified *start_time*.</span></span>  
  
 <span data-ttu-id="6f446-161">如果您指定的開始時間已經過去， **SQLdiag** 會強制變更開始日期，使開始日期和時間設定在未來。</span><span class="sxs-lookup"><span data-stu-id="6f446-161">If you specify a start time that is in the past, **SQLdiag** forcibly changes the start date so the start date and time are in the future.</span></span> <span data-ttu-id="6f446-162">例如，如果您指定 **/B 01:00:00** ，且目前的時間是 08:00:00， **SQLdiag** 會強制變更開始日期，使開始日期設定在隔天。</span><span class="sxs-lookup"><span data-stu-id="6f446-162">For example, if you specify **/B 01:00:00** and the current time is 08:00:00, **SQLdiag** forcibly changes the start date so that the start date is the next day.</span></span>  
  
 <span data-ttu-id="6f446-163">請注意， **SQLdiag** 會使用執行公用程式之電腦的本機時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-163">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="6f446-164">**/E** [ **+** ]*stop_time*</span><span class="sxs-lookup"><span data-stu-id="6f446-164">**/E** [**+**]*stop_time*</span></span>  
 <span data-ttu-id="6f446-165">依照下列格式來指定停止收集診斷資料的日期和時間：</span><span class="sxs-lookup"><span data-stu-id="6f446-165">Specifies the date and time to stop collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="6f446-166">YYYYMMDD_HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="6f446-166">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="6f446-167">時間使用 24 小時標記法指定。</span><span class="sxs-lookup"><span data-stu-id="6f446-167">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="6f446-168">例如，下午 2:00</span><span class="sxs-lookup"><span data-stu-id="6f446-168">For example, 2:00 P.M.</span></span> <span data-ttu-id="6f446-169">應該指定為 **14:00:00**。</span><span class="sxs-lookup"><span data-stu-id="6f446-169">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="6f446-170">請利用 **+** (不含日期 (只有 HH:MM:SS)) 來指定相對於目前日期和時間的時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-170">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="6f446-171">例如，如果您利用 **/B +02:00:00 /E +03:00:00**來指定開始時間和結束時間， **SQLdiag** 會等候 2 小時再開始收集資訊，之後會收集 3 小時的資訊，再停止並結束。</span><span class="sxs-lookup"><span data-stu-id="6f446-171">For example, if you specify a start time and end time by using **/B +02:00:00 /E +03:00:00**, **SQLdiag** waits 2 hours before it starts collecting information, then collects information for 3 hours before it stops and exits.</span></span> <span data-ttu-id="6f446-172">如果未指定 **/B** ， **SQLdiag** 會立即開始收集診斷資訊，並會在 **/E**所指定的日期和時間結束。</span><span class="sxs-lookup"><span data-stu-id="6f446-172">If **/B** is not specified, **SQLdiag** starts collecting diagnostics immediately and ends at the date and time specified by **/E**.</span></span>  
  
 <span data-ttu-id="6f446-173">請勿在 **+** 和指定的 *start_time* 或 *end_time*之間插入空格。</span><span class="sxs-lookup"><span data-stu-id="6f446-173">Do not insert a space between **+** and the specified *start_time* or *end_time*.</span></span>  
  
 <span data-ttu-id="6f446-174">請注意， **SQLdiag** 會使用執行公用程式之電腦的本機時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-174">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="6f446-175">**/A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="6f446-175">**/A** _SQLdiag_application_name_</span></span>  
 <span data-ttu-id="6f446-176">使 **SQLdiag** 公用程式的多個執行個體可以針對相同的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體執行。</span><span class="sxs-lookup"><span data-stu-id="6f446-176">Enables running multiple instances of the **SQLdiag** utility against the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="6f446-177">每一個 *SQLdiag_application_name* 會識別一個不同的 **SQLdiag**執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f446-177">Each *SQLdiag_application_name* identifies a different instance of **SQLdiag**.</span></span> <span data-ttu-id="6f446-178">*SQLdiag_application_name* 執行個體和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體名稱之間沒有關聯性。</span><span class="sxs-lookup"><span data-stu-id="6f446-178">No relationship exists between a *SQLdiag_application_name* instance and a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="6f446-179">*SQLdiag_application_name* 可用來啟動或停止 **SQLdiag** 服務的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f446-179">*SQLdiag_application_name* can be used to start or stop a specific instance of the **SQLdiag** service.</span></span>  
  
 <span data-ttu-id="6f446-180">例如：</span><span class="sxs-lookup"><span data-stu-id="6f446-180">For example:</span></span>  
  
 <span data-ttu-id="6f446-181">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="6f446-181">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
 <span data-ttu-id="6f446-182">它也可以與 **/R** 選項一起使用，將 **SQLdiag** 的特定執行個體註冊為服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-182">It can also be used with the **/R** option to register a specific instance of **SQLdiag** as a service.</span></span> <span data-ttu-id="6f446-183">例如：</span><span class="sxs-lookup"><span data-stu-id="6f446-183">For example:</span></span>  
  
 <span data-ttu-id="6f446-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="6f446-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-185">**SQLdiag** 會自動將 DIAG$ 前置於為 *SQLdiag_application_name*所指定的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-185">**SQLdiag** automatically prefixes DIAG$ to the instance name specified for *SQLdiag_application_name*.</span></span> <span data-ttu-id="6f446-186">其可為在您將 **SQLdiag** 註冊成服務時，提供實用的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-186">This provides a sensible service name if you register **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="6f446-187">/T { tcp [ ,*port* ] | np | lpc }</span><span class="sxs-lookup"><span data-stu-id="6f446-187">/T { tcp [ ,*port* ] | np | lpc }</span></span>  
 <span data-ttu-id="6f446-188">使用指定的通訊協定連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f446-188">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the specified protocol.</span></span>  
  
 <span data-ttu-id="6f446-189">tcp [,*port*]</span><span class="sxs-lookup"><span data-stu-id="6f446-189">tcp [,*port*]</span></span>  
 <span data-ttu-id="6f446-190">傳輸控制通訊協定/網際網路通訊協定 (TCP/IP)。</span><span class="sxs-lookup"><span data-stu-id="6f446-190">Transmission Control Protocol/Internet Protocol (TCP/IP).</span></span> <span data-ttu-id="6f446-191">您可以選擇性地為此連接指定通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="6f446-191">You can optionally specify a port number for the connection.</span></span>  
  
 <span data-ttu-id="6f446-192">np</span><span class="sxs-lookup"><span data-stu-id="6f446-192">np</span></span>  
 <span data-ttu-id="6f446-193">具名管道。</span><span class="sxs-lookup"><span data-stu-id="6f446-193">Named pipes.</span></span> <span data-ttu-id="6f446-194">根據預設， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設執行個體會針對具名執行個體接聽具名管道 `\\.\pipe\sql\query` 和 `\\.\pipe\MSSQL$<instancename>\sql\query` 。</span><span class="sxs-lookup"><span data-stu-id="6f446-194">By default, the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listens on named pipe `\\.\pipe\sql\query` and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="6f446-195">您無法使用替代管道名稱來連接 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f446-195">You cannot connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using an alternate pipe name.</span></span>  
  
 <span data-ttu-id="6f446-196">lpc</span><span class="sxs-lookup"><span data-stu-id="6f446-196">lpc</span></span>  
 <span data-ttu-id="6f446-197">本機程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f446-197">Local procedure call.</span></span> <span data-ttu-id="6f446-198">如果用戶端連接到同一部電腦上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，也可以使用此共用的記憶體通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6f446-198">This shared memory protocol is available if the client is connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same computer.</span></span>  
  
 <span data-ttu-id="6f446-199">**/Q**</span><span class="sxs-lookup"><span data-stu-id="6f446-199">**/Q**</span></span>  
 <span data-ttu-id="6f446-200">以安靜模式執行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-200">Runs **SQLdiag** in quiet mode.</span></span> <span data-ttu-id="6f446-201">**/Q** 會抑制所有提示，如密碼提示。</span><span class="sxs-lookup"><span data-stu-id="6f446-201">**/Q** suppresses all prompts, such as password prompts.</span></span>  
  
 <span data-ttu-id="6f446-202">**/G**</span><span class="sxs-lookup"><span data-stu-id="6f446-202">**/G**</span></span>  
 <span data-ttu-id="6f446-203">以一般模式執行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-203">Runs **SQLdiag** in generic mode.</span></span> <span data-ttu-id="6f446-204">指定 **/G** 之後，在啟動時， **SQLdiag** 就不會強制執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 連線檢查，或確認使用者是否為 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6f446-204">When **/G** is specified, on startup **SQLdiag** does not enforce [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connectivity checks or verify that the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="6f446-205">但是， **SQLdiag** 會延遲 Windows 判斷使用者是否具有適當的權限，以收集各項要求的診斷。</span><span class="sxs-lookup"><span data-stu-id="6f446-205">Instead, **SQLdiag** defers to Windows to determine whether a user has the appropriate rights to gather each requested diagnostic.</span></span>  
  
 <span data-ttu-id="6f446-206">如果未指定 **/G** ， **SQLdiag** 會檢查並判斷使用者是否為 Windows **Administrator** 群組的成員，如果使用者不是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Administrator **群組成員，則不會收集** 診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="6f446-206">If **/G** is not specified, **SQLdiag** checks to determine whether the user is a member of the Windows **Administrators** group, and will not collect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] diagnostics if the user is not an **Administrators** group member.</span></span>  
  
 <span data-ttu-id="6f446-207">**/R**</span><span class="sxs-lookup"><span data-stu-id="6f446-207">**/R**</span></span>  
 <span data-ttu-id="6f446-208">將 **SQLdiag** 註冊為服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-208">Registers **SQLdiag** as a service.</span></span> <span data-ttu-id="6f446-209">您將 **SQLdiag** 註冊成服務時所指定的任何命令列引數都會保留下來，以便之後執行這項服務時使用。</span><span class="sxs-lookup"><span data-stu-id="6f446-209">Any command line arguments that are specified when you register **SQLdiag** as a service are preserved for future runs of the service.</span></span>  
  
 <span data-ttu-id="6f446-210">當 **SQLdiag** 註冊為服務時，預設服務名稱為 SQLDIAG。</span><span class="sxs-lookup"><span data-stu-id="6f446-210">When **SQLdiag** is registered as a service, the default service name is SQLDIAG.</span></span> <span data-ttu-id="6f446-211">您可以使用 **/A** 引數變更服務名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-211">You can change the service name by using the **/A** argument.</span></span>  
  
 <span data-ttu-id="6f446-212">使用 **START** 命令列引數來啟動服務：</span><span class="sxs-lookup"><span data-stu-id="6f446-212">Use the **START** command line argument to start the service:</span></span>  
  
 <span data-ttu-id="6f446-213">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="6f446-213">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="6f446-214">您也可以使用 **net start** 命令來啟動服務：</span><span class="sxs-lookup"><span data-stu-id="6f446-214">You can also use the **net start** command to start the service:</span></span>  
  
 <span data-ttu-id="6f446-215">**net start SQLDIAG**</span><span class="sxs-lookup"><span data-stu-id="6f446-215">**net start SQLDIAG**</span></span>  
  
 <span data-ttu-id="6f446-216">**/U**</span><span class="sxs-lookup"><span data-stu-id="6f446-216">**/U**</span></span>  
 <span data-ttu-id="6f446-217">將 **SQLdiag** 取消註冊為服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-217">Unregisters **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="6f446-218">若要取消註冊具名 **SQLdiag** 執行個體，也請使用 **/A** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-218">Use the **/A** argument also if unregistering a named **SQLdiag** instance.</span></span>  
  
 <span data-ttu-id="6f446-219">**/L**</span><span class="sxs-lookup"><span data-stu-id="6f446-219">**/L**</span></span>  
 <span data-ttu-id="6f446-220">若也分別以 **/B** 或 **/E** 引數指定開始時間或結束時間，請在連續模式下執行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-220">Runs **SQLdiag** in continuous mode when a start time or end time is also specified with the **/B** or **/E** arguments, respectively.</span></span> <span data-ttu-id="6f446-221">當因為排程關閉而停止收集診斷資訊之後，會自動重新啟動**SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-221">**SQLdiag** automatically restarts after diagnostics collection stops due to a scheduled shutdown.</span></span> <span data-ttu-id="6f446-222">例如，透過使用 **/E** 或 **/X** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-222">For example, by using the **/E** or the **/X** arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-223">如果開始時間或結束時間不是使用**SQLdiag** 和 **/L** 命令列引數指定，則 **SQLdiag** 會忽略 **/L** comm會忽略 line arguments.</span><span class="sxs-lookup"><span data-stu-id="6f446-223">**SQLdiag** ignores the **/L** argument if a start time or end time is not specified by using the **/B** and **/E** command line arguments.</span></span>  
  
 <span data-ttu-id="6f446-224">使用 **/L** 不代表服務模式。</span><span class="sxs-lookup"><span data-stu-id="6f446-224">Using **/L** does not imply the service mode.</span></span> <span data-ttu-id="6f446-225">將 **SQLdiag** 執行為服務時若要使用 **/L** ，請在註冊服務時於命令列上指定。</span><span class="sxs-lookup"><span data-stu-id="6f446-225">To use **/L** when running **SQLdiag** as a service, specify it on the command line when you register the service.</span></span>  
  
 <span data-ttu-id="6f446-226">**/X**</span><span class="sxs-lookup"><span data-stu-id="6f446-226">**/X**</span></span>  
 <span data-ttu-id="6f446-227">以快照集模式執行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-227">Runs **SQLdiag** in snapshot mode.</span></span> <span data-ttu-id="6f446-228">**SQLdiag** 會取得所有所設定之診斷資訊的快照，再自動關閉。</span><span class="sxs-lookup"><span data-stu-id="6f446-228">**SQLdiag** takes a snapshot of all configured diagnostics and then shuts down automatically.</span></span>  
  
 <span data-ttu-id="6f446-229">**START** | **STOP** | **STOP_ABORT**</span><span class="sxs-lookup"><span data-stu-id="6f446-229">**START** | **STOP** | **STOP_ABORT**</span></span>  
 <span data-ttu-id="6f446-230">啟動或停止 **SQLdiag** 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-230">Starts or stops the **SQLdiag** service.</span></span> <span data-ttu-id="6f446-231">**STOP_ABORT** 會在未完成它目前正在收集的診斷資訊收集工作的情況下，強制盡快關閉。</span><span class="sxs-lookup"><span data-stu-id="6f446-231">**STOP_ABORT** forces the service to shut down as quickly as possible without finishing collection of diagnostics it is currently collecting.</span></span>  
  
 <span data-ttu-id="6f446-232">使用這些服務控制引數時，它們必須是命令列所使用的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-232">When these service control arguments are used, they must be the first argument used on the command line.</span></span> <span data-ttu-id="6f446-233">例如：</span><span class="sxs-lookup"><span data-stu-id="6f446-233">For example:</span></span>  
  
 <span data-ttu-id="6f446-234">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="6f446-234">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="6f446-235">只有指定 **SQLdiag** 具名執行個體的 **/A**引數，才可以與 **START**、 **STOP**或 **STOP_ABORT** 一起使用，來控制 **SQLdiag** 服務的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f446-235">Only the **/A** argument, which specifies a named instance of **SQLdiag**, can be used with **START**, **STOP**, or **STOP_ABORT** to control a specific instance of the **SQLdiag** service.</span></span> <span data-ttu-id="6f446-236">例如：</span><span class="sxs-lookup"><span data-stu-id="6f446-236">For example:</span></span>  
  
 <span data-ttu-id="6f446-237">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="6f446-237">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
## <a name="security-requirements"></a><span data-ttu-id="6f446-238">安全性需求</span><span class="sxs-lookup"><span data-stu-id="6f446-238">Security Requirements</span></span>  
 <span data-ttu-id="6f446-239">除非 **SQLdiag** 於一般模式下執行 (藉由指定 **/G** 命令列引數)，否則執行 **SQLdiag** 的使用者必須是 Windows **Administrator** 群組成員，以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6f446-239">Unless **SQLdiag** is run in generic mode (by specifying the **/G** command line argument), the user who runs **SQLdiag** must be a member of the Windows **Administrators** group and a member of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** fixed server role.</span></span> <span data-ttu-id="6f446-240">依預設， **SQLdiag** 會使用 Windows 驗證來連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，但它也支援 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="6f446-240">By default, **SQLdiag** connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Windows Authentication, but it also supports [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="6f446-241">效能考量</span><span class="sxs-lookup"><span data-stu-id="6f446-241">Performance Considerations</span></span>  
 <span data-ttu-id="6f446-242">執行 **SQLdiag** 的效能結果，會隨著您設定它要收集的診斷資料類型而不同。</span><span class="sxs-lookup"><span data-stu-id="6f446-242">The performance effects of running **SQLdiag** depend on the type of diagnostic data you have configured it to collect.</span></span> <span data-ttu-id="6f446-243">例如，如果您已設定 **SQLdiag** 會收集 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤資訊，則您選擇要追蹤的事件類別愈多，伺服器效能受到的影響就愈大。</span><span class="sxs-lookup"><span data-stu-id="6f446-243">For example, if you have configured **SQLdiag** to collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tracing information, the more event classes you choose to trace, the more your server performance is affected.</span></span>  
  
 <span data-ttu-id="6f446-244">執行 **SQLdiag** 的效能影響大約相當於個別收集已設定之診斷資訊的成本總和。</span><span class="sxs-lookup"><span data-stu-id="6f446-244">The performance impact of running **SQLdiag** is approximately equivalent to the sum of the costs of collecting the configured diagnostics separately.</span></span> <span data-ttu-id="6f446-245">例如，利用 **SQLdiag** 收集追蹤，其帶來的效能成本與利用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]收集是一樣的。</span><span class="sxs-lookup"><span data-stu-id="6f446-245">For example, collecting a trace with **SQLdiag** incurs the same performance cost as collecting it with [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="6f446-246">使用 **SQLdiag** 所造成的效能影響可不予理會。</span><span class="sxs-lookup"><span data-stu-id="6f446-246">The performance impact of using **SQLdiag** is negligible.</span></span>  
  
## <a name="required-disk-space"></a><span data-ttu-id="6f446-247">所需磁碟空間</span><span class="sxs-lookup"><span data-stu-id="6f446-247">Required Disk Space</span></span>  
 <span data-ttu-id="6f446-248">由於 **SQLdiag** 可以收集不同類型的診斷資訊；因此，執行 **SQLdiag** 所需要的可用磁碟空間也各不相同。</span><span class="sxs-lookup"><span data-stu-id="6f446-248">Because **SQLdiag** can collect different types of diagnostic information, the free disk space that is required to run **SQLdiag** varies.</span></span> <span data-ttu-id="6f446-249">收集的診斷資訊數量會隨著伺服器所處理之工作負載的本質和數量而不同，範圍可能在幾 MB 到幾 GB 之間。</span><span class="sxs-lookup"><span data-stu-id="6f446-249">The amount of diagnostic information collected depends on the nature and volume of the workload that the server is processing and may range from a few megabytes to several gigabytes.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6f446-250">組態檔</span><span class="sxs-lookup"><span data-stu-id="6f446-250">Configuration Files</span></span>  
 <span data-ttu-id="6f446-251">在啟動時， **SQLdiag** 會讀取組態檔及已指定的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-251">On startup, **SQLdiag** reads the configuration file and the command line arguments that have been specified.</span></span> <span data-ttu-id="6f446-252">您可以在組態檔中指定 **SQLdiag** 所要收集的診斷資訊類型。</span><span class="sxs-lookup"><span data-stu-id="6f446-252">You specify the types of diagnostic information that **SQLdiag** collects in the configuration file.</span></span> <span data-ttu-id="6f446-253">依預設， **SQLdiag** 會使用 SQLDiag.Xml 組態檔，此組態檔會在每次執行此工具時加以擷取，且其位於 **SQLdiag** 公用程式啟動資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6f446-253">By default, **SQLdiag** uses the SQLDiag.Xml configuration file, which is extracted each time the tool runs and is located in the **SQLdiag** utility startup folder.</span></span> <span data-ttu-id="6f446-254">組態檔會使用 XML 結構描述 SQLDiag_schema.xsd，此結構描述也會在每次執行 **SQLdiag** 時，從可執行檔直接擷取到公用程式啟動目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f446-254">The configuration file uses the XML schema, SQLDiag_schema.xsd, which is also extracted into the utility startup directory from the executable file each time **SQLdiag** runs.</span></span>  
  
### <a name="editing-the-configuration-files"></a><span data-ttu-id="6f446-255">編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="6f446-255">Editing the Configuration Files</span></span>  
 <span data-ttu-id="6f446-256">您可以複製和編輯 SQLDiag.Xml 來變更 **SQLdiag** 所收集的診斷資料類型。</span><span class="sxs-lookup"><span data-stu-id="6f446-256">You can copy and edit SQLDiag.Xml to change the types of diagnostic data that **SQLdiag** collects.</span></span> <span data-ttu-id="6f446-257">編輯組態檔時，請務必使用可驗證組態檔之 XML 結構描述的 XML 編輯器，例如 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6f446-257">When editing the configuration file always use an XML editor that can validate the configuration file against its XML schema, such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="6f446-258">您不應該直接編輯 SQLDiag.Xml。</span><span class="sxs-lookup"><span data-stu-id="6f446-258">You should not edit SQLDiag.Xml directly.</span></span> <span data-ttu-id="6f446-259">但是，您應該複製一份 SQLDiag.Xml，然後在相同資料夾中，將它重新命名成新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-259">Instead, make a copy of SQLDiag.Xml and rename it to a new file name in the same folder.</span></span> <span data-ttu-id="6f446-260">接著，請編輯新的檔案，再利用 **/I** 引數，將它傳遞給 **SQLdiag**。</span><span class="sxs-lookup"><span data-stu-id="6f446-260">Then edit the new file, and use the **/I** argument to pass it to **SQLdiag**.</span></span>  
  
#### <a name="editing-the-configuration-file-when-sqldiag-runs-as-a-service"></a><span data-ttu-id="6f446-261">在 SQLdiag 執行為服務時編輯組態檔</span><span class="sxs-lookup"><span data-stu-id="6f446-261">Editing the Configuration File When SQLdiag Runs as a Service</span></span>  
 <span data-ttu-id="6f446-262">如果您已將 **SQLdiag** 執行為服務，且需要編輯組態檔，請指定 **/U** 命令列引數取消註冊 SQLDIAG 服務，再利用 **/R** 命令列引數重新註冊這項服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-262">If you have already run **SQLdiag** as a service and need to edit the configuration file, unregister the SQLDIAG service by specifying the **/U** command line argument and then re-register the service by using the **/R** command line argument.</span></span> <span data-ttu-id="6f446-263">取消登錄這項服務後再重新登錄它，會移除 Windows 登錄中快取的舊組態資訊。</span><span class="sxs-lookup"><span data-stu-id="6f446-263">Unregistering and re-registering the service removes old configuration information that was cached in the Windows registry.</span></span>  
  
## <a name="output-folder"></a><span data-ttu-id="6f446-264">輸出資料夾</span><span class="sxs-lookup"><span data-stu-id="6f446-264">Output Folder</span></span>  
 <span data-ttu-id="6f446-265">如果您沒有利用 **/O** 引數指定輸出資料夾， **SQLdiag** 會在 **SQLdiag** 啟動資料夾之下，建立名稱為 SQLDIAG 的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-265">If you do not specify an output folder with the **/O** argument, **SQLdiag** creates a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="6f446-266">對於需要大量追蹤的診斷資訊收集 (例如 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] )，請確定輸出資料夾位於擁有足夠空間，可以儲存所要求之診斷輸出的本機磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="6f446-266">For diagnostic information collection that involves high volume tracing, such as [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] , make sure that the output folder is on a local drive with enough space to store the requested diagnostic output.</span></span>  
  
 <span data-ttu-id="6f446-267">當 **SQLdiag** 重新啟動時，它會覆寫輸出資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="6f446-267">When **SQLdiag** is restarted, it overwrites the contents of the output folder.</span></span> <span data-ttu-id="6f446-268">若要避免發生此情形，請在命令列上指定 **/N 2** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-268">To avoid this, specify **/N 2** on the command line.</span></span>  
  
## <a name="data-collection-process"></a><span data-ttu-id="6f446-269">資料收集程序</span><span class="sxs-lookup"><span data-stu-id="6f446-269">Data Collection Process</span></span>  
 <span data-ttu-id="6f446-270">當 **SQLdiag** 啟動時，它會執行收集 SQLDiag.Xml 中所指定之診斷資料所需的初始化檢查。</span><span class="sxs-lookup"><span data-stu-id="6f446-270">When **SQLdiag** starts, it performs the initialization checks necessary to collect the diagnostic data that have been specified in SQLDiag.Xml.</span></span> <span data-ttu-id="6f446-271">這個程序可能需要幾秒鐘。</span><span class="sxs-lookup"><span data-stu-id="6f446-271">This process may take several seconds.</span></span> <span data-ttu-id="6f446-272">當以主控台應用程式執行 **SQLdiag** 時，在它開始收集診斷資料之後，會出現一則訊息，通知您 **SQLdiag** 收集作業已經開始，您可以按 CTRL+C 加以停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-272">After **SQLdiag** has started collecting diagnostic data when it is run as a console application, a message displays informing you that **SQLdiag** collection has started and that you can press CTRL+C to stop it.</span></span> <span data-ttu-id="6f446-273">當 **SQLdiag** 執行為服務時，會在 Windows 事件記錄檔中寫入一則類似的訊息。</span><span class="sxs-lookup"><span data-stu-id="6f446-273">When **SQLdiag** is run as a service, a similar message is written to the Windows event log.</span></span>  
  
 <span data-ttu-id="6f446-274">如果您利用 **SQLdiag** 診斷可以重現的問題，請等到收到這則訊息之後，再於伺服器中重現此問題。</span><span class="sxs-lookup"><span data-stu-id="6f446-274">If you are using **SQLdiag** to diagnose a problem that you can reproduce, wait until you receive this message before you reproduce the problem on your server.</span></span>  
  
 <span data-ttu-id="6f446-275">**SQLdiag** 會以平行方式收集大部分的診斷資料。</span><span class="sxs-lookup"><span data-stu-id="6f446-275">**SQLdiag** collects most diagnostic data in parallel.</span></span> <span data-ttu-id="6f446-276">除了從 Windows 效能記錄檔和事件記錄檔收集資訊之外，所有診斷資訊都是藉由連線到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** 公用程式或 Windows 命令處理器之類的工具加以收集。</span><span class="sxs-lookup"><span data-stu-id="6f446-276">All diagnostic information is collected by connecting to tools, such as the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** utility or the Windows command processor, except when information is collected from Windows performance logs and event logs.</span></span> <span data-ttu-id="6f446-277">**SQLdiag** 會在每部電腦上各使用一個工作者執行緒，監視這些其他工具的診斷資料收集，通常會同時等待多個工具完成。</span><span class="sxs-lookup"><span data-stu-id="6f446-277">**SQLdiag** uses one worker thread per computer to monitor the diagnostic data collection of these other tools, often simultaneously waiting for several tools to complete.</span></span> <span data-ttu-id="6f446-278">在收集過程期間， **SQLdiag** 會將每一個診斷的輸出路由傳送至輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-278">During the collection process, **SQLdiag** routes the output from each diagnostic to the output folder.</span></span>  
  
## <a name="stopping-data-collection"></a><span data-ttu-id="6f446-279">停止收集資料</span><span class="sxs-lookup"><span data-stu-id="6f446-279">Stopping Data Collection</span></span>  
 <span data-ttu-id="6f446-280">在 **SQLdiag** 開始收集診斷資料之後，除非您將它停止，或將它設定成在指定的時間停止，否則它會持續作業。</span><span class="sxs-lookup"><span data-stu-id="6f446-280">After **SQLdiag** starts collecting diagnostic data, it continues to do so unless you stop it or it is configured to stop at a specified time.</span></span> <span data-ttu-id="6f446-281">您可以利用可讓您指定停止時間的 **/E** 引數，或利用使 **SQLdiag** 以快照集模式執行的 **/X** 引數，將 **SQLdiag** 設定成於指定的時間停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-281">You can configure **SQLdiag** to stop at a specified time by using the **/E** argument, which allows you to specify a stop time, or by using the **/X** argument, which causes **SQLdiag** to run in snapshot mode.</span></span>  
  
 <span data-ttu-id="6f446-282">當 **SQLdiag** 停止時，它會停止所有已啟動的診斷作業。</span><span class="sxs-lookup"><span data-stu-id="6f446-282">When **SQLdiag** stops, it stops all diagnostics it has started.</span></span> <span data-ttu-id="6f446-283">例如，它會停止正在收集的 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤、停止執行正在執行的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼，以及停止在資料收集期間繁衍的任何子程序。</span><span class="sxs-lookup"><span data-stu-id="6f446-283">For example, it stops [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] traces it was collecting, it stops executing [!INCLUDE[tsql](../includes/tsql-md.md)] scripts it was running, and it stops any sub processes it has spawned during data collection.</span></span> <span data-ttu-id="6f446-284">診斷資料收集完成之後， **SQLdiag** 便會結束。</span><span class="sxs-lookup"><span data-stu-id="6f446-284">After diagnostic data collection has completed, **SQLdiag** exits.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-285">不支援暫停 **SQLdiag** 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-285">Pausing the **SQLdiag** service is not supported.</span></span> <span data-ttu-id="6f446-286">如果您嘗試暫停 **SQLdiag** 服務，它會將您暫停它時正在收集的診斷收集完成之後才停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-286">If you attempt to pause the **SQLdiag** service, it stops after it finishes collecting the diagnostics that it was collecting when you paused it.</span></span> <span data-ttu-id="6f446-287">如果您在停止 **SQLdiag** 之後又重新加以啟動，則該應用程式會重新啟動並覆寫輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-287">If you restart **SQLdiag** after stopping it, the application restarts and overwrites the output folder.</span></span> <span data-ttu-id="6f446-288">若要避免覆寫輸出資料夾，請在命令列上指定 **/N 2** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-288">To avoid overwriting the output folder, specify **/N 2** on the command line.</span></span>  
  
 <span data-ttu-id="6f446-289">**停止當做主控台應用程式執行的 SQLdiag**</span><span class="sxs-lookup"><span data-stu-id="6f446-289">**To stop SQLdiag when running as a console application**</span></span>  
  
 <span data-ttu-id="6f446-290">如果您將 **SQLdiag** 執行為主控台應用程式，在執行 **SQLdiag** 的主控台視窗中，按 CTRL+C 可加以停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-290">If you are running **SQLdiag** as a console application, press CTRL+C in the console window where **SQLdiag** is running to stop it.</span></span> <span data-ttu-id="6f446-291">按 CTRL+C 之後，主控台視窗中會出現一則訊息，通知您 **SQLDiag** 的資料收集即將結束，您應該等候該處理序關閉，這可能需要幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-291">After you press CTRL+C, a message displays in the console window informing you that **SQLDiag** data collection is ending, and that you should wait until the process shuts down, which may take several minutes.</span></span>  
  
 <span data-ttu-id="6f446-292">按 Ctrl+C 兩次結束所有子診斷程序，並立即結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f446-292">Press Ctrl+C twice to terminate all child diagnostic processes and immediately terminate the application.</span></span>  
  
 <span data-ttu-id="6f446-293">**停止執行為服務的 SQLdiag**</span><span class="sxs-lookup"><span data-stu-id="6f446-293">**To stop SQLdiag when running as a service**</span></span>  
  
 <span data-ttu-id="6f446-294">如果您將 **SQLdiag** 執行為服務，請在 **SQLdiag** 啟動資料夾內執行 **SQLDiag STOP** 加以停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-294">If you are running **SQLdiag** as a service, run **SQLDiag STOP** in the **SQLdiag** startup folder to stop it.</span></span>  
  
 <span data-ttu-id="6f446-295">如果您在相同的電腦上執行多個 **SQLdiag** 執行個體，則當您停止服務時，也可以在命令列上傳遞 **SQLdiag** 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-295">If you are running multiple instances of **SQLdiag** on the same computer, you can also pass the **SQLdiag** instance name to on the command line when you stop the service.</span></span> <span data-ttu-id="6f446-296">例如，若要停止 **SQLdiag** 執行個體 Instance1，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6f446-296">For example, to stop a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG STOP /A Instance1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-297">**/A** 是唯一可以與 **START**、 **STOP**或 **STOP_ABORT**一起使用的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-297">**/A** is the only command-line argument that can be used with **START**, **STOP**, or **STOP_ABORT**.</span></span> <span data-ttu-id="6f446-298">如果您需要以其中一個服務控制動詞指定 **SQLdiag** 的具名執行個體，請在命令列上該控制動詞後指定 **/A** ，如上述語法範例所示。</span><span class="sxs-lookup"><span data-stu-id="6f446-298">If you need to specify a named instance of **SQLdiag** with one of the service control verbs, specify **/A** after the control verb on the command line as shown in the previous syntax example.</span></span> <span data-ttu-id="6f446-299">使用控制動詞時，它們必須是命令列上的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-299">When control verbs are used, they must be the first argument on the command line.</span></span>  
  
 <span data-ttu-id="6f446-300">若要盡快停止服務，請執行公用程式啟動資料夾中的 **SQLDIAG STOP_ABORT** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-300">To stop the service as quickly as possible, run **SQLDIAG STOP_ABORT** in the utility startup folder.</span></span> <span data-ttu-id="6f446-301">此命令會中止目前正在執行的任何診斷收集，而不會等到它們完成。</span><span class="sxs-lookup"><span data-stu-id="6f446-301">This command aborts any diagnostics collecting currently being performed without waiting for them to finish.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-302">請使用 **SQLDiag STOP** 或 **SQLDIAG STOP_ABORT** 停止 **SQLdiag** 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-302">Use **SQLDiag STOP** or **SQLDIAG STOP_ABORT** to stop the **SQLdiag** service.</span></span> <span data-ttu-id="6f446-303">請勿使用 Windows 服務主控台停止 **SQLdiag** 或其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-303">Do not use the Windows Services Console to stop **SQLdiag** or other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="automatically-starting-and-stopping-sqldiag"></a><span data-ttu-id="6f446-304">自動啟動和停止 SQLdiag</span><span class="sxs-lookup"><span data-stu-id="6f446-304">Automatically Starting and Stopping SQLdiag</span></span>  
 <span data-ttu-id="6f446-305">若要在指定時間自動啟動及停止診斷資料收集，請使用 **/b**_start_time_和 **/e**_stop_time_引數（使用24小時標記法）。</span><span class="sxs-lookup"><span data-stu-id="6f446-305">To automatically start and stop diagnostic data collection at a specified time, use the **/B**_start_time_ and **/E**_stop_time_ arguments, using 24-hour notation.</span></span> <span data-ttu-id="6f446-306">例如，如果您要針對大約在 02:00:00 一致出現的問題進行疑難排解，您可以將 **SQLdiag** 設定成在 01:00 自動開始收集診斷資料且在 03:00:00 自動停止。</span><span class="sxs-lookup"><span data-stu-id="6f446-306">For example, if you are troubleshooting a problem that consistently appears at approximately 02:00:00, you can configure **SQLdiag** to automatically start collecting diagnostic data at 01:00 and automatically stop at 03:00:00.</span></span> <span data-ttu-id="6f446-307">請利用 **/B** 和 **/E** 引數來指定開始和停止時間。</span><span class="sxs-lookup"><span data-stu-id="6f446-307">Use the **/B** and **/E** arguments to specify the start and stop time.</span></span> <span data-ttu-id="6f446-308">請利用 24 小時標記法來指定開始和停止的確切日期和時間，格式為 YYYYMMDD_HH:MM:SS。</span><span class="sxs-lookup"><span data-stu-id="6f446-308">Use 24-hour notation to specify an exact start and stop date and time with the format YYYYMMDD_HH:MM:SS.</span></span> <span data-ttu-id="6f446-309">若要指定相對的開始或停止時間，請依照下列範例所示，在開始和停止時間之前附加 **+** ，並省略日期部分 (YYYYMMDD_)，如此會讓 **SQLdiag** 等候 1 小時再開始收集資訊，之後會收集 3 小時的資訊，再停止並結束：</span><span class="sxs-lookup"><span data-stu-id="6f446-309">To specify a relative start or stop time, prefix the start and stop time with **+** and omit the date portion (YYYYMMDD_) as shown in the following example, which causes **SQLdiag** to wait 1 hour before it starts collecting information, then it collects information for 3 hours before it stops and exits:</span></span>  
  
```  
sqldiag /B +01:00:00 /E +03:00:00  
```  
  
 <span data-ttu-id="6f446-310">指定相對的 *start_time* 之後， **SQLdiag** 就會在相對於目前日期和時間的時間啟動。</span><span class="sxs-lookup"><span data-stu-id="6f446-310">When a relative *start_time* is specified, **SQLdiag** starts at a time that is relative to the current date and time.</span></span> <span data-ttu-id="6f446-311">指定相對的 *end_time* 之後， **SQLdiag** 就會在相對於指定的 *start_time*的時間結束。</span><span class="sxs-lookup"><span data-stu-id="6f446-311">When a relative *end_time* is specified, **SQLdiag** ends at a time that is relative to the specified *start_time*.</span></span> <span data-ttu-id="6f446-312">如果您指定的開始或結束日期和時間已經過去， **SQLdiag** 會強制變更開始日期，讓開始日期和時間設定在未來。</span><span class="sxs-lookup"><span data-stu-id="6f446-312">If the start or end date and time that you have specified is in the past, **SQLdiag** forcibly changes the start date so that the start date and time are in the future.</span></span>  
  
 <span data-ttu-id="6f446-313">對您選擇的開始和結束日期而言，這有重要的影響。</span><span class="sxs-lookup"><span data-stu-id="6f446-313">This has important implications on the start and end dates you choose.</span></span> <span data-ttu-id="6f446-314">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="6f446-314">Consider the following example:</span></span>  
  
```  
sqldiag /B +01:00:00 /E 08:30:00  
```  
  
 <span data-ttu-id="6f446-315">如果目前的時間是 08:00，在實際開始收集診斷資訊之前，結束時間便已過去。</span><span class="sxs-lookup"><span data-stu-id="6f446-315">If the current time is 08:00, the end time passes before diagnostic collection actually begins.</span></span> <span data-ttu-id="6f446-316">因為 **SQLDiag** 會將發生在過去的開始和結束日期自動調整至隔天，所以在此範例中，診斷收集會從今天 09:00 開始 (已使用 **+** 指定相對的開始時間)，並繼續收集直到隔天早上 08:30。</span><span class="sxs-lookup"><span data-stu-id="6f446-316">Because **SQLDiag** automatically adjusts start and end dates to the next day when they occur in the past, in this example diagnostic collection starts at 09:00 today (a relative start time has been specified with **+**) and continues collecting until 08:30 the following morning.</span></span>  
  
### <a name="stopping-and-restarting-sqldiag-to-collect-daily-diagnostics"></a><span data-ttu-id="6f446-317">停止和重新啟動 SQLdiag 來收集每天的診斷資訊</span><span class="sxs-lookup"><span data-stu-id="6f446-317">Stopping and Restarting SQLdiag to Collect Daily Diagnostics</span></span>  
 <span data-ttu-id="6f446-318">若要每天收集一組指定的診斷資訊，而不要手動啟動和停止 **SQLdiag**，請使用 **/L** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-318">To collect a specified set of diagnostics on a daily basis without having to manually start and stop **SQLdiag**, use the **/L** argument.</span></span> <span data-ttu-id="6f446-319">**/L** 引數會在排程的關閉之後，自行重新啟動以持續執行 **SQLdiag** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-319">The **/L** argument causes **SQLdiag** to run continuously by automatically restarting itself after a scheduled shutdown.</span></span> <span data-ttu-id="6f446-320">若指定 **/L** ，且 **SQLdiag** 因為達到使用 **/E** 引數所指定的結束時間而停止，或因為使用 **/X** 引數以快照集模式執行而停止， **SQLdiag** 都將會重新啟動而不是結束。</span><span class="sxs-lookup"><span data-stu-id="6f446-320">When **/L** is specified, and **SQLdiag** stops because it has reached the end time specified with the **/E** argument, or it stops because it is being run in snapshot mode by using the **/X** argument, **SQLdiag** restarts instead of exiting.</span></span>  
  
 <span data-ttu-id="6f446-321">下列範例指定以連續模式執行 **SQLdiag** ，以便在 03:00:00 和 05:00:00 之間收集診斷資料之後，自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="6f446-321">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after diagnostic data collecting occurs between 03:00:00 and 05:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /E 05:00:00 /L  
```  
  
 <span data-ttu-id="6f446-322">下列範例指定以連續模式執行 **SQLdiag** ，以在 03:00:00 時取得診斷資料快照集之後，自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="6f446-322">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after taking a diagnostic data snapshot at 03:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /X /L  
```  
  
## <a name="running-sqldiag-as-a-service"></a><span data-ttu-id="6f446-323">將 SQLdiag 執行為服務</span><span class="sxs-lookup"><span data-stu-id="6f446-323">Running SQLdiag as a Service</span></span>  
 <span data-ttu-id="6f446-324">當您要利用 **SQLdiag** 長時間收集診斷資料，且在這段時間中您可能需要登出執行 **SQLdiag** 的電腦，您可以將其執行為服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-324">When you want to use **SQLdiag** to collect diagnostic data for long periods of time during which you might need to log out of the computer on which **SQLdiag** is running, you can run it as a service.</span></span>  
  
 <span data-ttu-id="6f446-325">**將 SQLDiag 註冊執行為服務**</span><span class="sxs-lookup"><span data-stu-id="6f446-325">**To register SQLDiag to run as a service**</span></span>  
  
 <span data-ttu-id="6f446-326">您可以在命令列處指定 **/R** 引數，將 **SQLdiag** 註冊為以服務方式執行。</span><span class="sxs-lookup"><span data-stu-id="6f446-326">You can register **SQLdiag** to run as a service by specifying the **/R** argument at the command line.</span></span> <span data-ttu-id="6f446-327">這會將 **SQLdiag** 註冊執行為服務</span><span class="sxs-lookup"><span data-stu-id="6f446-327">This registers **SQLdiag** to run as a service.</span></span> <span data-ttu-id="6f446-328">**SQLdiag** 服務名稱是 SQLDIAG。</span><span class="sxs-lookup"><span data-stu-id="6f446-328">The **SQLdiag** service name is SQLDIAG.</span></span> <span data-ttu-id="6f446-329">當您將 **SQLDiag** 註冊成服務時，您在命令列上指定的所有其他引數都會保留下來，啟動這項服務時會重複使用它們。</span><span class="sxs-lookup"><span data-stu-id="6f446-329">Any other arguments you specify on the command line when you register **SQLDiag** as a service are preserved and reused when the service is started.</span></span>  
  
 <span data-ttu-id="6f446-330">若要變更預設 SQLDIAG 服務名稱，請使用 **/A** 命令列引數來指定另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-330">To change the default SQLDIAG service name, use the **/A** command-line argument to specify another name.</span></span> <span data-ttu-id="6f446-331">**SQLdiag** 會將 DIAG$ 自動前置於任何以 **/A** 指定的 **SQLdiag** 執行個體名稱，以建立實用的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-331">**SQLdiag** automatically prefixes DIAG$ to any **SQLdiag** instance name specified with **/A** to create sensible service names.</span></span>  
  
 <span data-ttu-id="6f446-332">**若要取消登錄 SQLDIAG 服務**</span><span class="sxs-lookup"><span data-stu-id="6f446-332">**To unregister the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="6f446-333">若要取消註冊服務，請指定 **/U** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-333">To unregister the service, specify the **/U** argument.</span></span> <span data-ttu-id="6f446-334">取消註冊 **SQLdiag** 的服務身分，也會刪除該服務的 Windows 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="6f446-334">Unregistering **SQLdiag** as a service also deletes the Windows registry keys of the service.</span></span>  
  
 <span data-ttu-id="6f446-335">**若要啟動或重新啟動 SQLDIAG 服務**</span><span class="sxs-lookup"><span data-stu-id="6f446-335">**To start or restart the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="6f446-336">若要啟動或重新啟動 SQLDIAG 服務，請從命令列執行 **SQLDiag START** 。</span><span class="sxs-lookup"><span data-stu-id="6f446-336">To start or restart the SQLDIAG service, run **SQLDiag START** from the command line.</span></span>  
  
 <span data-ttu-id="6f446-337">如果您使用 **/A** 引數執行多個 **SQLdiag** 的執行個體，當您啟動服務時，您也可以在命令列上傳遞 **SQLdiag** 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="6f446-337">If you are running multiple instances of **SQLdiag** by using the **/A** argument, you can also pass the **SQLdiag** instance name on the command line when you start the service.</span></span> <span data-ttu-id="6f446-338">例如，若要開始 **SQLdiag** 執行個體 Instance1，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="6f446-338">For example, to start a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG START /A Instance1  
```  
  
 <span data-ttu-id="6f446-339">您也可以利用 **net start** 命令來啟動 SQLDIAG 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-339">You can also use the **net start** command to start the SQLDIAG service.</span></span>  
  
 <span data-ttu-id="6f446-340">當您重新啟動 **SQLdiag**時，它會覆寫目前輸出資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="6f446-340">When you restart **SQLdiag**, it overwrites the contents in the current output folder.</span></span> <span data-ttu-id="6f446-341">為避免發生此情形，請在命令列上指定 **/N 2** ，在公用程式啟動時重新命名輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="6f446-341">To avoid this, specify **/N 2** on the command line to rename the output folder when the utility starts.</span></span>  
  
 <span data-ttu-id="6f446-342">不支援暫停 **SQLdiag** 服務。</span><span class="sxs-lookup"><span data-stu-id="6f446-342">Pausing the **SQLdiag** service is not supported.</span></span>  
  
## <a name="running-multiple-instances-of-sqldiag"></a><span data-ttu-id="6f446-343">執行 SQLdiag 的多個執行個體</span><span class="sxs-lookup"><span data-stu-id="6f446-343">Running Multiple Instances of SQLdiag</span></span>  
 <span data-ttu-id="6f446-344">在同一部電腦上執行多個**SQLdiag**實例，方法是在命令列上指定 **/a**_SQLdiag_application_name_ 。</span><span class="sxs-lookup"><span data-stu-id="6f446-344">Run multiple instances of **SQLdiag** on the same computer by specifying **/A**_SQLdiag_application_name_ on the command line.</span></span> <span data-ttu-id="6f446-345">這對於同時從相同 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體收集不同的診斷集很有幫助。</span><span class="sxs-lookup"><span data-stu-id="6f446-345">This is useful for collecting different sets of diagnostics simultaneously from the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="6f446-346">例如，您可以設定 **SQLdiag** 的具名執行個體，持續執行輕量型資料收集。</span><span class="sxs-lookup"><span data-stu-id="6f446-346">For example, you can configure a named instance of **SQLdiag** to continuously perform lightweight data collection.</span></span> <span data-ttu-id="6f446-347">之後，如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上發生特定的問題，您可以執行預設的 **SQLdiag** 執行個體來收集該問題的診斷資訊，或蒐集 [!INCLUDE[msCoName](../includes/msconame-md.md)] 客戶支援服務要求您搜尋的一組診斷來診斷問題。</span><span class="sxs-lookup"><span data-stu-id="6f446-347">Then, if a specific problem occurs on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can run the default **SQLdiag** instance to collect diagnostics for that problem, or to gather a set of diagnostics that [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services has asked you to gather to diagnose a problem.</span></span>  
  
## <a name="collecting-diagnostic-data-from-clustered-sql-server-instances"></a><span data-ttu-id="6f446-348">從叢集 SQL Server 執行個體收集診斷資料</span><span class="sxs-lookup"><span data-stu-id="6f446-348">Collecting Diagnostic Data from Clustered SQL Server Instances</span></span>  
 <span data-ttu-id="6f446-349">**SQLdiag** 支援從叢集的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體中收集診斷資料。</span><span class="sxs-lookup"><span data-stu-id="6f446-349">**SQLdiag** supports collecting diagnostic data from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="6f446-350">若要從叢集的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體收集診斷資料，請確定已在設定檔 SQLDiag.Xml 中，為 **\<Machine>** 元素的 **name** 屬性指定 **"."** ，而且不要在命令列上指定 **/G** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-350">To gather diagnostics from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, make sure that **"."** is specified for the **name** attribute of the **\<Machine>** element in the configuration file SQLDiag.Xml and do not specify the **/G** argument on the command line.</span></span> <span data-ttu-id="6f446-351">預設會在組態檔中對 **name** 屬性指定 **"."** ，且會關閉 **/G** 引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-351">By default, **"."** is specified for the **name** attribute in the configuration file and the **/G** argument is turned off.</span></span> <span data-ttu-id="6f446-352">通常，從叢集的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體中收集時，您不需要編輯組態檔或變更命令列引數。</span><span class="sxs-lookup"><span data-stu-id="6f446-352">Typically, you do not need to edit the configuration file or change the command line arguments when collecting from a clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="6f446-353">當 **"."** 指定為機器名稱時， **SQLdiag** 會偵測到它執行於叢集上，同時會從安裝在叢集上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的所有虛擬執行個體，擷取診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="6f446-353">When **"."** is specified as the machine name, **SQLdiag** detects that it is running on a cluster, and simultaneously retrieves diagnostic information from all virtual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are installed on the cluster.</span></span> <span data-ttu-id="6f446-354">如果您只想要從電腦上執行的一個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 虛擬執行個體收集診斷資訊，請在 SQLDiag.Xml 中，為 **\<Machine>** 元素的 **name** 屬性指定該虛擬 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6f446-354">If you want to collect diagnostic information from only one virtual instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is running on a computer, specify that virtual [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] for the **name** attribute of the **\<Machine>** element in SQLDiag.Xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6f446-355">若要從叢集的 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 執行個體收集 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 追蹤資訊，必須在叢集上啟用管理共用 (ADMIN$)。</span><span class="sxs-lookup"><span data-stu-id="6f446-355">To collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, administrative shares (ADMIN$) must be enabled on the cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f446-356">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f446-356">See Also</span></span>  
 [<span data-ttu-id="6f446-357">命令提示字元公用程式參考 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="6f446-357">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
