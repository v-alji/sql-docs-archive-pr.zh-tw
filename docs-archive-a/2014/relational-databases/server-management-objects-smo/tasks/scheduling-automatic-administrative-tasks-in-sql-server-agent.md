---
title: 在 SQL Server Agent 中排程自動管理工作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- scheduling administrative tasks [SMO]
- SQL Server Agent [SMO]
- automatic administrative SMO tasks
ms.assetid: 900242ad-d6a2-48e9-8a1b-f0eea4413c16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a7620935a257a4200999cce27ba901588839b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599442"
---
# <a name="scheduling-automatic-administrative-tasks-in-sql-server-agent"></a><span data-ttu-id="7f6cb-102">使用 SQL Server Agent 排程自動管理工作</span><span class="sxs-lookup"><span data-stu-id="7f6cb-102">Scheduling Automatic Administrative Tasks in SQL Server Agent</span></span>
  <span data-ttu-id="7f6cb-103">在 SMO 中，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 是由下列物件表示：</span><span class="sxs-lookup"><span data-stu-id="7f6cb-103">In SMO, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is represented by the following objects:</span></span>  
  
-   <span data-ttu-id="7f6cb-104"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> 物件具有三個作業、警示和運算子的集合。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-104">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobServer> object has three collections of jobs, alerts and operators.</span></span>  
  
-   <span data-ttu-id="7f6cb-105"><xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> 物件表示呼叫器、電子郵件地址和網路傳送操作員的清單，在發生事件時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 會自動加以通知。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-105">The <xref:Microsoft.SqlServer.Management.Smo.Agent.OperatorCollection> object represents a list of pager, e-mail addresses and net send operators that can be notified of events automatically by the Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="7f6cb-106"><xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> 物件表示系統事件或效能條件之類情況的清單，這些情況都受到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的監視。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-106">The <xref:Microsoft.SqlServer.Management.Smo.Agent.AlertCollection> object represents a list of circumstances such as system events or performance conditions that are monitored by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7f6cb-107"><xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> 物件就稍微複雜一點，</span><span class="sxs-lookup"><span data-stu-id="7f6cb-107">The <xref:Microsoft.SqlServer.Management.Smo.Agent.JobCollection> object is slightly more complex.</span></span> <span data-ttu-id="7f6cb-108">它表示會在指定排程執行的多重步驟工作的清單。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-108">It represents a list of multi-step tasks that run at specified schedules.</span></span> <span data-ttu-id="7f6cb-109">步驟和排程資訊會儲存在 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> 和 <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> 物件中。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-109">The steps and schedule information are stored in the <xref:Microsoft.SqlServer.Management.Smo.Agent.JobStep> and <xref:Microsoft.SqlServer.Management.Smo.Agent.JobSchedule> objects.</span></span>  
  
 <span data-ttu-id="7f6cb-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 物件位於 <xref:Microsoft.SqlServer.Management.Smo.Agent> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent objects are in the <xref:Microsoft.SqlServer.Management.Smo.Agent> namespace.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7f6cb-111">範例</span><span class="sxs-lookup"><span data-stu-id="7f6cb-111">Examples</span></span>  
 <span data-ttu-id="7f6cb-112">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-112">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="7f6cb-113">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-113">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
1.  <span data-ttu-id="7f6cb-114">如果程式使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent，則您必須包含 `Imports` 陳述式來限定 Agent 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-114">For programs that use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, you must include the `Imports` statement to qualify the Agent namespace.</span></span> <span data-ttu-id="7f6cb-115">將陳述式插入至其他 `Imports` 陳述式之後、在應用程式中的任何宣告之前，例如：</span><span class="sxs-lookup"><span data-stu-id="7f6cb-115">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Agent`  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-basic"></a><span data-ttu-id="7f6cb-116">在 Visual Basic 中建立具有步驟和排程的作業</span><span class="sxs-lookup"><span data-stu-id="7f6cb-116">Creating a Job with Steps and a Schedule in Visual Basic</span></span>  
 <span data-ttu-id="7f6cb-117">此程式碼範例會建立具有步驟和排程的作業，然後通知操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-117">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent1](SMO How to#SMO_VBAgent1)]  -->  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-visual-c"></a><span data-ttu-id="7f6cb-118">在 Visual C# 中建立具有步驟和排程的作業</span><span class="sxs-lookup"><span data-stu-id="7f6cb-118">Creating a Job with Steps and a Schedule in Visual C#</span></span>  
 <span data-ttu-id="7f6cb-119">此程式碼範例會建立具有步驟和排程的作業，然後通知操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-119">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
  
            //Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.   
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
  
            //Set the Net send address.   
            op.NetSendAddress = "Network1_PC";  
  
            //Create the operator on the instance of SQL Server Agent.   
            op.Create();  
  
            //Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
            Job jb = new Job(srv.JobServer, "Test_Job");  
  
            //Specify which operator to inform and the completion action.   
            jb.OperatorToNetSend = "Test_Operator";  
            jb.NetSendLevel = CompletionAction.Always;  
  
            //Create the job on the instance of SQL Server Agent.   
            jb.Create();  
  
            //Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
            JobStep jbstp = new JobStep(jb, "Test_Job_Step");  
            jbstp.Command = "Test_StoredProc";  
            jbstp.OnSuccessAction = StepCompletionAction.QuitWithSuccess;  
            jbstp.OnFailAction = StepCompletionAction.QuitWithFailure;  
  
            //Create the job step on the instance of SQL Agent.   
            jbstp.Create();  
  
            //Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
  
            JobSchedule jbsch = new JobSchedule(jb, "Test_Job_Schedule");  
  
            //Set properties to define the schedule frequency, and duration.   
            jbsch.FrequencyTypes = FrequencyTypes.Daily;  
            jbsch.FrequencySubDayTypes = FrequencySubDayTypes.Minute;  
            jbsch.FrequencySubDayInterval = 30;  
            TimeSpan ts1 = new TimeSpan(9, 0, 0);  
            jbsch.ActiveStartTimeOfDay = ts1;  
  
            TimeSpan ts2 = new TimeSpan(17, 0, 0);  
            jbsch.ActiveEndTimeOfDay = ts2;  
            jbsch.FrequencyInterval = 1;  
  
            System.DateTime d = new System.DateTime(2003, 1, 1);  
            jbsch.ActiveStartDate = d;  
  
            //Create the job schedule on the instance of SQL Agent.   
            jbsch.Create();  
        }  
```  
  
## <a name="creating-a-job-with-steps-and-a-schedule-in-powershell"></a><span data-ttu-id="7f6cb-120">在 PowerShell 中建立具有步驟和排程的作業</span><span class="sxs-lookup"><span data-stu-id="7f6cb-120">Creating a Job with Steps and a Schedule in PowerShell</span></span>  
 <span data-ttu-id="7f6cb-121">此程式碼範例會建立具有步驟和排程的作業，然後通知操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-121">This code example creates a job with steps and a schedule, and then informs an operator.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Define a Job object variable by supplying the Agent and the name arguments in the constructor and setting properties.   
$jb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Job -argumentlist $srv.JobServer, "Test_Job"   
  
#Specify which operator to inform and the completion action.   
$jb.OperatorToNetSend = "Test_Operator";   
$jb.NetSendLevel = [Microsoft.SqlServer.Management.SMO.Agent.CompletionAction]::Always  
  
#Create the job on the instance of SQL Server Agent.   
$jb.Create()  
  
#Define a JobStep object variable by supplying the parent job and name arguments in the constructor.   
$jbstp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobStep -argumentlist $jb, "Test_Job_Step"   
$jbstp.Command = "Test_StoredProc";   
$jbstp.OnSuccessAction = [Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithSuccess;   
$jbstp.OnFailAction =[Microsoft.SqlServer.Management.SMO.Agent.StepCompletionAction]::QuitWithFailure;   
  
#Create the job step on the instance of SQL Agent.   
$jbstp.Create();   
  
#Define a JobSchedule object variable by supplying the parent job and name arguments in the constructor.   
$jbsch = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.JobSchedule -argumentlist $jb, "Test_Job_Schedule"   
  
#Set properties to define the schedule frequency, and duration.   
$jbsch.FrequencyTypes =  [Microsoft.SqlServer.Management.SMO.Agent.FrequencyTypes]::Daily  
  
$jbsch.FrequencySubDayTypes = [Microsoft.SqlServer.Management.SMO.Agent.FrequencySubDayTypes]::Minute  
$jbsch.FrequencySubDayInterval = 30  
$ts1 =  New-Object -TypeName TimeSpan -argumentlist 9, 0, 0  
$jbsch.ActiveStartTimeOfDay = $ts1  
$ts2 = New-Object -TypeName TimeSpan -argumentlist 17, 0, 0  
$jbsch.ActiveEndTimeOfDay = $ts2  
$jbsch.FrequencyInterval = 1  
$jbsch.ActiveStartDate = "01/01/2003"  
  
#Create the job schedule on the instance of SQL Agent.   
$jbsch.Create();  
```  
  
## <a name="creating-an-alert-in-visual-basic"></a><span data-ttu-id="7f6cb-122">在 Visual Basic 中建立警示</span><span class="sxs-lookup"><span data-stu-id="7f6cb-122">Creating an Alert in Visual Basic</span></span>  
 <span data-ttu-id="7f6cb-123">此程式碼範例會建立由效能條件觸發的警示。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-123">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="7f6cb-124">該條件必須以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="7f6cb-124">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="7f6cb-125">**ObjectName |CounterName |實例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="7f6cb-125">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="7f6cb-126">警示通知需要有操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-126">An operator is required for the alert notification.</span></span> <span data-ttu-id="7f6cb-127"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 類型需要使用方括號，因為 `operator` 是 Visual Basic 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-127">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a Visual Basic keyword.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent3](SMO How to#SMO_VBAgent3)]  -->  
  
## <a name="creating-an-alert-in-visual-c"></a><span data-ttu-id="7f6cb-128">在 Visual C# 中建立警示</span><span class="sxs-lookup"><span data-stu-id="7f6cb-128">Creating an Alert in Visual C#</span></span>  
 <span data-ttu-id="7f6cb-129">此程式碼範例會建立由效能條件觸發的警示。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-129">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="7f6cb-130">該條件必須以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="7f6cb-130">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="7f6cb-131">**ObjectName |CounterName |實例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="7f6cb-131">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="7f6cb-132">警示通知需要有操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-132">An operator is required for the alert notification.</span></span> <span data-ttu-id="7f6cb-133"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 類型需要使用方括號，因為 `operator` 是 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-133">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```csharp
{  
             //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Define an Alert object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
            Alert al = new Alert(srv.JobServer, "Test_Alert");  
  
            //Specify the performance condition string to define the alert.   
            al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3";  
  
            //Create the alert on the SQL Agent.   
            al.Create();  
  
            //Define an Operator object variable by supplying the SQL Server Agent and the name arguments in the constructor.   
  
            Operator op = new Operator(srv.JobServer, "Test_Operator");  
            //Set the net send address.   
            op.NetSendAddress = "NetworkPC";  
            //Create the operator on the SQL Agent.   
            op.Create();  
            //Run the AddNotification method to specify the operator is notified when the alert is raised.   
            al.AddNotification("Test_Operator", NotifyMethods.NetSend);  
        }  
```  
  
## <a name="creating-an-alert-in-powershell"></a><span data-ttu-id="7f6cb-134">在 PowerShell 中建立警示</span><span class="sxs-lookup"><span data-stu-id="7f6cb-134">Creating an Alert in PowerShell</span></span>  
 <span data-ttu-id="7f6cb-135">此程式碼範例會建立由效能條件觸發的警示。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-135">This code example creates an alert that is triggered by a performance condition.</span></span> <span data-ttu-id="7f6cb-136">該條件必須以特定格式提供：</span><span class="sxs-lookup"><span data-stu-id="7f6cb-136">The condition must be provided in a specific format:</span></span>  
  
 <span data-ttu-id="7f6cb-137">**ObjectName |CounterName |實例 |ComparisionOp |CompValue**</span><span class="sxs-lookup"><span data-stu-id="7f6cb-137">**ObjectName|CounterName|Instance|ComparisionOp|CompValue**</span></span>  
  
 <span data-ttu-id="7f6cb-138">警示通知需要有操作員。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-138">An operator is required for the alert notification.</span></span> <span data-ttu-id="7f6cb-139"><xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> 類型需要使用方括號，因為 `operator` 是 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-139">The <xref:Microsoft.SqlServer.Management.Smo.Agent.Operator> type requires square parentheses because `operator` is a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] keyword.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define an Alert object variable by supplying the SQL Agent and the name arguments in the constructor.  
$al = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Alert -argumentlist $srv.JobServer, "Test_Alert"  
  
#Specify the performance condition string to define the alert.  
$al.PerformanceCondition = "SQLServer:General Statistics|User Connections||>|3"  
  
#Create the alert on the SQL Agent.  
$al.Create()  
  
#Define an Operator object variable by supplying the Agent (parent JobServer object) and the name in the constructor.  
$op = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Agent.Operator -argumentlist $srv.JobServer, "Test_Operator"  
  
#Set the Net send address.  
$op.NetSendAddress = "Network1_PC"  
  
#Create the operator on the instance of SQL Agent.  
$op.Create()  
  
#Run the AddNotification method to specify the operator is notified when the alert is raised.  
$ns = [Microsoft.SqlServer.Management.SMO.Agent.NotifyMethods]::NetSend  
$al.AddNotification("Test_Operator", $ns)  
  
#Drop the alert and the operator  
$al.Drop()  
$op.Drop()  
```  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-basic"></a><span data-ttu-id="7f6cb-140">在 Visual Basic 中允許使用者使用 Proxy 帳戶存取子系統</span><span class="sxs-lookup"><span data-stu-id="7f6cb-140">Allowing User Access to Subsystem by Using a Proxy Account in Visual Basic</span></span>  
 <span data-ttu-id="7f6cb-141">此程式碼範例示範如何允許使用者利用 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 方法來存取指定的子系統。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-141">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBAgent2](SMO How to#SMO_VBAgent2)]  -->  
  
## <a name="allowing-user-access-to-subsystem-by-using-a-proxy-account-in-visual-c"></a><span data-ttu-id="7f6cb-142">在 Visual C# 中允許使用者使用 Proxy 帳戶存取子系統</span><span class="sxs-lookup"><span data-stu-id="7f6cb-142">Allowing User Access to Subsystem by Using a Proxy Account in Visual C#</span></span>  
 <span data-ttu-id="7f6cb-143">此程式碼範例示範如何允許使用者利用 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> 方法來存取指定的子系統。</span><span class="sxs-lookup"><span data-stu-id="7f6cb-143">This code example shows how to allow a user access to a specified subsystem by using the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount.AddSubSystem%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.Agent.ProxyAccount> object.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Declare a JobServer object variable and reference the SQL Server Agent.   
JobServer js = default(JobServer);   
js = srv.JobServer;   
//Define a Credential object variable by supplying the parent server and name arguments in the constructor.   
Credential c = default(Credential);   
c = new Credential(srv, "Proxy_accnt");   
//Set the identity to a valid login represented by the vIdentity string variable.   
//The sub system will run under this login.   
c.Identity = vIdentity;   
//Create the credential on the instance of SQL Server.   
c.Create();   
//Define a ProxyAccount object variable by supplying the SQL Server Agent, the name, the credential, the description arguments in the constructor.   
ProxyAccount pa = default(ProxyAccount);   
pa = new ProxyAccount(js, "Test_proxy", "Proxy_accnt", true, "Proxy account for users to run job steps in command shell.");   
//Create the proxy account on the SQL Agent.   
pa.Create();   
//Add the login, represented by the vLogin string variable, to the proxy account.   
pa.AddLogin(vLogin);   
//Add the CmdExec subsytem to the proxy account.   
pa.AddSubSystem(AgentSubSystem.CmdExec);   
}   
//Now users logged on as vLogin can run CmdExec job steps with the specified credentials.   
```  
  
## <a name="see-also"></a><span data-ttu-id="7f6cb-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f6cb-144">See Also</span></span>  
 <span data-ttu-id="7f6cb-145">[SQL Server Agent](../../../ssms/agent/sql-server-agent.md) </span><span class="sxs-lookup"><span data-stu-id="7f6cb-145">[SQL Server Agent](../../../ssms/agent/sql-server-agent.md) </span></span>  
 [<span data-ttu-id="7f6cb-146">實作作業</span><span class="sxs-lookup"><span data-stu-id="7f6cb-146">Implement Jobs</span></span>](../../../ssms/agent/implement-jobs.md)  
