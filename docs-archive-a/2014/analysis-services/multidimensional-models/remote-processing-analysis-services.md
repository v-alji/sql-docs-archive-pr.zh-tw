---
title: 遠端處理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e0d6ade25f5a321e49c748692a961abc369efad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597408"
---
# <a name="remote-processing-analysis-services"></a><span data-ttu-id="3e515-102">遠端處理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="3e515-102">Remote Processing (Analysis Services)</span></span>
  <span data-ttu-id="3e515-103">您可以執行遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的排程處理或自動處理，其只會處理某電腦所發出的要求，但會在同一網路中的另一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="3e515-103">You can run scheduled or unattended processing on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, where the processing request originates from one computer but executes on another computer on the same network.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3e515-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3e515-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="3e515-105">您的每部電腦上若各自執行不同版本的 SQL Server，則用戶端程式庫的版本與處理此模型之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的版本必須相符。</span><span class="sxs-lookup"><span data-stu-id="3e515-105">If you are running different versions of SQL Server on each computer, the client libraries must match the version of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance that is processing the model.</span></span> <span data-ttu-id="3e515-106">例如，若處理在 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 執行個體上進行，則發出要求的電腦便須擁有和 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]相同的用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="3e515-106">For example, if processing is on a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] instance, then the computer from which the request originates must have the client library corresponding to [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span> <span data-ttu-id="3e515-107">請參閱 [用於 Analysis Services 連接的資料提供者](../instances/data-providers-used-for-analysis-services-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="3e515-107">See [Data providers used for Analysis Services connections](../instances/data-providers-used-for-analysis-services-connections.md).</span></span>  
  
-   <span data-ttu-id="3e515-108">遠端伺服器必須啟用 [允許遠端連線到此電腦] \*\*\*\* ，而發出處理要求的帳戶必須列名為允許的使用者。</span><span class="sxs-lookup"><span data-stu-id="3e515-108">On the remote server, **Allow remote connections to this computer** must be enabled, and the account issuing the processing request must be listed as an allowed user.</span></span>  
  
-   <span data-ttu-id="3e515-109">Windows 防火牆規則必須設定為允許 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的傳入連線。</span><span class="sxs-lookup"><span data-stu-id="3e515-109">Windows firewall rules must be configured to allow inbound connections to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="3e515-110">確認您可以使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接遠端 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e515-110">Verify you can connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3e515-111">請參閱 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)。</span><span class="sxs-lookup"><span data-stu-id="3e515-111">See [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="3e515-112">解決現有的本機處理錯誤，然後再嘗試遠端處理。</span><span class="sxs-lookup"><span data-stu-id="3e515-112">Resolve any existing local processing errors before attempting remote processing.</span></span> <span data-ttu-id="3e515-113">確認當處理要求來自本機時，可以順利從外部關聯式資料來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="3e515-113">Verify that when the processing request is local, data can be successfully retrieved from the external relational data source.</span></span> <span data-ttu-id="3e515-114">如需指定用來擷取資料之認證相關指示，請參閱[設定模擬選項 (SSAS - 多維度)](set-impersonation-options-ssas-multidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="3e515-114">See [Set Impersonation Options &#40;SSAS - Multidimensional&#41;](set-impersonation-options-ssas-multidimensional.md) for instructions on specifying credentials used to retrieve data.</span></span>  
  
## <a name="on-demand-remote-processing"></a><span data-ttu-id="3e515-115">隨選遠端處理</span><span class="sxs-lookup"><span data-stu-id="3e515-115">On-demand remote processing</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="3e515-116">接受具有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 系統管理員權限之使用者或應用程式帳戶所發出的處理要求。</span><span class="sxs-lookup"><span data-stu-id="3e515-116">accepts processing requests from user or application accounts that have [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator permissions.</span></span> <span data-ttu-id="3e515-117">您若是系統管理員，請確認您可以連接到遠端執行個體，並可透過遠端連接手動處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="3e515-117">If you are an administrator, verify that you can connect to the remote instance and process the database manually over the remote connection.</span></span>  
  
1.  <span data-ttu-id="3e515-118">在要用於排程處理電腦上啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，並連接到遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e515-118">On the computer that will be used to schedule processing, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="3e515-119">在資料庫上按一下滑鼠右鍵，再選取 [處理序]\*\*\*\* 並指向 [指令碼]\*\*\*\*，然後選擇 [編寫動作的指令碼至新增查詢視窗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3e515-119">Right-click the database, select **Process**, point to **Script** and choose **Script Action to New Query Window**.</span></span> <span data-ttu-id="3e515-120">用於叫用處理的命令會出現在查詢視窗中。</span><span class="sxs-lookup"><span data-stu-id="3e515-120">Commands used to invoke processing will appear in the query window.</span></span>  
  
3.  <span data-ttu-id="3e515-121">按一下 [確定] \*\*\*\* 開始執行處理序。</span><span class="sxs-lookup"><span data-stu-id="3e515-121">Click **OK** to begin processing.</span></span>  
  
     <span data-ttu-id="3e515-122">此工作若是成功，將會提供 XMLA 查詢讓您嵌入排程的作業中。</span><span class="sxs-lookup"><span data-stu-id="3e515-122">Successful completion of this task provides an XMLA query that you can embed in a scheduled job.</span></span> <span data-ttu-id="3e515-123">此工作也會確認連接沒有問題。</span><span class="sxs-lookup"><span data-stu-id="3e515-123">It also confirms there are no connection problems.</span></span>  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a><span data-ttu-id="3e515-124">使用 SQL Server Agent 服務排程遠端處理</span><span class="sxs-lookup"><span data-stu-id="3e515-124">Schedule remote processing using SQL Server Agent Service</span></span>  
 <span data-ttu-id="3e515-125">SQL Server Agent 服務預設會以虛擬帳戶執行，並使用電腦帳戶所建立的網路連接。</span><span class="sxs-lookup"><span data-stu-id="3e515-125">By default, SQL Server Agent service runs under a virtual account, with network connections made using the machine account.</span></span> <span data-ttu-id="3e515-126">為避免授與遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上之電腦帳戶的系統管理權限，應將 SQL Server Agent 服務變更為以最低權限的網域使用者帳戶身分執行。</span><span class="sxs-lookup"><span data-stu-id="3e515-126">To avoid having to give a machine account administrative rights on the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, you should change the SQL Server Agent service account to run as a least-privilege domain user account.</span></span>  
  
 <span data-ttu-id="3e515-127">請務必授與帳戶所有必要的權限，包括提供此服務之 Database Engine 執行個體的 **sysadmin** 權限。</span><span class="sxs-lookup"><span data-stu-id="3e515-127">Be sure to grant all of the necessary permissions, including giving the account **sysadmin** rights on the Database Engine instance providing the service.</span></span>  
  
 <span data-ttu-id="3e515-128">您可以使用下列連結來設定權限：</span><span class="sxs-lookup"><span data-stu-id="3e515-128">Use the following links to set permissions:</span></span>  
  
-   [<span data-ttu-id="3e515-129">設定 SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="3e515-129">Configure SQL Server Agent</span></span>](../../ssms/agent/configure-sql-server-agent.md)  
  
-   <span data-ttu-id="3e515-130">若無法授與[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) 權限， **SQL Server Agent Components** 建議使用替代的固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="3e515-130">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) suggests alternative fixed server roles if granting **sysadmin** permissions is not possible.</span></span>  
  
 <span data-ttu-id="3e515-131">設定帳戶權限之後，請繼續執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="3e515-131">After account permissions are configured, continue with these steps.</span></span>  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a><span data-ttu-id="3e515-132">授與 SSAS 上之 SQL Server Agent 帳戶的系統管理員權限</span><span class="sxs-lookup"><span data-stu-id="3e515-132">Grant the SQL Server Agent account administrator permission on SSAS</span></span>  
  
1.  <span data-ttu-id="3e515-133">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]連接到遠端 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e515-133">Using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="3e515-134">在伺服器名稱上按一下滑鼠右鍵，再按一下 [屬性]\*\*\*\*，然後按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3e515-134">Right-click the server name, click P**roperties**, and then click **Security**.</span></span>  
  
3.  <span data-ttu-id="3e515-135">按一下 [加入] \*\*\*\* ，以加入 SQL Server Agent 帳戶。</span><span class="sxs-lookup"><span data-stu-id="3e515-135">Click **Add** to add the SQL Server Agent account.</span></span>  
  
#### <a name="create-the-job"></a><span data-ttu-id="3e515-136">建立作業</span><span class="sxs-lookup"><span data-stu-id="3e515-136">Create the Job</span></span>  
  
1.  <span data-ttu-id="3e515-137">在 Management Studio 中，連接到本機 Database Engine 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e515-137">In Management Studio, connect to the local Database Engine instance.</span></span> <span data-ttu-id="3e515-138">SQL Server Agent 是物件總管中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="3e515-138">SQL Server Agent is the last item in Object Explorer.</span></span> <span data-ttu-id="3e515-139">如有必要，請啟動該服務。</span><span class="sxs-lookup"><span data-stu-id="3e515-139">If necessary, start the service.</span></span>  
  
2.  <span data-ttu-id="3e515-140">在 [作業]\*\*\*\* 上按一下滑鼠右鍵，再按一下 [新增作業]\*\*\*\*，然後輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="3e515-140">Right-click **Job**s, click **New Job** and then enter a name.</span></span>  
  
3.  <span data-ttu-id="3e515-141">在步驟中按一下 [新增] \*\*\*\* ，然後輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="3e515-141">In Steps, click **New** and then enter a name.</span></span>  
  
4.  <span data-ttu-id="3e515-142">在 [類型] 中，選取 [SQL Server Analysis Services 命令] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3e515-142">In Type, choose **SQL Server Analysis Services Command**.</span></span>  
  
5.  <span data-ttu-id="3e515-143">在 [伺服器] 中，輸入遠端名稱 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e515-143">In Server, enter the name of the remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
6.  <span data-ttu-id="3e515-144">在 [命令] 中，貼上用以處理資料庫的 XMLA 命令。</span><span class="sxs-lookup"><span data-stu-id="3e515-144">In Command, paste the XMLA command for processing the database.</span></span> <span data-ttu-id="3e515-145">這就是您在隨選遠端處理之驗證步驟中所產生的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3e515-145">This is the XMLA script that you generated in the verification step for on-demand remote processing.</span></span> <span data-ttu-id="3e515-146">按一下 **[確定]** 以儲存作業。</span><span class="sxs-lookup"><span data-stu-id="3e515-146">Click **OK** to save the job.</span></span>  
  
#### <a name="start-sql-server-profiler"></a><span data-ttu-id="3e515-147">啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="3e515-147">Start SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="3e515-148">在遠端電腦上，啟動 SQL Server Profiler。</span><span class="sxs-lookup"><span data-stu-id="3e515-148">On the remote computer, start SQL Server Profiler.</span></span> <span data-ttu-id="3e515-149">連接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體，然後按一下 [執行] \*\*\*\* ，以啟動使用預設事件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="3e515-149">Connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and click **Run** to start the trace using the default events.</span></span>  
  
     <span data-ttu-id="3e515-150">您將使用 SQL Server Profiler 監視所發生旳處理事件。</span><span class="sxs-lookup"><span data-stu-id="3e515-150">You will use SQL Server Profiler to monitor the processing events as they occur.</span></span>  
  
2.  <span data-ttu-id="3e515-151">(選擇性) 您可以設定追蹤屬性，將追蹤傳送至檔案或資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="3e515-151">Optionally, you can set trace properties to send the trace to a file or table in a database.</span></span>  
  
#### <a name="run-the-job"></a><span data-ttu-id="3e515-152">執行作業</span><span class="sxs-lookup"><span data-stu-id="3e515-152">Run the job</span></span>  
  
1.  <span data-ttu-id="3e515-153">在執行此作業的電腦上，確認此作業可以執行基本作業。</span><span class="sxs-lookup"><span data-stu-id="3e515-153">On the computer used to run the job, verify that the job can perform the basic operation.</span></span> <span data-ttu-id="3e515-154">在物件總管中的 SQL Server Agent 下，先展開 [作業]\*\*\*\*，再於剛才所建立的作業上按一下滑鼠右鍵，然後按一下 [從下列步驟啟動作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3e515-154">In Object Explorer, under SQL Server Agent, expand **Jobs**, right-click the job you just created, and click **Start Job at Step**.</span></span> <span data-ttu-id="3e515-155">作業會立即啟動。</span><span class="sxs-lookup"><span data-stu-id="3e515-155">The job starts immediately.</span></span> <span data-ttu-id="3e515-156">您可以在 SQL Server Profiler 中監視進度。</span><span class="sxs-lookup"><span data-stu-id="3e515-156">You can monitor progress in SQL Server Profiler.</span></span>  
  
2.  <span data-ttu-id="3e515-157">最後一個步驟是將作業修改成依照您所義的排程執行，並新增管理作業所需的警示或通知。</span><span class="sxs-lookup"><span data-stu-id="3e515-157">As a final step, modify the job to run on a schedule that you define, adding any alerts or notifications necessary to administer the job.</span></span> <span data-ttu-id="3e515-158">您也可能想要精簡處理指令碼，或在作業中建立多個步驟來單獨處理物件。</span><span class="sxs-lookup"><span data-stu-id="3e515-158">You might also want to refine the processing script, or create multiple steps in the job to process objects independently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e515-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e515-159">See Also</span></span>  
 <span data-ttu-id="3e515-160">[SQL Server Agent 元件](../../ssms/agent/sql-server-agent.md#Components) </span><span class="sxs-lookup"><span data-stu-id="3e515-160">[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) </span></span>  
 <span data-ttu-id="3e515-161">[使用 SQL Server Agent 排程 SSAS 管理工作](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="3e515-161">[Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md) </span></span>  
 <span data-ttu-id="3e515-162">[批次處理 &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3e515-162">[Batch Processing &#40;Analysis Services&#41;](batch-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="3e515-163">[多維度模型物件處理](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3e515-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="3e515-164">處理物件 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="3e515-164">Processing Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
