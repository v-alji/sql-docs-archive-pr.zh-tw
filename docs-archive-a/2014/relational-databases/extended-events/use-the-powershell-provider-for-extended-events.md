---
title: 針對擴充事件使用 PowerShell 提供者 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], xevent
- extended events [SQL Server], PowerShell
- PowerShell [SQL Server], extended events
ms.assetid: 0b10016f-a479-4444-a484-46cb4677cf64
author: rothja
ms.author: jroth
ms.openlocfilehash: a9efbd389545dcde8285a38b06f41580fb65de6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597122"
---
# <a name="use-the-powershell-provider-for-extended-events"></a><span data-ttu-id="711ec-102">針對擴充事件使用 PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="711ec-102">Use the PowerShell Provider for Extended Events</span></span>
  <span data-ttu-id="711ec-103">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供者來管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充事件。</span><span class="sxs-lookup"><span data-stu-id="711ec-103">You can manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider.</span></span> <span data-ttu-id="711ec-104">XEvent 子資料夾位於 SQLSERVER 磁碟機底下。</span><span class="sxs-lookup"><span data-stu-id="711ec-104">The XEvent subfolder is available under the SQLSERVER drive.</span></span> <span data-ttu-id="711ec-105">您可以使用下列其中一種方法來存取這個資料夾：</span><span class="sxs-lookup"><span data-stu-id="711ec-105">You can access the folder by using either of the following methods:</span></span>  
  
-   <span data-ttu-id="711ec-106">在命令提示字元中輸入 `sqlps`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="711ec-106">At a command prompt, type `sqlps`, and then press ENTER.</span></span> <span data-ttu-id="711ec-107">輸入 `cd xevent`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="711ec-107">Type `cd xevent`, and then press ENTER.</span></span> <span data-ttu-id="711ec-108">從該處，您可以使用**cd**和 `dir` 命令 (或**設定位置**和**get-childitem** Cmdlet，) 流覽至伺服器名稱和實例名稱。</span><span class="sxs-lookup"><span data-stu-id="711ec-108">From there, you can use the **cd** and `dir` commands (or **Set-Location** and **Get-Childitem** cmdlets) to navigate to the server name and instance name.</span></span>  
  
-   <span data-ttu-id="711ec-109">在物件總管中，展開執行個體名稱、展開 [管理]\*\*\*\*、以滑鼠右鍵按一下 [擴充事件]\*\*\*\*，然後按一下 [啟動 PowerShell]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="711ec-109">In Object Explorer, expand the instance name, expand **Management**, right-click **Extended Events**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="711ec-110">這樣就會在下列路徑中啟動 PowerShell：</span><span class="sxs-lookup"><span data-stu-id="711ec-110">This starts PowerShell in the following path:</span></span>  
  
     <span data-ttu-id="711ec-111">PS SQLSERVER： \ XEvent \\ *ServerName* \\ *實例*名稱></span><span class="sxs-lookup"><span data-stu-id="711ec-111">PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*></span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="711ec-112">您可以從 [擴充事件]\*\*\*\* 底下的任何節點啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="711ec-112">You can start PowerShell from any node under **Extended Events**.</span></span> <span data-ttu-id="711ec-113">例如，您可以用滑鼠右鍵按一下 [工作階段]\*\*\*\*，然後按一下 [啟動 PowerShell]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="711ec-113">For example, you can right-click **Sessions**, and then click **Start PowerShell**.</span></span> <span data-ttu-id="711ec-114">這樣就會在下一個層級 (Sessions 資料夾) 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="711ec-114">This starts PowerShell one level deeper, at the Sessions folder.</span></span>  
  
 <span data-ttu-id="711ec-115">您可以瀏覽 XEvent 資料夾樹狀目錄來檢視現有的擴充事件工作階段及其相關聯的事件、目標和述詞。</span><span class="sxs-lookup"><span data-stu-id="711ec-115">You can browse the XEvent folder tree to view existing Extended Events sessions and their associated events, targets and predicates.</span></span> <span data-ttu-id="711ec-116">例如，從 PS SQLSERVER： \ XEvent \\ *ServerName* \\ *InstanceName*> 路徑，如果您輸入，請 `cd sessions` 按 enter，輸入 `dir` ，然後按 enter 鍵，即可看到儲存在該實例上的會話清單。</span><span class="sxs-lookup"><span data-stu-id="711ec-116">For example, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*> path, if you type `cd sessions`, press ENTER, type `dir`, and then press ENTER, you can see the list of sessions that are stored on that instance.</span></span> <span data-ttu-id="711ec-117">您也可以檢視工作階段是否正在執行 (如果有，執行的時間長度)，以及工作階段是否設定為在執行個體啟動時啟動。</span><span class="sxs-lookup"><span data-stu-id="711ec-117">You can also view whether the session is running (and if this is the case, for how long), and whether the session is configured to start when the instance starts.</span></span>  
  
 <span data-ttu-id="711ec-118">若要檢視與工作階段相關聯的事件、其述詞和目標，您可以將目錄變更為工作階段名稱，然後檢視 events 或 targets 資料夾。</span><span class="sxs-lookup"><span data-stu-id="711ec-118">To view the events, their predictates, and the targets that are associated with a session, you can change directories to the session name, and then view either the events or targets folder.</span></span> <span data-ttu-id="711ec-119">例如，若要查看與預設系統健全狀況會話相關聯的事件及其述詞，請從 PS SQLSERVER： \ XEvent \\ *ServerName* \\ *InstanceName*\Sessions> 路徑，輸入 `cd system_health\events,` 按 enter 鍵，輸入 `dir` ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="711ec-119">For example, to view the events and their predicates that are associated with the default system health session, from the PS SQLSERVER:\XEvent\\*ServerName*\\*InstanceName*\Sessions> path, type `cd system_health\events,` press ENTER, type `dir`, and then press ENTER.</span></span>  
  
 <span data-ttu-id="711ec-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供者是一項功能強大的工具，可讓您用來建立、改變和管理擴充事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="711ec-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider is a powerful tool that you can use to create, alter, and manage Extended Events sessions.</span></span> <span data-ttu-id="711ec-121">下列章節將提供使用 PowerShell 指令碼搭配擴充事件的一些基本範例。</span><span class="sxs-lookup"><span data-stu-id="711ec-121">The following section provides some basic examples of using PowerShell scripts with Extended Events.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="711ec-122">範例</span><span class="sxs-lookup"><span data-stu-id="711ec-122">Examples</span></span>  
 <span data-ttu-id="711ec-123">在下列範例中，請注意：</span><span class="sxs-lookup"><span data-stu-id="711ec-123">In the following examples, note the following:</span></span>  
  
-   <span data-ttu-id="711ec-124">腳本必須從 PS SQLSERVER： \\> 提示字元中執行， (可以 `sqlps` 在命令提示字元中輸入) 。</span><span class="sxs-lookup"><span data-stu-id="711ec-124">The scripts must be run from the PS SQLSERVER:\\> prompt (available by typing `sqlps` at a command prompt).</span></span>  
  
-   <span data-ttu-id="711ec-125">這些指令碼會使用預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="711ec-125">The scripts use the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="711ec-126">您必須使用 .ps1 副檔名來儲存這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="711ec-126">The scripts must be saved with a .ps1 extension.</span></span>  
  
-   <span data-ttu-id="711ec-127">PowerShell 執行原則必須允許指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="711ec-127">The PowerShell execution policy must allow the script to run.</span></span> <span data-ttu-id="711ec-128">若要設定執行原則，請使用 **Set-Executionpolicy** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="711ec-128">To set the execution policy, use the **Set-Executionpolicy** cmdlet.</span></span> <span data-ttu-id="711ec-129">(如需詳細資訊，請輸入 `get-help set-executionpolicy -detailed`，然後按 ENTER 鍵。)</span><span class="sxs-lookup"><span data-stu-id="711ec-129">(For more information, type `get-help set-executionpolicy -detailed`, and then press ENTER.)</span></span>  
  
 <span data-ttu-id="711ec-130">下列指令碼會建立名為 'TestSession' 的新工作階段。</span><span class="sxs-lookup"><span data-stu-id="711ec-130">The following script creates a new session that is named 'TestSession'.</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 <span data-ttu-id="711ec-131">下列指令碼會將信號緩衝區目標加入至您在上一則範例中建立的工作階段</span><span class="sxs-lookup"><span data-stu-id="711ec-131">The following script adds the ring buffer target to the session that was created in the previous example.</span></span> <span data-ttu-id="711ec-132">(此範例會示範如何使用 `Alter` 方法。</span><span class="sxs-lookup"><span data-stu-id="711ec-132">(This example shows the use of the `Alter` method.</span></span> <span data-ttu-id="711ec-133">請注意，當您第一次建立工作階段時，可以加入目標)。</span><span class="sxs-lookup"><span data-stu-id="711ec-133">Be aware that you can add the target when you first create the session.)</span></span>  
  
```powershell
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir | where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 <span data-ttu-id="711ec-134">下列指令碼會建立使用述詞運算式的新工作階段。</span><span class="sxs-lookup"><span data-stu-id="711ec-134">The following script creates a new session that uses a predicate expression.</span></span> <span data-ttu-id="711ec-135">在此情況下，工作階段會收集何時寫入 c:\temp.log 檔案 (透過 sqlserver.file_written 事件) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="711ec-135">In this case, the session collects information for when the c:\temp.log file is written to (through the sqlserver.file_written event).</span></span>  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -ArgumentList $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a><span data-ttu-id="711ec-136">安全性</span><span class="sxs-lookup"><span data-stu-id="711ec-136">Security</span></span>  
 <span data-ttu-id="711ec-137">若要建立、更改或卸除擴充事件工作階段，您必須擁有 ALTER ANY EVENT SESSION 權限。</span><span class="sxs-lookup"><span data-stu-id="711ec-137">To create, alter, or drop an Extended Events session, you must have the ALTER ANY EVENT SESSION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711ec-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="711ec-138">See Also</span></span>  
 <span data-ttu-id="711ec-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="711ec-139">[SQL Server PowerShell](../../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="711ec-140">[使用 system_health 會話](use-the-ssms-xe-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="711ec-140">[Use the system_health Session](use-the-ssms-xe-profiler.md) </span></span>  
 [<span data-ttu-id="711ec-141">擴充事件工具</span><span class="sxs-lookup"><span data-stu-id="711ec-141">Extended Events Tools</span></span>](extended-events-tools.md)  
