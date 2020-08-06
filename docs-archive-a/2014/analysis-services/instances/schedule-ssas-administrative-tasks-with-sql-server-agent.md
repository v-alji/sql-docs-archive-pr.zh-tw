---
title: 使用 SQL Server Agent 排程 SSAS 管理工作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d1484b3-51d9-48a0-93d2-0c3e4ed22b87
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c78fa5fcebc0589ba863163b93ad2d10731b75a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702061"
---
# <a name="schedule-ssas-administrative-tasks-with-sql-server-agent"></a><span data-ttu-id="8da32-102">使用 SQL Server Agent 排程 SSAS 管理工作</span><span class="sxs-lookup"><span data-stu-id="8da32-102">Schedule SSAS Administrative Tasks with SQL Server Agent</span></span>
  <span data-ttu-id="8da32-103">您可以使用 SQL Server Agent 服務來為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理工作排程，以便按照所需的順序和時間執行工作。</span><span class="sxs-lookup"><span data-stu-id="8da32-103">Using the SQL Server Agent service, you can schedule [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrative tasks to run in the order and times that you need.</span></span> <span data-ttu-id="8da32-104">為工作排程可協助您將處理自動化，以便定期或依照可預測的週期執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-104">Scheduled tasks help you automate processes that run on regular or predictable cycles.</span></span> <span data-ttu-id="8da32-105">您可以排程管理工作 (例如 Cube 處理) 在商務活動較少的時間執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-105">You can schedule administrative tasks, such as cube processing, to run during times of slow business activity.</span></span> <span data-ttu-id="8da32-106">此外，您也可以在 SQL Server Agent 作業內建立作業步驟，決定工作執行的順序。</span><span class="sxs-lookup"><span data-stu-id="8da32-106">You can also determine the order in which tasks run by creating job steps within a SQL Server Agent job.</span></span> <span data-ttu-id="8da32-107">例如，您可以先處理 Cube，然後再執行 Cube 的備份。</span><span class="sxs-lookup"><span data-stu-id="8da32-107">For example, you can process a cube and then perform a backup of the cube.</span></span>  
  
 <span data-ttu-id="8da32-108">作業步驟可以讓您控制執行的流程。</span><span class="sxs-lookup"><span data-stu-id="8da32-108">Job steps give you control over flow of execution.</span></span> <span data-ttu-id="8da32-109">如果一項作業失敗，您可以設定 SQL Server Agent 繼續執行其餘工作或停止執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-109">If one job fails, you can configure SQL Server Agent to continue to run the remaining tasks or to stop execution.</span></span> <span data-ttu-id="8da32-110">您也可以設定 SQL Server Agent 傳送有關作業執行成功或失敗的通知。</span><span class="sxs-lookup"><span data-stu-id="8da32-110">You can also configure SQL Server Agent to send notifications about the success or failure of job execution.</span></span>  
  
 <span data-ttu-id="8da32-111">本主題是一項逐步解說，其中示範了兩種使用 SQL Server Agent 來執行 XMLA 指令碼的方式。</span><span class="sxs-lookup"><span data-stu-id="8da32-111">This topic is a walkthrough that shows two ways of using SQL Server Agent to run XMLA script.</span></span> <span data-ttu-id="8da32-112">第一則範例會示範如何排程單一維度的處理。</span><span class="sxs-lookup"><span data-stu-id="8da32-112">The first example demonstrates how to schedule processing of a single dimension.</span></span> <span data-ttu-id="8da32-113">第二則範例會示範如何將處理工作結合成依照排程執行的單一指令碼。</span><span class="sxs-lookup"><span data-stu-id="8da32-113">Example two shows how to combine processing tasks into a single script that runs on a schedule.</span></span> <span data-ttu-id="8da32-114">若要完成此逐步解說，您必須符合下列必要條件。</span><span class="sxs-lookup"><span data-stu-id="8da32-114">To complete this walkthrough, you will need to meet the following prerequisites.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8da32-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8da32-115">Prerequisites</span></span>  
 <span data-ttu-id="8da32-116">您必須安裝 SQL Server Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="8da32-116">SQL Server Agent service must be installed.</span></span>  
  
 <span data-ttu-id="8da32-117">根據預設，作業會在此服務帳戶底下執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-117">By default, jobs run under the service account.</span></span> <span data-ttu-id="8da32-118">在中 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，SQL Server Agent 的預設帳戶是 NT Service\SQLAgent $ \<instancename> 。</span><span class="sxs-lookup"><span data-stu-id="8da32-118">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the default account for SQL Server Agent is NT Service\SQLAgent$\<instancename>.</span></span> <span data-ttu-id="8da32-119">若要執行備份或處理工作，此帳戶必須是 Analysis Services 執行個體的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8da32-119">To perform a backup or processing task, this account must be a system administrator on the Analysis Services instance.</span></span> <span data-ttu-id="8da32-120">如需詳細資訊，請參閱[&#40;Analysis Services&#41;授與伺服器管理員許可權](grant-server-admin-rights-to-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="8da32-120">For more information, see [Grant Server Administrator Permissions &#40;Analysis Services&#41;](grant-server-admin-rights-to-an-analysis-services-instance.md).</span></span>  
  
 <span data-ttu-id="8da32-121">您也應該擁有要使用的測試資料庫。</span><span class="sxs-lookup"><span data-stu-id="8da32-121">You should also have a test database to work with.</span></span> <span data-ttu-id="8da32-122">您可以部署 AdventureWorks 多維度範例資料庫或是要用於此逐步解說之 Analysis Services 多維度教學課程中的專案。</span><span class="sxs-lookup"><span data-stu-id="8da32-122">You can deploy the AdventureWorks multidimensional sample database or a project from the Analysis Services multidimensional tutorial to use in this walkthrough.</span></span> <span data-ttu-id="8da32-123">如需詳細資訊，請參閱[安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](../install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="8da32-123">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../install-sample-data-and-projects.md).</span></span>  
  
## <a name="example-1-processing-a-dimension-in-a-scheduled-task"></a><span data-ttu-id="8da32-124">範例 1：在排程工作中處理維度</span><span class="sxs-lookup"><span data-stu-id="8da32-124">Example 1: Processing a dimension in a scheduled task</span></span>  
 <span data-ttu-id="8da32-125">這則範例會示範如何建立和排程處理維度的作業。</span><span class="sxs-lookup"><span data-stu-id="8da32-125">This example demonstrates how to create and schedule a job that processes a dimension.</span></span>  
  
 <span data-ttu-id="8da32-126">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 排程工作是內嵌至 SQL Server Agent 作業中的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8da32-126">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] scheduled task is an XMLA script that is embedded into a SQL Server Agent job.</span></span> <span data-ttu-id="8da32-127">這項作業已排程在所要的時間與頻率執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-127">This job is scheduled to run at desired times and frequency.</span></span> <span data-ttu-id="8da32-128">由於 SQL Server Agent 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的一部分，因此，您會同時使用 Database Engine 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 來建立並排程管理工作。</span><span class="sxs-lookup"><span data-stu-id="8da32-128">Because the SQL Server Agent is part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you work with both the Database Engine and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create and schedule an administrative task.</span></span>  
  
###  <a name="create-a-script-for-processing-a-dimension-in-a-sql-server-agent-job"></a><a name="bkmk_CreateScript"></a><span data-ttu-id="8da32-129">建立腳本來處理 SQL Server Agent 作業中的維度</span><span class="sxs-lookup"><span data-stu-id="8da32-129">Create a script for processing a dimension in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="8da32-130">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8da32-130">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8da32-131">開啟資料庫資料夾並尋找維度。</span><span class="sxs-lookup"><span data-stu-id="8da32-131">Open a database folder and find a dimension.</span></span> <span data-ttu-id="8da32-132">以滑鼠右鍵按一下維度，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-132">Right-click the dimension and select **Process**.</span></span>  
  
2.  <span data-ttu-id="8da32-133">在 **[處理維度]** 對話方塊中，於 **[物件清單]** 下的 **[處理選項]** 資料行中，確認這個資料行的選項是 **[完整處理]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-133">In the **Process Dimension** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span> <span data-ttu-id="8da32-134">如果不是，請在 [處理選項]\*\*\*\* 底下，按一下選項，然後從下拉式清單中選取 [完整處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-134">If it is not, under **Process Options**, click the option, and then select **Process Full** from the drop-down list.</span></span>  
  
3.  <span data-ttu-id="8da32-135">按一下 **[指令碼]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-135">Click **Script**.</span></span>  
  
     <span data-ttu-id="8da32-136">此步驟會開啟包含處理維度之 XMLA 指令碼的 **[XML 查詢]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="8da32-136">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="8da32-137">在 **[處理維度]** 對話方塊中，按一下 **[取消]** 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8da32-137">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="8da32-138">在 [XMLA 查詢]\*\*\*\* 視窗中，反白顯示 XMLA 指令碼、以滑鼠右鍵按一下反白顯示的指令碼，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-138">In the **XMLA Query** window, highlight the XMLA script, right-click the highlighted script, and select **Copy**.</span></span>  
  
     <span data-ttu-id="8da32-139">此步驟會將 XMLA 指令碼複製到 Windows [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="8da32-139">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="8da32-140">您可以將 XMLA 指令碼保留在 [剪貼簿] 中，也可以將它貼入 [記事本] 或其他文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="8da32-140">You can leave the XMLA script in the Clipboard or paste it into Notepad or another text editor.</span></span> <span data-ttu-id="8da32-141">下面是 XMLA 指令碼的範例。</span><span class="sxs-lookup"><span data-stu-id="8da32-141">The following is an example of the XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Account</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
###  <a name="create-and-schedule-the-dimension-processing-job"></a><a name="bkmk_ProcessJob"></a><span data-ttu-id="8da32-142">建立和排程維度處理作業</span><span class="sxs-lookup"><span data-stu-id="8da32-142">Create and schedule the dimension processing job</span></span>  
  
1.  <span data-ttu-id="8da32-143">連接到 Database Engine 的執行個體，然後開啟 [物件總管]。</span><span class="sxs-lookup"><span data-stu-id="8da32-143">Connect to an instance of the Database Engine and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="8da32-144">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-144">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="8da32-145">以滑鼠右鍵按一下 [作業]\*\*\*\*，然後選取 [新增作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-145">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="8da32-146">在 **[新增作業]** 對話方塊的 **[名稱]** 方塊中，輸入作業名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-146">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="8da32-147">在 **[選取頁面]** 底下，選取 **[步驟]**，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-147">Under **Select a page**, select **Steps**, and then click **New**.</span></span>  
  
6.  <span data-ttu-id="8da32-148">在 **[新增作業步驟]** 對話方塊的 **[步驟名稱]** 中，輸入步驟名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-148">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="8da32-149">在 [**伺服器**] 中，為的預設實例輸入**localhost** ， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 並為指定的實例輸入\*\*localhost \\ \*\* \<*instance name*> 。</span><span class="sxs-lookup"><span data-stu-id="8da32-149">In **Server**, type **localhost** for a default instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and **localhost\\**\<*instance name*> for a named instance.</span></span>  
  
     <span data-ttu-id="8da32-150">如果您要從遠端電腦執行作業，請使用作業執行所在的伺服器名稱和執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-150">If you will be running the job from a remote computer, use the server name and instance name where the job will run.</span></span> <span data-ttu-id="8da32-151">使用 \<*server name*> 預設實例的格式，並針對 \<*server name*> \\ < 已命名的實例>*實例名稱*。</span><span class="sxs-lookup"><span data-stu-id="8da32-151">Use the format \<*server name*> for a default instance, and \<*server name*>\\<*instance name*> for a named instance.</span></span>  
  
8.  <span data-ttu-id="8da32-152">在 **[類型]** 中，選取 **[SQL Server Analysis Services 命令]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-152">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
9. <span data-ttu-id="8da32-153">在 [命令]\*\*\*\* 中，按一下滑鼠右鍵，然後選取 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-153">In **Command**, right-click and select **Paste**.</span></span> <span data-ttu-id="8da32-154">您在上一個步驟中產生的 XMLA 指令碼應該就會出現在命令視窗中。</span><span class="sxs-lookup"><span data-stu-id="8da32-154">The XMLA script that you generated in the previous step should appear in the command window.</span></span>  
  
10. <span data-ttu-id="8da32-155">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8da32-155">Click **OK**.</span></span>  
  
11. <span data-ttu-id="8da32-156">在 **[選取頁面]** 底下，按一下 **[排程]**，然後按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-156">Under **Select a page**, click **Schedules**, and then click **New**.</span></span>  
  
12. <span data-ttu-id="8da32-157">在 **[新增作業排程]** 對話方塊的 **[名稱]** 中，輸入排程名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-157">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8da32-158">此步驟會建立星期日上午 12:00 的排程。</span><span class="sxs-lookup"><span data-stu-id="8da32-158">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="8da32-159">下一個步驟將為您示範如何手動執行作業。</span><span class="sxs-lookup"><span data-stu-id="8da32-159">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="8da32-160">您也可以指定在監視時執行作業的排程。</span><span class="sxs-lookup"><span data-stu-id="8da32-160">You can also specify a schedule that executes the job when you are monitoring it.</span></span>  
  
13. <span data-ttu-id="8da32-161">在 **[新增作業]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-161">In the **New Job** dialog box, click **OK**.</span></span>  
  
14. <span data-ttu-id="8da32-162">在物件總管\*\*\*\* 中，展開 [作業]\*\*\*\*、以滑鼠右鍵按一下您所建立的作業，然後選取 [從下列步驟啟動作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-162">In **Object Explorer**, expand **Jobs**, right-click the job you created, and then select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="8da32-163">因為作業只有一個步驟，所以作業將立即執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-163">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="8da32-164">如果作業包含多個步驟，您就可以選取應該啟動作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="8da32-164">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
15. <span data-ttu-id="8da32-165">當作業完成時，請按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-165">When the job finishes, click **Close**.</span></span>  
  
## <a name="example-2-batch-processing-a-dimension-and-a-partition-in-a-scheduled-task"></a><span data-ttu-id="8da32-166">範例 2：在排程工作中批次處理維度和資料分割</span><span class="sxs-lookup"><span data-stu-id="8da32-166">Example 2: Batch processing a dimension and a partition in a scheduled task</span></span>  
 <span data-ttu-id="8da32-167">這則範例中的程序會示範如何建立和排程批次處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫維度的作業，同時處理相依於此維度進行彙總的 Cube 資料分割。</span><span class="sxs-lookup"><span data-stu-id="8da32-167">The procedures in this example demonstrate how to create and schedule a job that batch processes an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database dimension, and at the same time to process a  cube partition that depends on the dimension for aggregation.</span></span> <span data-ttu-id="8da32-168">如需批次處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的詳細資訊，請參閱[批次處理 &#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8da32-168">For more information about batch processing of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Batch Processing &#40;Analysis Services&#41;](../multidimensional-models/batch-processing-analysis-services.md).</span></span>  
  
###  <a name="create-a-script-for-batch-processing-a-dimension-and-partition-in-a-sql-server-agent-job"></a><a name="bkmk_BatchProcess"></a><span data-ttu-id="8da32-169">在 SQL Server Agent 作業中建立批次處理維度和資料分割的腳本</span><span class="sxs-lookup"><span data-stu-id="8da32-169">Create a script for batch processing a dimension and partition in a SQL Server Agent job</span></span>  
  
1.  <span data-ttu-id="8da32-170">使用相同的資料庫時，展開 [維度]\*\*\*\*、以滑鼠右鍵按一下 [客戶]\*\*\*\* 維度，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-170">Using the same database, expand **Dimensions**, right-click the **Customer** dimension, and select **Process**.</span></span>  
  
2.  <span data-ttu-id="8da32-171">在 **[處理維度]** 對話方塊中，於 **[物件清單]** 下的 **[處理選項]** 資料行中，確認這個資料行的選項是 **[完整處理]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-171">In the **Process Dimension** dialog box, in **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
3.  <span data-ttu-id="8da32-172">按一下 **[指令碼]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-172">Click **Script**.</span></span>  
  
     <span data-ttu-id="8da32-173">此步驟會開啟包含處理維度之 XMLA 指令碼的 **[XML 查詢]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="8da32-173">This step opens an **XML Query** window that contains the XMLA script that processes the dimension.</span></span>  
  
4.  <span data-ttu-id="8da32-174">在 **[處理維度]** 對話方塊中，按一下 **[取消]** 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8da32-174">In the **Process Dimension** dialog box, click **Cancel** to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="8da32-175">依序展開 [Cube]\*\*\*\*、[Adventure Works]\*\*\*\*、[量值群組]\*\*\*\*、[網際網路銷售]\*\*\*\* 和 [資料分割]\*\*\*\*、以滑鼠右鍵按一下清單中的最後一個資料分割，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-175">Expand **Cubes**, expand **Adventure Works**, expand **Measure Groups**, expand **Internet Sales**, expand **Partitions**, right-click the last partition in the list, and then select **Process**.</span></span>  
  
6.  <span data-ttu-id="8da32-176">在 **[處理資料分割]** 對話方塊中，於 **[物件清單]** 下的 **[處理選項]** 資料行中，確認這個資料行的選項是 **[完整處理]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-176">In the **Process Partition** dialog box, in the **Process Options** column under **Object list**, verify that the option for this column is **Process Full**.</span></span>  
  
7.  <span data-ttu-id="8da32-177">按一下 **[指令碼]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-177">Click **Script**.</span></span>  
  
     <span data-ttu-id="8da32-178">此步驟會開啟第二個 **[XML 查詢]** 視窗，其中包含處理資料分割的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8da32-178">This step opens a second **XML Query** window that contains the XMLA script that processes the partition.</span></span>  
  
8.  <span data-ttu-id="8da32-179">在 **[處理資料分割]** 對話方塊中，按一下 **[取消]** 關閉編輯器。</span><span class="sxs-lookup"><span data-stu-id="8da32-179">In the **Process Partition** dialog box, click **Cancel** to close the editor.</span></span>  
  
     <span data-ttu-id="8da32-180">此時，您必須合併這兩個指令碼，並且確保系統先處理維度。</span><span class="sxs-lookup"><span data-stu-id="8da32-180">At this point you must merge the two scripts, and ensure that the dimension is processed first.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="8da32-181">如果系統先處理資料分割，後續的維度處理就會導致資料分割變成尚未處理。</span><span class="sxs-lookup"><span data-stu-id="8da32-181">If the partition is processed first, the subsequent dimension processing causes the partition to become unprocessed.</span></span> <span data-ttu-id="8da32-182">然後，資料分割需要第二次處理，才能達成已處理狀態。</span><span class="sxs-lookup"><span data-stu-id="8da32-182">The partition would then require a second processing to reach a processed state.</span></span>  
  
9. <span data-ttu-id="8da32-183">在包含處理資料分割之 XMLA 指令碼的 [XMLA 查詢]\*\*\*\* 視窗中，反白顯示 `Batch` 和 `Parallel` 標記內部的程式碼、以滑鼠右鍵按一下反白顯示的指令碼，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-183">In the **XMLA Query** window that contains the XMLA script that processes the partition, highlight the code inside the `Batch` and `Parallel` tags, right-click the highlighted script, and select **Copy**.</span></span>  
  
    ```  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID> Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID> Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
    ```  
  
10. <span data-ttu-id="8da32-184">開啟包含處理維度之 XMLA 指令碼的 **[XMLA 查詢]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="8da32-184">Open the **XMLA Query** window that contains the XMLA script that processes the dimension.</span></span> <span data-ttu-id="8da32-185">在 `</Process>` 標記左邊的指令碼中按一下滑鼠右鍵，然後選取 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-185">Right-click within the script to the left of the `</Process>` tag and select **Paste**.</span></span>  
  
     <span data-ttu-id="8da32-186">下列範例顯示已修訂的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8da32-186">The following example shows the revised XMLA script.</span></span>  
  
    ```  
    <Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
     <Parallel>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <DimensionID>Dim Customer</DimensionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
      <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
        <Object>  
          <DatabaseID>Adventure Works DW Multidimensional</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID>Internet_Sales_2004</PartitionID>  
        </Object>  
        <Type>ProcessFull</Type>  
        <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
      </Process>  
     </Parallel>  
    </Batch>  
    ```  
  
11. <span data-ttu-id="8da32-187">反白顯示已修訂的 XMLA 指令碼、以滑鼠右鍵按一下反白顯示的指令碼，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-187">Highlight the revised XMLA script, right-click the highlighted script, and select **Copy.**</span></span>  
  
12. <span data-ttu-id="8da32-188">此步驟會將 XMLA 指令碼複製到 Windows [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="8da32-188">This step copies the XMLA script to the Windows Clipboard.</span></span> <span data-ttu-id="8da32-189">您可以將 XMLA 指令碼保留在 [剪貼簿] 中、將它儲存至檔案，也可以將它貼入 [記事本] 或其他文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="8da32-189">You can leave the XMLA script in the Clipboard, save it to a file, or paste it into Notepad or another text editor.</span></span>  
  
###  <a name="create-and-schedule-the-batch-processing-job"></a><a name="bkmk_Scheduling"></a><span data-ttu-id="8da32-190">建立和排程批次處理作業</span><span class="sxs-lookup"><span data-stu-id="8da32-190">Create and schedule the batch processing job</span></span>  
  
1.  <span data-ttu-id="8da32-191">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體，然後開啟 [物件總管]。</span><span class="sxs-lookup"><span data-stu-id="8da32-191">Connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then open Object Explorer.</span></span>  
  
2.  <span data-ttu-id="8da32-192">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-192">Expand **SQL Server Agent**.</span></span> <span data-ttu-id="8da32-193">如果此服務並未執行，請啟動它。</span><span class="sxs-lookup"><span data-stu-id="8da32-193">Start the service if is not running.</span></span>  
  
3.  <span data-ttu-id="8da32-194">以滑鼠右鍵按一下 [作業]\*\*\*\*，然後選取 [新增作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-194">Right-click **Jobs** and select **New Job**.</span></span>  
  
4.  <span data-ttu-id="8da32-195">在 **[新增作業]** 對話方塊的 **[名稱]** 方塊中，輸入作業名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-195">In the **New Job** dialog box, enter a job name in **Name**.</span></span>  
  
5.  <span data-ttu-id="8da32-196">在 **[步驟]** 中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-196">In **Steps**, click **New**.</span></span>  
  
6.  <span data-ttu-id="8da32-197">在 **[新增作業步驟]** 對話方塊的 **[步驟名稱]** 中，輸入步驟名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-197">In the **New Job Step** dialog box, enter a step name in **Step Name**.</span></span>  
  
7.  <span data-ttu-id="8da32-198">在 **[類型]** 中，選取 **[SQL Server Analysis Services 命令]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-198">In **Type**, select **SQL Server Analysis Services Command**.</span></span>  
  
8.  <span data-ttu-id="8da32-199">在 **[執行身分]** 中，選取 **[SQL Server Agent 服務帳戶]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-199">In **Run as**, select the **SQL Server Agent Service Account**.</span></span> <span data-ttu-id="8da32-200">正如＜必要條件＞一節所述，此帳戶必須擁有 Analysis Services 的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="8da32-200">Recall from the Prerequisites section that this account must have administrative permissions on Analysis Services.</span></span>  
  
9. <span data-ttu-id="8da32-201">在 **[伺服器]** 中，指定 Analysis Services 執行個體的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="8da32-201">In **Server**, specify the server name of the Analysis Services instance.</span></span>  
  
10. <span data-ttu-id="8da32-202">在 [命令]\*\*\*\* 中，按一下滑鼠右鍵，然後選取 [貼上]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-202">In **Command**, right-click and select **Paste**.</span></span>  
  
11. <span data-ttu-id="8da32-203">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8da32-203">Click **OK**.</span></span>  
  
12. <span data-ttu-id="8da32-204">在 **[排程]** 頁面中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-204">In the **Schedules** page, click **New**.</span></span>  
  
13. <span data-ttu-id="8da32-205">在 **[新增作業排程]** 對話方塊的 **[名稱]** 中，輸入排程名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-205">In the **New Job Schedule** dialog box, enter a schedule name in **Name**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8da32-206">此步驟會建立星期日上午 12:00 的排程。</span><span class="sxs-lookup"><span data-stu-id="8da32-206">This step creates a schedule for Sunday at 12:00 AM.</span></span> <span data-ttu-id="8da32-207">下一個步驟將為您示範如何手動執行作業。</span><span class="sxs-lookup"><span data-stu-id="8da32-207">The next step shows you how to manually execute the job.</span></span> <span data-ttu-id="8da32-208">您也可以選取在監視時執行作業的排程。</span><span class="sxs-lookup"><span data-stu-id="8da32-208">You can also select a schedule which will execute the job when you are monitoring it.</span></span>  
  
14. <span data-ttu-id="8da32-209">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8da32-209">Click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="8da32-210">在物件總管\*\*\*\* 中，展開 [作業]\*\*\*\*、以滑鼠右鍵按一下您所建立的作業，然後選取 [從下列步驟啟動作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8da32-210">In **Object Explorer**, expand **Jobs**, right-click the job you created, and select **Start Job at Step**.</span></span>  
  
     <span data-ttu-id="8da32-211">因為作業只有一個步驟，所以作業將立即執行。</span><span class="sxs-lookup"><span data-stu-id="8da32-211">Because the job has only one step, the job executes immediately.</span></span> <span data-ttu-id="8da32-212">如果作業包含多個步驟，您就可以選取應該啟動作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="8da32-212">If the job contains more than one step, you can select the step at which the job should start.</span></span>  
  
16. <span data-ttu-id="8da32-213">當作業完成時，請按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="8da32-213">When the job finishes, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da32-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8da32-214">See Also</span></span>  
 <span data-ttu-id="8da32-215">[處理選項和設定 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="8da32-215">[Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md) </span></span>  
 [<span data-ttu-id="8da32-216">在 Analysis Services 中編寫管理工作的指令碼</span><span class="sxs-lookup"><span data-stu-id="8da32-216">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  
