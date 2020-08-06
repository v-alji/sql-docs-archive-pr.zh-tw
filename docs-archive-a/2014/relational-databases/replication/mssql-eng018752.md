---
title: MSSQL_ENG018752 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018752 error
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fe62d540ea8e988cd4249112f196f75493a8f623
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708186"
---
# <a name="mssql_eng018752"></a><span data-ttu-id="b438a-102">MSSQL_ENG018752</span><span class="sxs-lookup"><span data-stu-id="b438a-102">MSSQL_ENG018752</span></span>
    
## <a name="message-details"></a><span data-ttu-id="b438a-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="b438a-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b438a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b438a-104">Product Name</span></span>|<span data-ttu-id="b438a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b438a-105">SQL Server</span></span>|  
|<span data-ttu-id="b438a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b438a-106">Event ID</span></span>|<span data-ttu-id="b438a-107">18752</span><span class="sxs-lookup"><span data-stu-id="b438a-107">18752</span></span>|  
|<span data-ttu-id="b438a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b438a-108">Event Source</span></span>|<span data-ttu-id="b438a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b438a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b438a-110">元件</span><span class="sxs-lookup"><span data-stu-id="b438a-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="b438a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b438a-111">Symbolic Name</span></span>||  
|<span data-ttu-id="b438a-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b438a-112">Message Text</span></span>|<span data-ttu-id="b438a-113">一次只有一個記錄讀取器代理程式或記錄檔相關程序 (sp_repldone, sp_replcmds, and sp_replshowcmds) 可連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="b438a-113">Only one Log Reader Agent or log-related procedure (sp_repldone, sp_replcmds, and sp_replshowcmds) can connect to a database at a time.</span></span> <span data-ttu-id="b438a-114">若您已執行記錄檔相關程序，請卸除執行程序的連接，或者利用該連接執行 sp_replflush 之後，再啟動記錄讀取器代理程式或執行其他記錄檔相關程序。</span><span class="sxs-lookup"><span data-stu-id="b438a-114">If you executed a log-related procedure, drop the connection over which the procedure was executed or execute sp_replflush over that connection before starting the Log Reader Agent or executing another log-related procedure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b438a-115">說明</span><span class="sxs-lookup"><span data-stu-id="b438a-115">Explanation</span></span>  
 <span data-ttu-id="b438a-116">目前有多個連接嘗試執行下列任一項目： **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds**。</span><span class="sxs-lookup"><span data-stu-id="b438a-116">More than one current connection is trying to execute any of the following: **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span> <span data-ttu-id="b438a-117">[sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) 和 [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) 是一種預存程序，可供記錄讀取器代理程式在已發行資料庫中尋找及更新已複寫異動的資訊。</span><span class="sxs-lookup"><span data-stu-id="b438a-117">The stored procedures [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql) and [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) are stored procedures used by the Log Reader Agent to locate and update information about replicated transactions in a published database.</span></span> <span data-ttu-id="b438a-118">[sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) 預存程序是用來對特定類型的異動複寫問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="b438a-118">The stored procedure [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql) is used to troubleshoot certain types of issues with transactional replication.</span></span>  
  
 <span data-ttu-id="b438a-119">此錯誤在下列情況下產生：</span><span class="sxs-lookup"><span data-stu-id="b438a-119">This error is raised in the following circumstances:</span></span>  
  
-   <span data-ttu-id="b438a-120">如果已發行資料庫的「記錄讀取器代理程式」正在執行，而第二個「記錄讀取器代理程式」嘗試針對相同的資料庫執行，則錯誤就會在第二個代理程式中產生，並且出現在代理程式記錄中。</span><span class="sxs-lookup"><span data-stu-id="b438a-120">If the Log Reader Agent for a published database is running and a second Log Reader Agent attempts to run against the same database, the error is raised for the second agent and appears in the agent history.</span></span>  
  
     <span data-ttu-id="b438a-121">若出現多個代理程式的情況，則可能其中一個代理程式是被遺棄處理的結果。</span><span class="sxs-lookup"><span data-stu-id="b438a-121">In a situation where it appears there are multiple agents, it is possible that one of them is the result of an orphaned process.</span></span>  
  
-   <span data-ttu-id="b438a-122">如果已發行資料庫的「記錄讀取器代理程式」已啟動，而使用者針對相同的資料庫執行 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds** ，則錯誤就會在執行預存程序 (例如 **sqlcmd**) 的應用程式中產生。</span><span class="sxs-lookup"><span data-stu-id="b438a-122">If the Log Reader Agent for a published database is started and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** against the same database, the error is raised in the application where the stored procedure was executed (such as **sqlcmd**).</span></span>  
  
-   <span data-ttu-id="b438a-123">如果已發行資料庫的「記錄讀取器代理程式」未在執行，且使用者執行了 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds** ，之後也未關閉執行該程序的連接，則當「記錄讀取器代理程式」嘗試連接到資料庫時就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b438a-123">If no Log Reader Agent is running for a published database and a user executes **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** and then does not close the connection over which the procedure was executed, the error is raised when the Log Reader Agent attempts to connect to the database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b438a-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b438a-124">User Action</span></span>  
 <span data-ttu-id="b438a-125">下列步驟可以幫助您對此問題進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="b438a-125">The following steps can help you to troubleshoot the problem.</span></span> <span data-ttu-id="b438a-126">如果任一步驟允許「記錄讀取器代理程式」在沒有錯誤的情況下啟動，則無需完成剩餘步驟。</span><span class="sxs-lookup"><span data-stu-id="b438a-126">If any step allows the Log Reader Agent to start without errors, there is no need to complete the remaining steps.</span></span>  
  
-   <span data-ttu-id="b438a-127">檢查「記錄讀取器代理程式」的記錄，以便尋找可能導致此錯誤的其他任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="b438a-127">Check the history of the Log Reader agent for any other errors that could be contributing to this error.</span></span> <span data-ttu-id="b438a-128">如需有關在「複寫監視器」中檢視代理程式狀態和錯誤詳細資料的資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="b438a-128">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="b438a-129">檢查 [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) 的輸出，以尋找連接到已發行資料庫之特定處理序識別碼 (SPID)。</span><span class="sxs-lookup"><span data-stu-id="b438a-129">Check the output of [sp_who &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) for specific process identification numbers (SPIDs) that are connected to the published database.</span></span> <span data-ttu-id="b438a-130">關閉可能已執行 **sp_repldone**、 **sp_replcmds**或 **sp_replshowcmds**的任何連接。</span><span class="sxs-lookup"><span data-stu-id="b438a-130">Close any connections that might have run **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds**.</span></span>  
  
-   <span data-ttu-id="b438a-131">重新啟動「記錄讀取器代理程式」。</span><span class="sxs-lookup"><span data-stu-id="b438a-131">Restart the Log Reader Agent.</span></span> <span data-ttu-id="b438a-132">如需詳細資訊，請參閱[啟動和停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="b438a-132">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="b438a-133">在「散發者」上重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務 (使其在叢集中離線或上線)。</span><span class="sxs-lookup"><span data-stu-id="b438a-133">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service (bring it offline or online in a cluster) on the Distributor.</span></span> <span data-ttu-id="b438a-134">如果已排程作業可能已經從其他任何 **執行個體執行**sp_repldone **、** sp_replcmds **或** sp_replshowcmds [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，則重新啟動那些執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="b438a-134">If there is possibility that a scheduled job could have executed **sp_repldone**, **sp_replcmds**, or **sp_replshowcmds** from any other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for those instances as well.</span></span> <span data-ttu-id="b438a-135">如需詳細資訊，請參閱[啟動、停止或暫停 SQL Server Agent 服務](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b438a-135">For more information, see [Start, Stop, or Pause the SQL Server Agent Service](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md).</span></span>  
  
-   <span data-ttu-id="b438a-136">在發行集資料庫上的「發行者」端執行 [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql)，然後重新啟動記錄讀取器代理程式。</span><span class="sxs-lookup"><span data-stu-id="b438a-136">Execute [sp_replflush &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) at the Publisher on the publication database, and then restart the Log Reader Agent.</span></span>  
  
-   <span data-ttu-id="b438a-137">若錯誤繼續發生，請增加代理程式的記錄，並指定記錄的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="b438a-137">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="b438a-138">視錯誤內容的不同，可提供導致錯誤的步驟和 (或) 其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="b438a-138">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b438a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b438a-139">See Also</span></span>  
 <span data-ttu-id="b438a-140">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="b438a-140">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="b438a-141">複寫記錄讀取器代理程式</span><span class="sxs-lookup"><span data-stu-id="b438a-141">Replication Log Reader Agent</span></span>](agents/replication-log-reader-agent.md)  
  
  
