---
title: 檢視與讀取 SQL Server 安裝程式記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 70f9bbb9a8ed72503dc6fe90077232748b2c4ac2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698515"
---
# <a name="view-and-read-sql-server-setup-log-files"></a><span data-ttu-id="54760-102">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="54760-102">View and Read SQL Server Setup Log Files</span></span>
  <span data-ttu-id="54760-103">每次執行安裝程式時，都會使用新的時間戳記記錄檔資料夾（位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log）來建立記錄檔 \\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-103">Each execution of Setup creates log files are created with a new timestamped log folder at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span> <span data-ttu-id="54760-104">時間戳記記錄檔資料夾的名稱格式為 YYYYMMDD_hhmmss。</span><span class="sxs-lookup"><span data-stu-id="54760-104">The time-stamped log folder name format is YYYYMMDD_hhmmss.</span></span> <span data-ttu-id="54760-105">在自動安裝模式下執行安裝程式時，會在 % temp%\sqlsetup\*.log 建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="54760-105">When Setup is run in an unattended mode, the logs are created at % temp%\sqlsetup\*.log.</span></span> <span data-ttu-id="54760-106">記錄檔資料夾中的所有檔案都會封存到個別記錄檔資料夾的 Log\*.cab 檔中。</span><span class="sxs-lookup"><span data-stu-id="54760-106">All files in the logs folder are archived into the Log\*.cab file in their respective log folder.</span></span>  
  
 <span data-ttu-id="54760-107">典型的安裝程式要求會經過三個執行階段：</span><span class="sxs-lookup"><span data-stu-id="54760-107">A typical Setup request goes through three execution phases:</span></span>  
  
1.  <span data-ttu-id="54760-108">全域規則文字</span><span class="sxs-lookup"><span data-stu-id="54760-108">Global rules text</span></span>  
  
2.  <span data-ttu-id="54760-109">元件更新</span><span class="sxs-lookup"><span data-stu-id="54760-109">Component update</span></span>  
  
3.  <span data-ttu-id="54760-110">使用者要求的動作</span><span class="sxs-lookup"><span data-stu-id="54760-110">User-requested action</span></span>  
  
 <span data-ttu-id="54760-111">在每個階段，安裝程式都會產生詳細和摘要的記錄檔，並且會依需要建立其他的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="54760-111">In each phase, Setup generates detail and summary logs with additional logs created as appropriate.</span></span> <span data-ttu-id="54760-112">每個使用者要求的安裝程式動作都會至少呼叫安裝程式三次。</span><span class="sxs-lookup"><span data-stu-id="54760-112">Setup is called at least three times per user-requested Setup action.</span></span>  
  
 <span data-ttu-id="54760-113">資料存放區檔案包含安裝程序所追蹤的所有組態物件的狀態快照，對於疑難排解組態錯誤很有用。</span><span class="sxs-lookup"><span data-stu-id="54760-113">Datastore files contain a snapshot of the state of all configuration objects being tracked by the Setup process, and are useful for troubleshooting configuration errors.</span></span> <span data-ttu-id="54760-114">XML 檔案傾印會針對每個執行階段為資料存放區物件而建立。</span><span class="sxs-lookup"><span data-stu-id="54760-114">XML file dumps are created for datastore objects for each execution phase.</span></span> <span data-ttu-id="54760-115">這些會儲存在本身的記錄子資料夾的時間戳記記錄檔資料夾下方，如下所示：</span><span class="sxs-lookup"><span data-stu-id="54760-115">They are saved in their own log subfolder under the time-stamped log folder, as follows:</span></span>  
  
-   <span data-ttu-id="54760-116">Datastore_GlobalRules</span><span class="sxs-lookup"><span data-stu-id="54760-116">Datastore_GlobalRules</span></span>  
  
-   <span data-ttu-id="54760-117">Datastore_ComponentUpdated</span><span class="sxs-lookup"><span data-stu-id="54760-117">Datastore_ComponentUpdated</span></span>  
  
-   <span data-ttu-id="54760-118">資料存放區</span><span class="sxs-lookup"><span data-stu-id="54760-118">Datastore</span></span>  
  
 <span data-ttu-id="54760-119">下列各節描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="54760-119">The following sections describe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup log files.</span></span>  
  
## <a name="summary-text"></a><span data-ttu-id="54760-120">摘要文字</span><span class="sxs-lookup"><span data-stu-id="54760-120">Summary Text</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-121">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-121">Overview</span></span>  
 <span data-ttu-id="54760-122">此檔案會顯示安裝期間偵測到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件、作業系統環境、命令列參數值 (如果有指定)，以及已執行之每個 MSI/MSP 的整體狀態。</span><span class="sxs-lookup"><span data-stu-id="54760-122">This file shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components that were detected during Setup, the operating system environment, command-line parameter values if they are specified, and the overall status of each MSI/MSP that was executed.</span></span>  
  
 <span data-ttu-id="54760-123">記錄檔組織成下列各區段：</span><span class="sxs-lookup"><span data-stu-id="54760-123">The log is organized into the following sections:</span></span>  
  
-   <span data-ttu-id="54760-124">執行的整體摘要</span><span class="sxs-lookup"><span data-stu-id="54760-124">An overall summary of the execution</span></span>  
  
-   <span data-ttu-id="54760-125">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式所在電腦的屬性和組態</span><span class="sxs-lookup"><span data-stu-id="54760-125">Properties and the configuration of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup was run</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="54760-126">先前安裝在電腦上的產品功能</span><span class="sxs-lookup"><span data-stu-id="54760-126">product features previously installed on the computer</span></span>  
  
-   <span data-ttu-id="54760-127">安裝版本與安裝套件屬性的描述</span><span class="sxs-lookup"><span data-stu-id="54760-127">Description of the installation version and installation package properties</span></span>  
  
-   <span data-ttu-id="54760-128">安裝期間提供的執行階段輸入設定</span><span class="sxs-lookup"><span data-stu-id="54760-128">Runtime input settings that are provided during install</span></span>  
  
-   <span data-ttu-id="54760-129">組態檔的位置</span><span class="sxs-lookup"><span data-stu-id="54760-129">Location of the configuration file</span></span>  
  
-   <span data-ttu-id="54760-130">執行結果的詳細資料</span><span class="sxs-lookup"><span data-stu-id="54760-130">Details of the execution results</span></span>  
  
-   <span data-ttu-id="54760-131">全域規則</span><span class="sxs-lookup"><span data-stu-id="54760-131">Global rules</span></span>  
  
-   <span data-ttu-id="54760-132">安裝狀況專屬的規則</span><span class="sxs-lookup"><span data-stu-id="54760-132">Rules specific to the installation scenario</span></span>  
  
-   <span data-ttu-id="54760-133">失敗的規則</span><span class="sxs-lookup"><span data-stu-id="54760-133">Failed rules</span></span>  
  
-   <span data-ttu-id="54760-134">規則報表檔案的位置</span><span class="sxs-lookup"><span data-stu-id="54760-134">Location of the rules report file</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-135">Location</span><span class="sxs-lookup"><span data-stu-id="54760-135">Location</span></span>  
 <span data-ttu-id="54760-136">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-136">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\.</span></span>  
  
 <span data-ttu-id="54760-137">若要尋找摘要文字檔中的錯誤，使用 "error" 或 "failed" 等關鍵字搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="54760-137">To find errors in the summary text file, search the file by using the "error" or "failed" keywords.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmsstxt"></a><span data-ttu-id="54760-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span><span class="sxs-lookup"><span data-stu-id="54760-138">Summary_engine-base_YYYYMMDD_HHMMss.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-139">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-139">Overview</span></span>  
 <span data-ttu-id="54760-140">summary_engine base 檔案與摘要檔案類似，而且是在主要工作流程期間產生的。</span><span class="sxs-lookup"><span data-stu-id="54760-140">The summary_engine base file is similar to the summary file and is generated during the main workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-141">Location</span><span class="sxs-lookup"><span data-stu-id="54760-141">Location</span></span>  
 <span data-ttu-id="54760-142">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-142">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_yyyymmdd_hhmmss_componentupdatetxt"></a><span data-ttu-id="54760-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="54760-143">Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-144">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-144">Overview</span></span>  
 <span data-ttu-id="54760-145">元件更新摘要記錄檔與摘要檔案類似，而且是在元件更新工作流程期間產生的。</span><span class="sxs-lookup"><span data-stu-id="54760-145">The component update summary log file is similar to the summary file and is generated during the component update workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-146">Location</span><span class="sxs-lookup"><span data-stu-id="54760-146">Location</span></span>  
 <span data-ttu-id="54760-147">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-147">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="summary_engine-base_versionnumbermmdd_hhmmss_globalrulestxt"></a><span data-ttu-id="54760-148">Summary_engine base_ \<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="54760-148">Summary_engine-base_\<VersionNumber>MMDD_HHMMss_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-149">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-149">Overview</span></span>  
 <span data-ttu-id="54760-150">全域規則摘要記錄檔與摘要檔案類似，而且是在全域規則工作流程期間產生的。</span><span class="sxs-lookup"><span data-stu-id="54760-150">The global rules summary log file is similar to the summary file generated during the global rules workflow.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-151">Location</span><span class="sxs-lookup"><span data-stu-id="54760-151">Location</span></span>  
 <span data-ttu-id="54760-152">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-152">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detailtxt"></a><span data-ttu-id="54760-153">Detail.txt</span><span class="sxs-lookup"><span data-stu-id="54760-153">Detail.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-154">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-154">Overview</span></span>  
 <span data-ttu-id="54760-155">安裝或升級之類的主要工作流程會產生 Detail.txt，並提供執行的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="54760-155">Detail.txt is generated for the main workflow such as install or upgrade, and provides the details of the execution.</span></span> <span data-ttu-id="54760-156">針對安裝叫用每個動作時，檔案中的記錄會隨著時間而產生，並顯示執行動作的順序及其相依性。</span><span class="sxs-lookup"><span data-stu-id="54760-156">The logs in the file are generated based on the time when each action for the installation was invoked, and show the order in which the actions were executed, and their dependencies.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-157">Location</span><span class="sxs-lookup"><span data-stu-id="54760-157">Location</span></span>  
 <span data-ttu-id="54760-158">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup</span><span class="sxs-lookup"><span data-stu-id="54760-158">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup</span></span>  
  
 <span data-ttu-id="54760-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span><span class="sxs-lookup"><span data-stu-id="54760-159">Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt.</span></span>  
  
 <span data-ttu-id="54760-160">如果在安裝程序期間發生錯誤，就會在此檔案的結尾記錄例外狀況或錯誤。</span><span class="sxs-lookup"><span data-stu-id="54760-160">If an error occurs during the Setup process, the exception or error are logged at the end of this file.</span></span> <span data-ttu-id="54760-161">若要尋找此檔案中的錯誤，請先檢查檔案的結尾，然後再搜尋檔案中的 "error" 或 "exception" 等關鍵字。</span><span class="sxs-lookup"><span data-stu-id="54760-161">To find the errors in this file, first examine the end of the file followed by a search of the file for the "error" or "exception" keywords.</span></span>  
  
## <a name="detail_componentupdatetxt"></a><span data-ttu-id="54760-162">Detail_ComponentUpdate.txt</span><span class="sxs-lookup"><span data-stu-id="54760-162">Detail_ComponentUpdate.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-163">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-163">Overview</span></span>  
 <span data-ttu-id="54760-164">元件更新工作流程會產生 Detail_ComponentUpdate.txt 檔，而且與 Detail.txt 類似。</span><span class="sxs-lookup"><span data-stu-id="54760-164">The Detail_ComponentUpdate.txt file is generated for the component update workflow and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-165">Location</span><span class="sxs-lookup"><span data-stu-id="54760-165">Location</span></span>  
 <span data-ttu-id="54760-166">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-166">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="detail_globalrulestxt"></a><span data-ttu-id="54760-167">Detail_GlobalRules.txt</span><span class="sxs-lookup"><span data-stu-id="54760-167">Detail_GlobalRules.txt</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-168">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-168">Overview</span></span>  
 <span data-ttu-id="54760-169">全域規則執行會產生 Detail_GlobalRules.txt，而且與 Detail.txt 類似。</span><span class="sxs-lookup"><span data-stu-id="54760-169">Detail_GlobalRules.txt is generated for the global rules execution and is similar to Detail.txt.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-170">Location</span><span class="sxs-lookup"><span data-stu-id="54760-170">Location</span></span>  
 <span data-ttu-id="54760-171">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-171">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="msi-log-files"></a><span data-ttu-id="54760-172">MSI 記錄檔</span><span class="sxs-lookup"><span data-stu-id="54760-172">MSI log files</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-173">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-173">Overview</span></span>  
 <span data-ttu-id="54760-174">MSI 記錄檔會提供安裝套件程序的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="54760-174">The MSI log files provide details of the installation package process.</span></span> <span data-ttu-id="54760-175">在指定之套件的安裝期間，MSIEXEC 會產生這些記錄檔。</span><span class="sxs-lookup"><span data-stu-id="54760-175">They are generated by the MSIEXEC during the installation of the specified package.</span></span>  
  
 <span data-ttu-id="54760-176">MSI 記錄檔的類型：</span><span class="sxs-lookup"><span data-stu-id="54760-176">Types of MSI log files:</span></span>  
  
-   <span data-ttu-id="54760-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="54760-177">\<Feature>_\<Architecture>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="54760-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span><span class="sxs-lookup"><span data-stu-id="54760-178">\<Feature>_\<Architecture>\_\<Language>\_\<Interaction>.log</span></span>  
  
-   <span data-ttu-id="54760-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span><span class="sxs-lookup"><span data-stu-id="54760-179">\<Feature>_\<Architecture>\_\<Interaction>\_\<workflow>.log</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-180">Location</span><span class="sxs-lookup"><span data-stu-id="54760-180">Location</span></span>  
 <span data-ttu-id="54760-181">MSI 記錄檔位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\<名稱 \> .log。</span><span class="sxs-lookup"><span data-stu-id="54760-181">The MSI log files are located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\<Name\>.log.</span></span>  
  
 <span data-ttu-id="54760-182">檔案的結尾是執行的摘要，其中包含成功或失敗狀態以及屬性。</span><span class="sxs-lookup"><span data-stu-id="54760-182">At the end of the file is a summary of the execution which includes the success or failure status and properties.</span></span> <span data-ttu-id="54760-183">若要尋找 MSI 檔中的錯誤，請搜尋 "value 3"，通常就可以在該字串的附近找到錯誤。</span><span class="sxs-lookup"><span data-stu-id="54760-183">To find the error in the MSI file, search for "value 3" and usually the errors can be found close to the string.</span></span>  
  
## <a name="configurationfileini"></a><span data-ttu-id="54760-184">ConfigurationFile.ini</span><span class="sxs-lookup"><span data-stu-id="54760-184">ConfigurationFile.ini</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-185">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-185">Overview</span></span>  
 <span data-ttu-id="54760-186">組態檔包含安裝期間提供的輸入設定。</span><span class="sxs-lookup"><span data-stu-id="54760-186">The configuration file contains the input settings that are provided during installation.</span></span> <span data-ttu-id="54760-187">該檔案可以用來重新啟動安裝，而不必手動輸入設定。</span><span class="sxs-lookup"><span data-stu-id="54760-187">It can be used to restart the installation without having to enter the settings manually.</span></span> <span data-ttu-id="54760-188">不過，帳號的密碼、PID 與某些參數不會儲存在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="54760-188">However, passwords for the accounts, PID, and some parameters are not saved in the configuration file.</span></span> <span data-ttu-id="54760-189">這些設定可以加入至檔案，或者使用命令列或安裝程式使用者介面提供。</span><span class="sxs-lookup"><span data-stu-id="54760-189">The settings can be either added to the file or provided by using the command line or the Setup user interface.</span></span> <span data-ttu-id="54760-190">如需詳細資訊，請參閱[使用設定檔安裝 SQL Server 2014](install-sql-server-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="54760-190">For more information, see [Install SQL Server 2014 Using a Configuration File](install-sql-server-using-a-configuration-file.md).</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-191">Location</span><span class="sxs-lookup"><span data-stu-id="54760-191">Location</span></span>  
 <span data-ttu-id="54760-192">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-192">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="systemconfigurationcheck_reporthtm"></a><span data-ttu-id="54760-193">SystemConfigurationCheck_Report.htm</span><span class="sxs-lookup"><span data-stu-id="54760-193">SystemConfigurationCheck_Report.htm</span></span>  
  
### <a name="overview"></a><span data-ttu-id="54760-194">概觀</span><span class="sxs-lookup"><span data-stu-id="54760-194">Overview</span></span>  
 <span data-ttu-id="54760-195">系統組態檢查報告包含每個已執行規則以及執行狀態的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="54760-195">The system configuration check report contains a short description for each executed rule, and the execution status.</span></span>  
  
### <a name="location"></a><span data-ttu-id="54760-196">Location</span><span class="sxs-lookup"><span data-stu-id="54760-196">Location</span></span>  
 <span data-ttu-id="54760-197">它位於% programfiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<YYYYMMDD_HHMM>\\ 。</span><span class="sxs-lookup"><span data-stu-id="54760-197">It is located at %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54760-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54760-198">See Also</span></span>  
 <span data-ttu-id="54760-199">[安裝 how to 主題](../../sql-server/install/installation-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="54760-199">[Installation How-to Topics](../../sql-server/install/installation-how-to-topics.md) </span></span>  
 [<span data-ttu-id="54760-200">安裝 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="54760-200">Install SQL Server 2014</span></span>](install-sql-server.md)  
  
  
