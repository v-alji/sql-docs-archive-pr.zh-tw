---
title: MSSQL_ENG020557 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 45c24d453eb95abaa967ae65ceb5934b7dee969e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606795"
---
# <a name="mssql_eng020557"></a><span data-ttu-id="85175-102">MSSQL_ENG020557</span><span class="sxs-lookup"><span data-stu-id="85175-102">MSSQL_ENG020557</span></span>
    
## <a name="message-details"></a><span data-ttu-id="85175-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="85175-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85175-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="85175-104">Product Name</span></span>|<span data-ttu-id="85175-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="85175-105">SQL Server</span></span>|  
|<span data-ttu-id="85175-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="85175-106">Event ID</span></span>|<span data-ttu-id="85175-107">20557</span><span class="sxs-lookup"><span data-stu-id="85175-107">20557</span></span>|  
|<span data-ttu-id="85175-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="85175-108">Event Source</span></span>|<span data-ttu-id="85175-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="85175-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="85175-110">元件</span><span class="sxs-lookup"><span data-stu-id="85175-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="85175-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="85175-111">Symbolic Name</span></span>||  
|<span data-ttu-id="85175-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="85175-112">Message Text</span></span>|<span data-ttu-id="85175-113">代理程式關閉。</span><span class="sxs-lookup"><span data-stu-id="85175-113">Agent shutdown.</span></span> <span data-ttu-id="85175-114">如需詳細資訊，請參閱 SQL Server Agent 作業記錄中的作業 '%s'。</span><span class="sxs-lookup"><span data-stu-id="85175-114">For more information, see the SQL Server Agent job history for job '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="85175-115">說明</span><span class="sxs-lookup"><span data-stu-id="85175-115">Explanation</span></span>  
 <span data-ttu-id="85175-116">複寫代理程式已關閉，而未將原因寫入適當的記錄資料表，或者代理程式在處理序仍執行時關閉。</span><span class="sxs-lookup"><span data-stu-id="85175-116">A replication agent has shut down without writing a reason to the appropriate history table, or the agent was shut down while in the middle of a process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85175-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="85175-117">User Action</span></span>  
  
-   <span data-ttu-id="85175-118">重新啟動代理程式，查看現在執行是否已無錯誤。</span><span class="sxs-lookup"><span data-stu-id="85175-118">Restart the agent to see whether it will now run without failures.</span></span> <span data-ttu-id="85175-119">如需詳細資訊，請參閱[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 與[複寫代理程式可執行檔概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="85175-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="85175-120">請檢查代理程式記錄和作業記錄是否同時發生其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="85175-120">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="85175-121">如需有關如何在「複寫監視器」中檢視代理程式狀態和錯誤詳細資料的資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="85175-121">For information about how to view agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>
-   <span data-ttu-id="85175-122">確認代理程式所存取電腦之間的基本連接能夠正常運作，然後使用公用程式 (例如 **sqlcmd** 公用程式) 連接每部電腦。</span><span class="sxs-lookup"><span data-stu-id="85175-122">Verify that basic connectivity is working between the computers that are accessed by the agent, and then connect to each computer by using a utility, such as the **sqlcmd** utility.</span></span> <span data-ttu-id="85175-123">連接時，請使用代理程式建立連接的相同帳戶。</span><span class="sxs-lookup"><span data-stu-id="85175-123">When you connect, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="85175-124">如需有關每個代理程式帳戶所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](security/replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="85175-124">For more information about the permissions that are required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="85175-125">如果在建立或套用快照集時發生錯誤，則請檢查快照集目錄中的檔案以找出錯誤。</span><span class="sxs-lookup"><span data-stu-id="85175-125">If the error occurs while you are creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="85175-126">若錯誤繼續發生，請增加代理程式的記錄，並指定記錄的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="85175-126">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="85175-127">視錯誤內容的不同，可提供導致錯誤的步驟和其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="85175-127">Depending on the context of the error, this could provide the steps leading up to the error and additional error messages.</span></span> <span data-ttu-id="85175-128">如需有關如何設定複寫記錄的詳細資訊，請參閱 Microsoft 知識庫文件 [312292](https://support.microsoft.com/kb/312292)。</span><span class="sxs-lookup"><span data-stu-id="85175-128">For more information about how to configure logging for replication, see the Microsoft Knowledge Base article [312292](https://support.microsoft.com/kb/312292).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85175-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85175-129">See Also</span></span>  
 [<span data-ttu-id="85175-130">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="85175-130">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
