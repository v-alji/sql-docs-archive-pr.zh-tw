---
title: 啟動、停止、暫停、繼續、重新開機資料庫引擎、SQL Server Agent 或 SQL Server Browser 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, start and stop services
- stopping SQL Server Agent
- parameters [SQL Server], startup options
- SQL Server, startup options
- Database Engine [SQL Server], starting and stopping services
- pausing SQL Server
- PowerShell [SQL Server], starting and stopping services
- single-user mode [SQL Server], starting in
- SQL Server Management Studio [SQL Server], starting or stopping services
- stopping SQL Server Browser service
- starting SQL Server Agent
- default instances [SQL Server], starting and stopping
- SQL Server Agent, starting and stopping
- command prompt [SQL Server], starting and stopping SQL Server services
- continuing SQL Server
- starting SQL Server Database Engine
- net stop commands [SQL Server]
- command prompt [SQL Server], SQL Browser service
- Configuration Manager, start and stop services
- resuming SQL Server
- startup options [SQL Server]
- named instances [SQL Server], starting and stopping
- net start commands [SQL Server]
- SQL Server, starting and stopping
- stopping SQL Server
- starting SQL Server Browser service
- SQL Server Database Engine setting startup options
- administering SQL Server, starting and stopping services
- Management Studio [SQL Server], starting or stopping services
ms.assetid: 32660a02-e5a1-411a-9e57-7066ca459df6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f4b102c8fd81923d7386c8e556896e715311a07e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706706"
---
# <a name="start-stop-pause-resume-restart-the-database-engine-sql-server-agent-or-sql-server-browser-service"></a><span data-ttu-id="a8ab0-102">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="a8ab0-102">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>
  <span data-ttu-id="a8ab0-103">本主題描述如何 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 從命令提示字元、或 PowerShell 使用 Configuration Manager、、 **net**命令 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，啟動、停止、暫停、繼續或重新開機、代理程式或 Browser 服務。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-103">This topic describes how to start, stop, pause, resume, or restart the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], **net** commands from a command prompt, [!INCLUDE[tsql](../../includes/tsql-md.md)], or PowerShell.</span></span>  
  
-   <span data-ttu-id="a8ab0-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-104">**Before you begin:**</span></span>  
  
    -   [<span data-ttu-id="a8ab0-105">這些是什麼服務？</span><span class="sxs-lookup"><span data-stu-id="a8ab0-105">What are these services?</span></span>](#Services)  
  
    -   [<span data-ttu-id="a8ab0-106">其他資訊</span><span class="sxs-lookup"><span data-stu-id="a8ab0-106">Additional Information</span></span>](#MoreInformation)  
  
    -   [<span data-ttu-id="a8ab0-107">安全性</span><span class="sxs-lookup"><span data-stu-id="a8ab0-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a8ab0-108">**使用指示：**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-108">**Instructions using:**</span></span>  
  
    -   [<span data-ttu-id="a8ab0-109">SQL Server 組態管理員</span><span class="sxs-lookup"><span data-stu-id="a8ab0-109">SQL Server Configuration Manager</span></span>](#SSCMProcedure)  
  
    -   [<span data-ttu-id="a8ab0-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8ab0-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
    -   [<span data-ttu-id="a8ab0-111">命令提示字元視窗中的 net 命令</span><span class="sxs-lookup"><span data-stu-id="a8ab0-111">net Commands from a Command Prompt window</span></span>](#CommandPrompt)  
  
    -   [<span data-ttu-id="a8ab0-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8ab0-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
    -   [<span data-ttu-id="a8ab0-113">PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8ab0-113">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a8ab0-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="a8ab0-114">Before You Begin</span></span>  
  
###  <a name="what-is-the-ssdenoversion-service-the-ssnoversion-agent-service-and-the-ssnoversion-browser-service"></a><a name="Services"></a> <span data-ttu-id="a8ab0-115">什麼是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務？</span><span class="sxs-lookup"><span data-stu-id="a8ab0-115">What is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service?</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8ab0-116">元件是當做 Windows 服務執行的可執行程式。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-116">components are executable programs that run as a Windows service.</span></span> <span data-ttu-id="a8ab0-117">當做 Windows 服務執行的程式可以繼續操作，而不會在電腦螢幕上顯示任何活動。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-117">Programs that run as a Windows service can continue to operate without displaying any activity on the computer screen.</span></span>  
  
 <span data-ttu-id="a8ab0-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)]維護**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-118">**[!INCLUDE[ssDE](../../includes/ssde-md.md)] service**</span></span>  
 <span data-ttu-id="a8ab0-119">當做 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的可執行處理序。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-119">The executable process that is the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="a8ab0-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 可以是預設執行個體 (每部電腦只限一個執行個體)，或者可以是許多具名 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的其中一個。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be the default instance (limit one per computer), or can be one of many named instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="a8ab0-121">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來判斷哪些 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體會安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-121">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to determine which instances of [!INCLUDE[ssDE](../../includes/ssde-md.md)] are installed on the computer.</span></span> <span data-ttu-id="a8ab0-122">預設實例 (如果您安裝它) 會列為\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) \*\*。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-122">The default instance (if you install it) is listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)**.</span></span> <span data-ttu-id="a8ab0-123">如果您安裝 (命名的實例) 會列為\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( # B0 instance_name>) \*\*。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-123">Named instances (if you install them) are listed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (<instance_name>)**.</span></span> <span data-ttu-id="a8ab0-124">根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 會安裝為\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS) \*\*。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-124">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express is installed as **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLEXPRESS)**.</span></span>  
  
 <span data-ttu-id="a8ab0-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代理程式服務**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-125">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service**</span></span>  
 <span data-ttu-id="a8ab0-126">一種 Windows 服務，它會執行排程的管理工作 (稱為作業和警示)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-126">A Windows service that executes scheduled administrative tasks, which are called jobs and alerts.</span></span> <span data-ttu-id="a8ab0-127">如需詳細資訊，請參閱 [SQL Server Agent](../../ssms/agent/sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-127">For more information, see [SQL Server Agent](../../ssms/agent/sql-server-agent.md).</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8ab0-128">版本都可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-128">Agent is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8ab0-129">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-129">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="a8ab0-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Browser 服務**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service**</span></span>  
 <span data-ttu-id="a8ab0-131">一種 Windows 服務，它會接聽 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的內送要求，並為用戶端提供有關電腦上所安裝之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-131">A Windows service that listens for incoming requests for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides clients information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span> <span data-ttu-id="a8ab0-132">單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務執行個體會用於電腦上所安裝的所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-132">A single instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is used for all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installed on the computer.</span></span>  
  
###  <a name="additional-information"></a><a name="MoreInformation"></a><span data-ttu-id="a8ab0-133">其他資訊</span><span class="sxs-lookup"><span data-stu-id="a8ab0-133">Additional Information</span></span>  
  
-   <span data-ttu-id="a8ab0-134">暫停 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務會阻止新的使用者連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，但是已連接的使用者可以繼續工作，直到連接中斷為止。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-134">Pausing the [!INCLUDE[ssDE](../../includes/ssde-md.md)] service prevents new users from connecting to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but users who are already connected can continue to work until their connections are broken.</span></span> <span data-ttu-id="a8ab0-135">當您希望在停止服務之前等待使用者完成工作時，請使用暫停。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-135">Use pause when you want to wait for users to complete work before you stop the service.</span></span> <span data-ttu-id="a8ab0-136">這樣可讓他們完成正在進行的交易。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-136">This enables them to complete transactions that are in progress.</span></span> <span data-ttu-id="a8ab0-137">「繼續」可讓 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 再次接受新的連接。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-137">Resume allows the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to accept new connections again.</span></span> <span data-ttu-id="a8ab0-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務無法暫停或繼續。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service cannot be paused or resumed.</span></span>  
  
-   <span data-ttu-id="a8ab0-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會使用以下圖示來顯示目前的服務狀態。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] display the current status of services by using the following icons.</span></span>  
  
     <span data-ttu-id="a8ab0-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-140">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager**</span></span>  
  
    -   <span data-ttu-id="a8ab0-141">服務名稱旁圖示上的綠色箭頭，表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-141">A green arrow on the icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="a8ab0-142">服務名稱旁圖示上的紅色方塊，表示服務已停止。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-142">A red square on the icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="a8ab0-143">服務名稱旁圖示上的兩條垂直藍線，表示服務已暫停。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-143">Two vertical blue lines on the icon next to the service name indicates that the service is paused.</span></span>  
  
    -   <span data-ttu-id="a8ab0-144">重新啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]時，紅色方塊表示服務已停止，綠色箭頭則表示服務已順利啟動。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-144">When restarting the [!INCLUDE[ssDE](../../includes/ssde-md.md)], a red square will indicate that the service stopped, and then a green arrow will indicate that he service started successfully.</span></span>  
  
     **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
    -   <span data-ttu-id="a8ab0-145">服務名稱旁綠色圓形圖示上的白色箭頭，表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-145">A white arrow on a green circle icon next to the service name indicates that the service is started.</span></span>  
  
    -   <span data-ttu-id="a8ab0-146">服務名稱旁紅色圓形圖示上的白色方塊，表示服務已停止。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-146">A white square on a red circle icon next to the service name indicates that the service is stopped.</span></span>  
  
    -   <span data-ttu-id="a8ab0-147">服務名稱旁藍色圓形圖示上的兩條垂直白線，表示服務已暫停。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-147">Two vertical white lines on a blue circle icon next to the service name indicates that the service is paused.</span></span>  
  
-   <span data-ttu-id="a8ab0-148">當使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]時，只能使用可能的選項。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-148">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], only options that are possible will be available.</span></span> <span data-ttu-id="a8ab0-149">例如，如果此服務已啟動，則無法使用 **[啟動]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-149">For example, if the service is already started, **Start** will be unavailable.</span></span>  
  
-   <span data-ttu-id="a8ab0-150">在叢集上執行時，使用叢集管理員來管理 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-150">When running on a cluster, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service is best managed by using Cluster Administrator.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a8ab0-151">Security</span><span class="sxs-lookup"><span data-stu-id="a8ab0-151">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a8ab0-152">權限</span><span class="sxs-lookup"><span data-stu-id="a8ab0-152">Permissions</span></span>  
 <span data-ttu-id="a8ab0-153">根據預設，只有本機 Administrators 群組的成員能夠啟動、停止、暫停、繼續或重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-153">By default, only members of the local administrators group can start, stop, pause, resume or restart a service.</span></span> <span data-ttu-id="a8ab0-154">若要將管理服務的能力授與非系統管理員，請參閱 [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349)(如何在 Windows Server 2003 中，將管理服務的權限授與使用者)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-154">To grant non-administrators the ability to manage services, see [How to grant users rights to manage services in Windows Server 2003](https://support.microsoft.com/kb/325349).</span></span> <span data-ttu-id="a8ab0-155">(其他 Windows 版本的程序都很相似)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-155">(The process is similar on other versions of Windows.)</span></span>  
  
 <span data-ttu-id="a8ab0-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)]使用命令停止， [!INCLUDE[tsql](../../includes/tsql-md.md)] `SHUTDOWN` 需要**sysadmin**或**serveradmin**固定伺服器角色中的成員資格，而且無法轉移。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-156">Stopping the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[tsql](../../includes/tsql-md.md)]`SHUTDOWN` command requires membership in the **sysadmin** or **serveradmin** fixed server roles, and is not transferable.</span></span>  
  
##  <a name="using-ssnoversion-configuration-manager"></a><a name="SSCMProcedure"></a> <span data-ttu-id="a8ab0-157">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員</span><span class="sxs-lookup"><span data-stu-id="a8ab0-157">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="a8ab0-158">若要啟動、停止、暫停、繼續或重新啟動 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-158">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="a8ab0-159">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-159">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="a8ab0-160">如果出現 **[使用者帳戶控制]** 對話方塊，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-160">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a8ab0-161">在 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員] 中，按一下左窗格中的 **[SQL Server 服務]**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-161">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="a8ab0-162">在結果窗格中，以滑鼠右鍵按一下 [SQL Server (MSSQLServer)] 或具名執行個體，然後按一下 [啟動]、[停止]、[暫停]、[繼續] 或 [重新啟動]。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-162">In the results pane, right-click **SQL Server (MSSQLServer)** or a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="a8ab0-163">按一下 **[確定]** ，即可關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-163">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8ab0-164">若要使用啟動選項啟動 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，請參閱[設定伺服器啟動選項 &#40;SQL Server 組態管理員&#41;](scm-services-configure-server-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-164">To start an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with startup options, see [Configure Server Startup Options &#40;SQL Server Configuration Manager&#41;](scm-services-configure-server-startup-options.md).</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-ssnoversion-browser-or-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="a8ab0-165">若要啟動、停止、暫停、繼續或重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 或是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的執行個體</span><span class="sxs-lookup"><span data-stu-id="a8ab0-165">To start, stop, pause, resume, or restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser or an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="a8ab0-166">指向 **[開始]** 功能表上的 **[所有程式]** ，然後依序指向 [ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[組態工具]** ，再按一下 **[SQL Server 組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-166">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="a8ab0-167">如果出現 **[使用者帳戶控制]** 對話方塊，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-167">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a8ab0-168">在 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員] 中，按一下左窗格中的 **[SQL Server 服務]**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-168">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the left pane, click **SQL Server Services**.</span></span>  
  
4.  <span data-ttu-id="a8ab0-169">在 [結果] 窗格中，以滑鼠右鍵按一下 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 瀏覽器**] 或 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式 (MSSQLServer) **或** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent ( # B0 instance_name>) **用於已命名的實例，然後按一下 [**啟動**]、[**停止**]、[**暫停**]、[**繼續**] 或 [**重新**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-169">In the results pane, right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser**, or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (MSSQLServer)** or **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent (<instance_name>)** for a named instance, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
5.  <span data-ttu-id="a8ab0-170">按一下 **[確定]** ，即可關閉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-170">Click **OK** to close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8ab0-171">Agent 無法暫停。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-171">Agent cannot be paused.</span></span>  
  
##  <a name="using-ssnoversion-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a8ab0-172">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8ab0-172">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio</span></span>  
  
#### <a name="to-start-stop-pause-resume-or-restart-the-an-instance-of-the-ssdenoversion"></a><span data-ttu-id="a8ab0-173">若要啟動、停止、暫停、繼續或重新啟動 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-173">To start, stop, pause, resume, or restart the an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="a8ab0-174">在物件總管中，連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，並以滑鼠右鍵按一下您要啟動的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體，然後按一下 [啟動]\*\*\*\*、[停止]\*\*\*\*、[暫停]\*\*\*\*、[繼續]\*\*\*\* 或 [重新啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-174">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
     <span data-ttu-id="a8ab0-175">或者在 [已註冊的伺服器] 中，以滑鼠右鍵按一下您要啟動的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體、並指向 [服務控制]\*\*\*\*，然後按一下 [啟動]\*\*\*\*、[停止]\*\*\*\*、[暫停]\*\*\*\*、[繼續]\*\*\*\* 或 [重新啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-175">Or, in Registered Servers, right-click the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] you want to start, point to **Service Control**, and then click **Start**, **Stop**, **Pause**, **Resume**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="a8ab0-176">如果出現 **[使用者帳戶控制]** 對話方塊，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-176">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a8ab0-177">當系統提示您是否要執行動作時，請按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-177">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
#### <a name="to-start-stop-or-restart-the-an-instance-of-the-ssnoversion-agent"></a><span data-ttu-id="a8ab0-178">若要啟動、停止或重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的執行個體</span><span class="sxs-lookup"><span data-stu-id="a8ab0-178">To start, stop, or restart the an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent</span></span>  
  
1.  <span data-ttu-id="a8ab0-179">在物件總管中，連接到的實例 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，以滑鼠右鍵按一下 [ \*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式**]，然後按一下 [**啟動**]、[**停止**] 或 [**重新開機\*\*]。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-179">In Object Explorer, connect to the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], right-click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent**, and then click **Start**, **Stop**, or **Restart**.</span></span>  
  
2.  <span data-ttu-id="a8ab0-180">如果出現 **[使用者帳戶控制]** 對話方塊，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-180">If the **User Account Control** dialog box appears, click **Yes**.</span></span>  
  
3.  <span data-ttu-id="a8ab0-181">當系統提示您是否要執行動作時，請按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-181">When prompted if you want to perform the action, click **Yes**.</span></span>  
  
##  <a name="from-the-command-prompt-window-using-net-commands"></a><a name="CommandPrompt"></a> <span data-ttu-id="a8ab0-182">從命令提示字元視窗使用 net 命令</span><span class="sxs-lookup"><span data-stu-id="a8ab0-182">From the Command Prompt Window using net Commands</span></span>  
 <span data-ttu-id="a8ab0-183">可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** 命令來啟動、停止或暫停 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-183">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services can be started, stopped, or paused by using [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows **net** commands.</span></span>  
  
###  <a name="to-start-the-default-instance-of-the-ssde"></a><a name="dbDefault"></a> <span data-ttu-id="a8ab0-184">若要啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-184">To start the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="a8ab0-185">從命令提示字元，輸入下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="a8ab0-185">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a8ab0-186">**net start "SQL Server (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-186">**net start "SQL Server (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="a8ab0-187">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-187">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-188">**net start MSSQLSERVER**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-188">**net start MSSQLSERVER**</span></span>  
  
###  <a name="to-start-a-named-instance-of-the-ssde"></a><a name="dbNamed"></a> <span data-ttu-id="a8ab0-189">若要啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-189">To start a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span></span>  
  
-   <span data-ttu-id="a8ab0-190">從命令提示字元，輸入下列其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-190">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="a8ab0-191">以想要管理執行個體的名稱來取代 *\<instancename>* 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-191">Replace *\<instancename>* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="a8ab0-192">**net start "SQL Server (** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-192">**net start "SQL Server (** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="a8ab0-193">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-193">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-194">**net start MSSQL$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="a8ab0-194">**net start MSSQL$** *instancename*</span></span>  
  
###  <a name="to-start-the-ssde-with-startup-options"></a><a name="dbStartup"></a> <span data-ttu-id="a8ab0-195">若要使用啟動選項來啟動 [!INCLUDE[ssDE](../../includes/ssde-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-195">To start the [!INCLUDE[ssDE](../../includes/ssde-md.md)] with startup options</span></span>  
  
-   <span data-ttu-id="a8ab0-196">將啟動選項加入 **net start "SQL Server (MSSQLSERVER)"** 陳述式結尾，並間隔一個空格。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-196">Add startup options to the end of the **net start "SQL Server (MSSQLSERVER)"** statement, separated by a space.</span></span> <span data-ttu-id="a8ab0-197">使用 **net start**啟動時，啟動選項會使用斜線 (/)，而非連字號 (-)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-197">When started using **net start**, startup options use a slash (/) instead of a hyphen (-).</span></span>  
  
     <span data-ttu-id="a8ab0-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-198">**net start "SQL Server (MSSQLSERVER)" /f /m**</span></span>  
  
     <span data-ttu-id="a8ab0-199">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-199">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-200">**net start MSSQLSERVER /f /m**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-200">**net start MSSQLSERVER /f /m**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a8ab0-201">如需啟動選項的詳細資訊，請參閱 [Database Engine 服務啟動選項](database-engine-service-startup-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-201">For more information about startup options, see [Database Engine Service Startup Options](database-engine-service-startup-options.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-the-default-instance-of-ssnoversion"></a><a name="agDefault"></a> <span data-ttu-id="a8ab0-202">若要使用啟動選項來啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的預設執行個體上啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-202">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="a8ab0-203">從命令提示字元，輸入下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="a8ab0-203">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a8ab0-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-204">**net start "SQL Server Agent (MSSQLSERVER)"**</span></span>  
  
     <span data-ttu-id="a8ab0-205">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-205">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-206">**net start SQLSERVERAGENT**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-206">**net start SQLSERVERAGENT**</span></span>  
  
###  <a name="to-start-the-ssnoversion-agent-on-a-named-instance-of-ssnoversion"></a><a name="agNamed"></a> <span data-ttu-id="a8ab0-207">若要使用啟動選項來啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的具名執行個體上啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-207">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent on a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="a8ab0-208">從命令提示字元，輸入下列其中一個命令。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-208">From a command prompt, enter one of the following commands.</span></span> <span data-ttu-id="a8ab0-209">以您要管理之執行個體的名稱取代 *執行個體名稱* 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-209">Replace *instancename* with the name of the instance you want to manage.</span></span>  
  
     <span data-ttu-id="a8ab0-210">**net start "SQL Server Agent(** *instancename* **)"**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-210">**net start "SQL Server Agent(** *instancename* **)"**</span></span>  
  
     <span data-ttu-id="a8ab0-211">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-211">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-212">**net start SQLAgent$** *instancename*</span><span class="sxs-lookup"><span data-stu-id="a8ab0-212">**net start SQLAgent$** *instancename*</span></span>  
  
 <span data-ttu-id="a8ab0-213">如需如何以詳細資訊模式執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來進行疑難排解的相關資訊，請參閱 [sqlagent90 應用程式](../../tools/sqlagent90-application.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-213">For information about how to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in verbose mode for troubleshooting, see [sqlagent90 Application](../../tools/sqlagent90-application.md).</span></span>  
  
###  <a name="to-start-the-ssnoversion-browser"></a><a name="Browser"></a> <span data-ttu-id="a8ab0-214">若要啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser</span><span class="sxs-lookup"><span data-stu-id="a8ab0-214">To start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser</span></span>  
  
-   <span data-ttu-id="a8ab0-215">從命令提示字元，輸入下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="a8ab0-215">From a command prompt, enter one of the following commands:</span></span>  
  
     <span data-ttu-id="a8ab0-216">**net start "SQL Server Browser"**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-216">**net start "SQL Server Browser"**</span></span>  
  
     <span data-ttu-id="a8ab0-217">-或-</span><span class="sxs-lookup"><span data-stu-id="a8ab0-217">-or-</span></span>  
  
     <span data-ttu-id="a8ab0-218">**net start SQLBrowser**</span><span class="sxs-lookup"><span data-stu-id="a8ab0-218">**net start SQLBrowser**</span></span>  
  
###  <a name="to-pause-or-stop-services-from-the-command-prompt-window"></a><a name="pauseStop"></a> <span data-ttu-id="a8ab0-219">若要從命令提示字元視窗暫停或停止服務</span><span class="sxs-lookup"><span data-stu-id="a8ab0-219">To pause or stop services from the Command Prompt window</span></span>  
  
-   <span data-ttu-id="a8ab0-220">若要暫停或停止服務，請使用以下方式來修改命令。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-220">To pause or stop services modify the commands in the following ways.</span></span>  
  
    -   <span data-ttu-id="a8ab0-221">若要暫停服務，請以 **net pause** 取代 **net start**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-221">To pause a service, replace **net start** with **net pause**.</span></span>  
  
    -   <span data-ttu-id="a8ab0-222">若要停止服務，請以 **net stop** 取代 **net start**。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-222">To stop a service, replace **net start** with use **net stop**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a8ab0-223">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8ab0-223">Using Transact-SQL</span></span>  
 <span data-ttu-id="a8ab0-224">可以使用 `SHUTDOWN` 陳述式來停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-224">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] can be stopped by using the `SHUTDOWN` statement.</span></span>  
  
#### <a name="to-stop-the-ssde-using-tsql"></a><span data-ttu-id="a8ab0-225">若要使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 停止 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ab0-225">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
-   <span data-ttu-id="a8ab0-226">若要等待目前執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和預存程序完成，然後停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，請執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-226">To wait for currently running [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and stored procedures to finish, and then stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)], execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN;   
    ```  
  
-   <span data-ttu-id="a8ab0-227">若要立即停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)]，請執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-227">To stop the [!INCLUDE[ssDE](../../includes/ssde-md.md)] immediately, execute the following statement.</span></span>  
  
    ```sql  
    SHUTDOWN WITH NOWAIT;   
    ```  
  
 <span data-ttu-id="a8ab0-228">如需語句的詳細資訊 `SHUTDOWN` ，請參閱[SHUTDOWN &#40;transact-sql&#41;](/sql/t-sql/language-elements/shutdown-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-228">For more information about the `SHUTDOWN` statement, see [SHUTDOWN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/shutdown-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="a8ab0-229">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8ab0-229">Using PowerShell</span></span>  
  
#### <a name="to-start-and-stop-ssde-services"></a><span data-ttu-id="a8ab0-230">若要啟動及停止 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 服務</span><span class="sxs-lookup"><span data-stu-id="a8ab0-230">To start and stop [!INCLUDE[ssDE](../../includes/ssde-md.md)] services</span></span>  
  
1.  <span data-ttu-id="a8ab0-231">在 [命令提示字元] 視窗中，執行下列命令來啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-231">In a Command Prompt window, start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell by executing the following command.</span></span>  
  
    ```ms-dos  
    sqlps  
    ```  
  
2.  <span data-ttu-id="a8ab0-232">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 命令提示字元中，執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-232">At a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell command prompt, by executing the following command.</span></span> <span data-ttu-id="a8ab0-233">以電腦的名稱取代 `computername` 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-233">Replace `computername` with the name of your computer.</span></span>  
  
    ```powershell  
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\computername  
    $Wmi = (Get-Item .).ManagedComputer
    ```  
  
3.  <span data-ttu-id="a8ab0-234">識別您想要停止或啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-234">Identify the service that you want to stop or start.</span></span> <span data-ttu-id="a8ab0-235">挑選下列其中一行。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-235">Pick one of the following lines.</span></span> <span data-ttu-id="a8ab0-236">使用具名執行個體的名稱取代 `instancename` 。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-236">Replace `instancename` with the name of the named instance.</span></span>  
  
    -   <span data-ttu-id="a8ab0-237">取得 [!INCLUDE[ssDE](../../includes/ssde-md.md)]預設執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-237">To get a reference to the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQLSERVER']  
        ```  
  
    -   <span data-ttu-id="a8ab0-238">取得 [!INCLUDE[ssDE](../../includes/ssde-md.md)]具名執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-238">To get a reference to a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['MSSQL$instancename']  
        ```  
  
    -   <span data-ttu-id="a8ab0-239">取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體上 [!INCLUDE[ssDE](../../includes/ssde-md.md)]Agent 服務的參考。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-239">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on the default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLSERVERAGENT']  
        ```  
  
    -   <span data-ttu-id="a8ab0-240">取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 具名執行個體上 [!INCLUDE[ssDE](../../includes/ssde-md.md)]Agent 服務的參考。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-240">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service on a named instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLAGENT$instancename']  
        ```  
  
    -   <span data-ttu-id="a8ab0-241">取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務的參考。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-241">To get a reference to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
        ```powershell  
        $DfltInstance = $Wmi.Services['SQLBROWSER']  
        ```  
  
4.  <span data-ttu-id="a8ab0-242">完成範例，以啟動然後停止選取的服務。</span><span class="sxs-lookup"><span data-stu-id="a8ab0-242">Complete the example to start and then stop the selected service.</span></span>  
  
    ```powershell  
    # Display the state of the service.  
    $DfltInstance  
    # Start the service.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a8ab0-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ab0-243">See Also</span></span>  
 <span data-ttu-id="a8ab0-244">[以最基本的設定啟動 SQL Server](start-sql-server-with-minimal-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a8ab0-244">[Start SQL Server with Minimal Configuration](start-sql-server-with-minimal-configuration.md) </span></span>  
 [<span data-ttu-id="a8ab0-245">SQL Server 2014 各版本所支援的功能</span><span class="sxs-lookup"><span data-stu-id="a8ab0-245">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
