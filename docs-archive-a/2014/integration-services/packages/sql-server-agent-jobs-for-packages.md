---
title: 套件的 SQL Server Agent 作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eb9c1cf39ab5120958c33dfeff24588d59f71307
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596086"
---
# <a name="sql-server-agent-jobs-for-packages"></a><span data-ttu-id="d1283-102">封裝的 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="d1283-102">SQL Server Agent Jobs for Packages</span></span>
  <span data-ttu-id="d1283-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來自動化並排程 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件的執行。</span><span class="sxs-lookup"><span data-stu-id="d1283-103">You can automate and schedule the execution of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="d1283-104">您可以排程部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器，並且儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區及檔案系統的封裝。</span><span class="sxs-lookup"><span data-stu-id="d1283-104">You can schedule packages that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, and are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span>  
  
## <a name="sections-in-this-topic"></a><span data-ttu-id="d1283-105">本主題的章節</span><span class="sxs-lookup"><span data-stu-id="d1283-105">Sections in This Topic</span></span>  
 <span data-ttu-id="d1283-106">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d1283-106">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d1283-107">在 SQL Server Agent 中排程作業</span><span class="sxs-lookup"><span data-stu-id="d1283-107">Scheduling jobs in SQL Server Agent</span></span>](#jobs)  
  
-   [<span data-ttu-id="d1283-108">排程 Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="d1283-108">Scheduling Integration Services packages</span></span>](#packages)  
  
-   [<span data-ttu-id="d1283-109">疑難排解已排程封裝</span><span class="sxs-lookup"><span data-stu-id="d1283-109">Troubleshooting scheduled packages</span></span>](#trouble)  
  
##  <a name="scheduling-jobs-in-sql-server-agent"></a><a name="jobs"></a> <span data-ttu-id="d1283-110">Scheduling Jobs in SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="d1283-110">Scheduling Jobs in SQL Server Agent</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d1283-111">Agent 是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所安裝的服務，可讓您透過執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，以自動化並排程工作。</span><span class="sxs-lookup"><span data-stu-id="d1283-111">Agent is the service installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that lets you automate and schedule tasks by running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span> <span data-ttu-id="d1283-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務必須先執行，作業才能自動執行。</span><span class="sxs-lookup"><span data-stu-id="d1283-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service must be running before jobs can run automatically.</span></span> <span data-ttu-id="d1283-113">如需詳細資訊，請參閱 [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-113">For more information, see [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="d1283-114">當您連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體時，[SQL Server Agent] 節點會出現在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的物件總管中。</span><span class="sxs-lookup"><span data-stu-id="d1283-114">The **SQL Server Agent** node appears in Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] when you connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d1283-115">若要自動化週期性工作，請使用 [新增作業] 對話方塊建立作業。</span><span class="sxs-lookup"><span data-stu-id="d1283-115">To automate a recurring task, you create a job by using the **New Job** dialog box.</span></span> <span data-ttu-id="d1283-116">如需詳細資訊，請參閱 [實作作業](../../ssms/agent/implement-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-116">For more information, see [Implement Jobs](../../ssms/agent/implement-jobs.md).</span></span>  
  
 <span data-ttu-id="d1283-117">建立作業後，您必須加入至少一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d1283-117">After you create the job, you must add at least one step.</span></span> <span data-ttu-id="d1283-118">作業可以包含多個步驟，且每個步驟都能執行不同的工作。</span><span class="sxs-lookup"><span data-stu-id="d1283-118">A job can include multiple steps, and each step can perform a different task.</span></span> <span data-ttu-id="d1283-119">如需詳細資訊，請參閱 [Manage Job Steps](../../ssms/agent/manage-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-119">For more information, see [Manage Job Steps](../../ssms/agent/manage-job-steps.md).</span></span>  
  
 <span data-ttu-id="d1283-120">在建立作業和步驟後，您就可以建立執行該作業的排程。</span><span class="sxs-lookup"><span data-stu-id="d1283-120">After you create the job and the job steps, you can create a schedule for running the job.</span></span> <span data-ttu-id="d1283-121">不過，您也可以建立以手動方式執行的未排程作業。</span><span class="sxs-lookup"><span data-stu-id="d1283-121">However you can also create an unscheduled job that you run manually.</span></span> <span data-ttu-id="d1283-122">如需詳細資訊，請參閱 [建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-122">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
 <span data-ttu-id="d1283-123">透過設定通知選項可以加強作業，例如，指定作業完成時要向其傳送電子郵件的操作員，或加入警示。</span><span class="sxs-lookup"><span data-stu-id="d1283-123">You can enhance the job by setting notification options, such as specifying an operator to send an e-mail message to when the job finishes, or adding alerts.</span></span> <span data-ttu-id="d1283-124">如需詳細資訊，請參閱 [警示](../../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-124">For more information, see [Alerts](../../ssms/agent/alerts.md).</span></span>  
  
##  <a name="scheduling-integration-services-packages"></a><a name="packages"></a> <span data-ttu-id="d1283-125">Scheduling Integration Services Packages</span><span class="sxs-lookup"><span data-stu-id="d1283-125">Scheduling Integration Services Packages</span></span>  
 <span data-ttu-id="d1283-126">當您建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業來排程 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時，必須加入至少一個步驟，並將該步驟的類型設為 [SQL Server Integration Services 封裝]。</span><span class="sxs-lookup"><span data-stu-id="d1283-126">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job to schedule [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you must add at least one step and set the type of the step to **SQL Server Integration Services Package**.</span></span> <span data-ttu-id="d1283-127">作業可以包含多個步驟，且每個步驟都能執行不同的封裝。</span><span class="sxs-lookup"><span data-stu-id="d1283-127">A job can include multiple steps, and each step can run a different package.</span></span>  
  
 <span data-ttu-id="d1283-128">從作業步驟執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，如同使用 **dtexec** (dtexec.exe) 和 **DTExecUI** (dtexecui.exe) 公用程式來執行封裝。</span><span class="sxs-lookup"><span data-stu-id="d1283-128">Running an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package from a job step is like running a package by using the **dtexec** (dtexec.exe) and **DTExecUI** (dtexecui.exe) utilities.</span></span> <span data-ttu-id="d1283-129">但不是透過使用命令列選項或 [執行封裝公用程式] 對話方塊來設定封裝的執行階段選項，而是在 [新增作業步驟] 對話方塊設定執行階段選項。</span><span class="sxs-lookup"><span data-stu-id="d1283-129">Instead of setting the run-time options for a package by using command-line options or the **Execute Package Utility** dialog box, you set the run-time options in the **New Job Step** dialog box.</span></span> <span data-ttu-id="d1283-130">如需執行封裝之選項的詳細資訊，請參閱 [dtexec 公用程式](dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-130">For more information about the options for running a package, see [dtexec Utility](dtexec-utility.md).</span></span>  
  
 <span data-ttu-id="d1283-131">如需詳細資訊，請參閱 [使用 SQL Server Agent 排程封裝](../schedule-a-package-by-using-sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-131">For more information, see [Schedule a Package by using SQL Server Agent](../schedule-a-package-by-using-sql-server-agent.md).</span></span>  
  
 <span data-ttu-id="d1283-132">如需示範如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式執行套件的影片，請參閱影片首頁的[如何：使用 SQL Server Agent 自動化執行套件 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=141771)，位於 MSDN Library。</span><span class="sxs-lookup"><span data-stu-id="d1283-132">For a video that demonstrates how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a package, see the video home page, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library.</span></span>  
  
##  <a name="troubleshooting"></a><a name="trouble"></a> <span data-ttu-id="d1283-133">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d1283-133">Troubleshooting</span></span>  
 <span data-ttu-id="d1283-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟可能無法啟動封裝，即使封裝在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中以及從命令列都順利執行。</span><span class="sxs-lookup"><span data-stu-id="d1283-134">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step may fail to start a package even though the package runs successfully in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and from the command line.</span></span> <span data-ttu-id="d1283-135">此問題有一些常見的原因，以及數個建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d1283-135">There are some common reasons for this issue and several recommended solutions.</span></span> <span data-ttu-id="d1283-136">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="d1283-136">For more information, see the following resources.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d1283-137">知識庫文件： [從 SQL Server Agent 作業步驟呼叫 SSIS 封裝時，SSIS 封裝未執行](https://support.microsoft.com/kb/918760)</span><span class="sxs-lookup"><span data-stu-id="d1283-137">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760)</span></span>  
  
-   <span data-ttu-id="d1283-138">影片，[疑難排解：使用 SQL Server Agent 執行套件 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=141772)，位於 MSDN Library。</span><span class="sxs-lookup"><span data-stu-id="d1283-138">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library.</span></span>  
  
 <span data-ttu-id="d1283-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟啟動封裝後，封裝執行可能失敗，也可能會成功，但產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="d1283-139">After a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step starts a package, the package execution may fail or the package may run successfully but with unexpected results.</span></span> <span data-ttu-id="d1283-140">您可以使用下列工具對這些問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="d1283-140">You can use the following tools to troubleshoot these issues.</span></span>  
  
-   <span data-ttu-id="d1283-141">對於儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB 資料庫、[!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區，或是本機電腦上資料夾中的封裝，您可以使用 [記錄檔檢視器]，以及在封裝執行期間所產生的任何記錄檔和偵錯傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="d1283-141">For packages that are stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] MSDB database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, or in a folder on your local machine, you can use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span>  
  
     <span data-ttu-id="d1283-142">**若要使用記錄檔檢視器，請執行下列操作。**</span><span class="sxs-lookup"><span data-stu-id="d1283-142">**To use the Log File Viewer, do the following.**</span></span>  
  
    1.  <span data-ttu-id="d1283-143">在物件總管中以滑鼠右鍵按一下 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業]，然後按一下 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="d1283-143">Right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in Object Explorer and then click **View History**.</span></span>  
  
    2.  <span data-ttu-id="d1283-144">利用 [訊息] 資料行中的 [作業失敗] 訊息，尋找 [記錄檔摘要] 方塊中的作業執行。</span><span class="sxs-lookup"><span data-stu-id="d1283-144">Locate the job execution in the **Log file summary** box with the **job failed** message in the **Message** column.</span></span>  
  
    3.  <span data-ttu-id="d1283-145">展開作業節點，然後按一下作業步驟，檢視 [記錄檔摘要] 方塊下方區域中訊息的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1283-145">Expand the job node, and click the job step to view the details of the message in the area below the **Log file summary** box.</span></span>  
  
-   <span data-ttu-id="d1283-146">對於儲存在 SSISDB 資料庫中的封裝，您也可以使用 [記錄檔檢視器]，以及在封裝執行期間所產生的任何記錄檔和偵錯傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="d1283-146">For packages that are stored in the SSISDB database, you can also use the **Log File Viewer** as well as any logs and debug dump files that were generated during the execution of the package.</span></span> <span data-ttu-id="d1283-147">此外，您可以使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的報表。</span><span class="sxs-lookup"><span data-stu-id="d1283-147">In addition, you can use the reports for the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="d1283-148">**若要在報表中尋找與作業執行相關聯之封裝執行的資訊，請執行下列操作。**</span><span class="sxs-lookup"><span data-stu-id="d1283-148">**To find information in the reports for the package execution associated with a job execution, do the following.**</span></span>  
  
    1.  <span data-ttu-id="d1283-149">依照上述步驟檢視作業步驟之訊息的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1283-149">Follow the steps above to view the details of the message for the job step.</span></span>  
  
    2.  <span data-ttu-id="d1283-150">尋找訊息中列出的執行識別碼。</span><span class="sxs-lookup"><span data-stu-id="d1283-150">Locate the Execution ID listed in the message.</span></span>  
  
    3.  <span data-ttu-id="d1283-151">在 [物件總管] 中展開 [Integration Services 目錄] 節點。</span><span class="sxs-lookup"><span data-stu-id="d1283-151">Expand the Integration Services Catalog node in Object Explorer.</span></span>  
  
    4.  <span data-ttu-id="d1283-152">以滑鼠右鍵按一下 [SSISDB]，然後依序指向 [報表]、[標準報表]，再按一下 [所有執行]。</span><span class="sxs-lookup"><span data-stu-id="d1283-152">Right-click SSISDB, point to Reports, then Standard Reports, and then click All Executions.</span></span>  
  
    5.  <span data-ttu-id="d1283-153">在 [所有執行] 報表中，於 [識別碼] 資料行中尋找執行識別碼。</span><span class="sxs-lookup"><span data-stu-id="d1283-153">In the **All Executions** report, locate the Execution ID in the **ID** column.</span></span> <span data-ttu-id="d1283-154">按一下 [概觀]、[所有訊息] 或 [執行效能]，檢視此封裝執行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d1283-154">Click **Overview**, **All Messages**, or **Execution Performance** to view information about this package execution.</span></span>  
  
         <span data-ttu-id="d1283-155">如需 [概觀]、[所有訊息] 和 [執行效能] 報告的詳細資訊，請參閱 [Integration Services 伺服器的報表](../reports-for-the-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d1283-155">For more information about the Overview, All Messages, and Execution Performance reports, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d1283-156">外部資源</span><span class="sxs-lookup"><span data-stu-id="d1283-156">External Resources</span></span>  
  
-   <span data-ttu-id="d1283-157">[網站上的知識庫文件：](https://support.microsoft.com/kb/918760)從 SQL Server Agent 作業步驟呼叫 SSIS 封裝時，SSIS 封裝未執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1283-157">Knowledge Base article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760), on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site</span></span>  
  
-   <span data-ttu-id="d1283-158">影片，[疑難排解：使用 SQL Server Agent 執行套件 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=141772)，位於 MSDN Library</span><span class="sxs-lookup"><span data-stu-id="d1283-158">Video, [Troubleshooting: Package Execution Using SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141772), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="d1283-159">影片，[如何：使用 SQL Server Agent 自動化執行套件 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=141771)，位於 MSDN Library</span><span class="sxs-lookup"><span data-stu-id="d1283-159">Video, [How to: Automate Package Execution by Using the SQL Server Agent (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=141771), in the MSDN Library</span></span>  
  
-   <span data-ttu-id="d1283-160">位於 mssqltips.com 的技術文件： [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675)(使用 Windows PowerShell 檢查 SQL Server Agent 作業)</span><span class="sxs-lookup"><span data-stu-id="d1283-160">Technical article, [Checking SQL Server Agent jobs using Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=165675), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="d1283-161">mssqltips.com 上的技術文件： [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676)(於 SQL Agent 作業已啟用或停用時自動警示)</span><span class="sxs-lookup"><span data-stu-id="d1283-161">Technical article, [Auto alert for SQL Agent jobs when they are enabled or disabled](https://go.microsoft.com/fwlink/?LinkId=165676), on mssqltips.com</span></span>  
  
-   <span data-ttu-id="d1283-162">mssqltips.com 上的部落格文章： [Configuring SQL Agent Jobs to Write to Windows Event Log](https://go.microsoft.com/fwlink/?LinkId=220745)(將 SQL 代理程式工作設定成寫入 Windows 事件記錄檔)。</span><span class="sxs-lookup"><span data-stu-id="d1283-162">Blog entry, [Configuring SQL Agent Jobs to Write to Windows Event Log](https://go.microsoft.com/fwlink/?LinkId=220745), on mssqltips.com.</span></span>  
  
  
