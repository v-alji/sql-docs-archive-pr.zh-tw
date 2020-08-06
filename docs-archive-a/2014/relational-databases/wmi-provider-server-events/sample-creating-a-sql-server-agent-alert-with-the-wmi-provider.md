---
title: 範例：使用伺服器事件的 WMI 提供者來建立 SQL Server Agent 警示 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f23a3a8738435dc6a27a230f4521300a3ee2470f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702514"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a><span data-ttu-id="05837-102">範例：使用伺服器事件的 WMI 提供者建立 SQL Server Agent 警示</span><span class="sxs-lookup"><span data-stu-id="05837-102">Sample: Creating a SQL Server Agent Alert by Using the WMI Provider for Server Events</span></span>
  <span data-ttu-id="05837-103">使用 WMI 事件提供者的常見方式為建立回應特定事件的 SQL Server Agent 警示。</span><span class="sxs-lookup"><span data-stu-id="05837-103">One common way to use the WMI Event Provider is to create SQL Server Agent alerts that respond to specific events.</span></span> <span data-ttu-id="05837-104">下列範例顯示一個簡單的警示，可將 XML 死結圖形事件儲存在資料表中，以便稍後進行分析。</span><span class="sxs-lookup"><span data-stu-id="05837-104">The following sample presents a simple alert that saves XML deadlock graph events in a table for later analysis.</span></span> <span data-ttu-id="05837-105">SQL Server Agent 會提交 WQL 要求、接收 WMI 事件，以及執行工作來回應事件。</span><span class="sxs-lookup"><span data-stu-id="05837-105">SQL Server Agent submits a WQL request, receives WMI events, and runs a job in response to the event.</span></span> <span data-ttu-id="05837-106">請注意，雖然在處理通知訊息時包含數個 Service Broker 物件，但是 WMI 事件提供者會處理建立與管理這些物件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="05837-106">Notice that, although several Service Broker objects are involved in processing the notification message, the WMI Event Provider handles the details of creating and managing these objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05837-107">範例</span><span class="sxs-lookup"><span data-stu-id="05837-107">Example</span></span>  
 <span data-ttu-id="05837-108">首先，在 `AdventureWorks` 資料庫中建立一個資料表來容納死結圖形事件。</span><span class="sxs-lookup"><span data-stu-id="05837-108">First, a table is created in the `AdventureWorks` database to hold the deadlock graph event.</span></span> <span data-ttu-id="05837-109">此資料表包含兩個資料行：`AlertTime` 資料行容納警示執行的時間，而 `DeadlockGraph` 資料行容納其中包含死結圖形的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="05837-109">The table contains two columns: The `AlertTime` column holds the time that the alert runs, and the `DeadlockGraph` column holds the XML document that contains the deadlock graph.</span></span>  
  
 <span data-ttu-id="05837-110">接著，建立警示。</span><span class="sxs-lookup"><span data-stu-id="05837-110">Then, the alert is created.</span></span> <span data-ttu-id="05837-111">指令碼會先建立警示將執行的工作、將作業步驟加入到工作中，然後將工作目標瞄準為目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="05837-111">The script first creates the job that the alert will run, adds a job step to the job, and targets the job to the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="05837-112">然後，指令碼會建立警示。</span><span class="sxs-lookup"><span data-stu-id="05837-112">The script then creates the alert.</span></span>  
  
 <span data-ttu-id="05837-113">作業步驟會抓取 WMI 事件實例的**TextData**屬性，並將該值插入**DeadlockEvents**資料表的**DeadlockGraph**資料行中。</span><span class="sxs-lookup"><span data-stu-id="05837-113">The job step retrieves the **TextData** property of the WMI event instance and inserts that value into the **DeadlockGraph** column of the **DeadlockEvents** table.</span></span> <span data-ttu-id="05837-114">請注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會以隱含的方式，將字串轉換為 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="05837-114">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implicitly converts the string into XML format.</span></span> <span data-ttu-id="05837-115">作業步驟會使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子系統，因此，作業步驟不會指定 Proxy。</span><span class="sxs-lookup"><span data-stu-id="05837-115">Because the job step uses the [!INCLUDE[tsql](../../includes/tsql-md.md)] subsystem, the job step does not specify a proxy.</span></span>  
  
 <span data-ttu-id="05837-116">每當記錄死結圖形追蹤事件時，警示就會執行作業。</span><span class="sxs-lookup"><span data-stu-id="05837-116">The alert runs the job whenever a deadlock graph trace event would be logged.</span></span> <span data-ttu-id="05837-117">對於 WMI 警示，SQL Server Agent 會使用指定的命名空間和 WQL 陳述式來建立通知查詢。</span><span class="sxs-lookup"><span data-stu-id="05837-117">For a WMI alert, SQL Server Agent creates a notification query using the namespace and WQL statement specified.</span></span> <span data-ttu-id="05837-118">SQL Server Agent 會針對此警示監視本機電腦上的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="05837-118">For this alert, SQL Server Agent monitors the default instance on the local computer.</span></span> <span data-ttu-id="05837-119">WQL 陳述式會要求預設執行個體中的任何 `DEADLOCK_GRAPH` 事件。</span><span class="sxs-lookup"><span data-stu-id="05837-119">The WQL statement requests any `DEADLOCK_GRAPH` event in the default instance.</span></span> <span data-ttu-id="05837-120">若要變更警示所監視的執行個體，將警示的執行個體名稱取代為 `MSSQLSERVER` 中的 `@wmi_namespace`。</span><span class="sxs-lookup"><span data-stu-id="05837-120">To change the instance that the alert monitors, substitute the instance name for `MSSQLSERVER` in the `@wmi_namespace` for the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05837-121">如需接收 WMI 事件的 SQL Server Agent， [!INCLUDE[ssSB](../../includes/sssb-md.md)] 必須在**msdb**和中啟用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="05837-121">For SQL Server Agent to receive WMI events, [!INCLUDE[ssSB](../../includes/sssb-md.md)] must be enabled in **msdb** and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a><span data-ttu-id="05837-122">測試範例</span><span class="sxs-lookup"><span data-stu-id="05837-122">Testing the Sample</span></span>  
 <span data-ttu-id="05837-123">若要查看作業執行，請先誘發死結。</span><span class="sxs-lookup"><span data-stu-id="05837-123">To see the job run, provoke a deadlock.</span></span> <span data-ttu-id="05837-124">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，開啟兩個 **[SQL 查詢**] 索引標籤，並將兩個查詢連接到相同的實例。</span><span class="sxs-lookup"><span data-stu-id="05837-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open two **SQL Query** tabs and connect both queries to the same instance.</span></span> <span data-ttu-id="05837-125">在其中一個查詢索引標籤中執行下列指令碼。</span><span class="sxs-lookup"><span data-stu-id="05837-125">Run the following script in one of the query tabs.</span></span> <span data-ttu-id="05837-126">這個指令碼會產生一個結果集並完成。</span><span class="sxs-lookup"><span data-stu-id="05837-126">This script produces one result set and finishes.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="05837-127">在第二個 [查詢] 索引標籤中執行下列腳本。此腳本會產生一個結果集，然後封鎖，等待取得上的鎖定 `Production.Product` 。</span><span class="sxs-lookup"><span data-stu-id="05837-127">Run the following script in the second query tab. This script produces one result set and then blocks, waiting to acquire a lock on `Production.Product`.</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="05837-128">在第一個 [查詢] 索引標籤中執行下列腳本。此腳本會封鎖，等待取得上的鎖定 `Production.Location` 。</span><span class="sxs-lookup"><span data-stu-id="05837-128">Run the following script in the first query tab. This script blocks, waiting to acquire a lock on `Production.Location`.</span></span> <span data-ttu-id="05837-129">短暫的逾時之後，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會選擇此指令碼或範例中的指令碼，做為死結的犧牲者，然後結束交易。</span><span class="sxs-lookup"><span data-stu-id="05837-129">After a short time-out, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will choose either this script or the script in the sample as the deadlock victim and end the transaction.</span></span>  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 <span data-ttu-id="05837-130">誘發死結之後稍等一陣子，讓 SQL Server Agent 啟動警示並執行作業。</span><span class="sxs-lookup"><span data-stu-id="05837-130">After provoking the deadlock, wait several moments for SQL Server Agent to activate the alert and run the job.</span></span> <span data-ttu-id="05837-131">執行下列指令碼來檢查 `DeadlockEvents` 資料表的內容：</span><span class="sxs-lookup"><span data-stu-id="05837-131">Examine the contents of the `DeadlockEvents` table by running the following script:</span></span>  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 <span data-ttu-id="05837-132">`DeadlockGraph` 資料行應該包含顯示死結圖形事件所有屬性的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="05837-132">The `DeadlockGraph` column should contain an XML document that shows all the properties of the deadlock graph event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05837-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05837-133">See Also</span></span>  
 [<span data-ttu-id="05837-134">伺服器事件的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="05837-134">WMI Provider for Server Events Concepts</span></span>](wmi-provider-for-server-events-concepts.md)  
  
  
