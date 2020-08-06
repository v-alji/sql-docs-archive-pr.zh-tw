---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2796451f6f681cfb0ce529ed44a946c34135649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585302"
---
# <a name="mssql_eng014151"></a><span data-ttu-id="d8430-102">MSSQL_ENG014151</span><span class="sxs-lookup"><span data-stu-id="d8430-102">MSSQL_ENG014151</span></span>
    
## <a name="message-details"></a><span data-ttu-id="d8430-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8430-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8430-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d8430-104">Product Name</span></span>|<span data-ttu-id="d8430-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d8430-105">SQL Server</span></span>|  
|<span data-ttu-id="d8430-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d8430-106">Event ID</span></span>|<span data-ttu-id="d8430-107">14151</span><span class="sxs-lookup"><span data-stu-id="d8430-107">14151</span></span>|  
|<span data-ttu-id="d8430-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d8430-108">Event Source</span></span>|<span data-ttu-id="d8430-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d8430-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d8430-110">元件</span><span class="sxs-lookup"><span data-stu-id="d8430-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="d8430-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d8430-111">Symbolic Name</span></span>||  
|<span data-ttu-id="d8430-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d8430-112">Message Text</span></span>|<span data-ttu-id="d8430-113">複寫 -%s：代理程式 %s 失敗。</span><span class="sxs-lookup"><span data-stu-id="d8430-113">Replication-%s: agent %s failed.</span></span> <span data-ttu-id="d8430-114">%s</span><span class="sxs-lookup"><span data-stu-id="d8430-114">%s</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d8430-115">說明</span><span class="sxs-lookup"><span data-stu-id="d8430-115">Explanation</span></span>  
 <span data-ttu-id="d8430-116">任何複寫代理程式的失敗均會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8430-116">This error is raised for any replication agent failure.</span></span> <span data-ttu-id="d8430-117">訊息結尾處的文字視失敗的內容而定。</span><span class="sxs-lookup"><span data-stu-id="d8430-117">The text at the end of the message depends on the context of the failure.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d8430-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d8430-118">User Action</span></span>  
 <span data-ttu-id="d8430-119">此錯誤在許多情況下都會出現；請視需要使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="d8430-119">This error can occur in a number of situations; use the following approaches as necessary:</span></span>  
  
-   <span data-ttu-id="d8430-120">重新啟動失敗的代理程式，查看現在執行是否已無錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8430-120">Restart the failed agent to see if it will now run without failures.</span></span> <span data-ttu-id="d8430-121">如需詳細資訊，請參閱[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 與[複寫代理程式可執行檔概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="d8430-121">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="d8430-122">請檢查代理程式記錄和作業記錄是否同時發生其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8430-122">Check the agent history and job history for other errors that occurred around the same time.</span></span> <span data-ttu-id="d8430-123">如需有關在「複寫監視器」中檢視代理程式狀態和錯誤詳細資料的資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="d8430-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
-   <span data-ttu-id="d8430-124">確認在由代理程式存取的電腦之間是否使用基本連接，然後使用類似 [sqlcmd Utility](../../tools/sqlcmd-utility.md)的公用程式連接到各台電腦。</span><span class="sxs-lookup"><span data-stu-id="d8430-124">Verify that basic connectivity is working between the computers accessed by the agent, and then connect to each computer with a utility like the [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span> <span data-ttu-id="d8430-125">連接時，請使用代理程式建立連接的相同帳戶。</span><span class="sxs-lookup"><span data-stu-id="d8430-125">When connecting, use the same account under which the agent makes connections.</span></span> <span data-ttu-id="d8430-126">如需各代理程式帳戶所需權限的詳細資訊，請參閱＜ [Replication Agent Security Model](security/replication-agent-security-model.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d8430-126">For more information about the permissions required by each agent account, see [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
-   <span data-ttu-id="d8430-127">如果在建立或套用快照集時發生錯誤，則請檢查快照集目錄中的檔案以找到錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8430-127">If the error occurs while creating or applying a snapshot, check the files in the snapshot directory for errors.</span></span>  
  
-   <span data-ttu-id="d8430-128">若錯誤繼續發生，請增加代理程式的記錄，並指定記錄的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d8430-128">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="d8430-129">視錯誤內容的不同，可提供導致錯誤的步驟和 (或) 其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d8430-129">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8430-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8430-130">See Also</span></span>  
 <span data-ttu-id="d8430-131">[複寫代理程式管理](agents/replication-agent-administration.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-131">[Replication Agent Administration](agents/replication-agent-administration.md) </span></span>  
 <span data-ttu-id="d8430-132">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-132">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 <span data-ttu-id="d8430-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-133">[Replication Distribution Agent](agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="d8430-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-134">[Replication Log Reader Agent](agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="d8430-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-135">[Replication Merge Agent](agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="d8430-136">[複寫佇列讀取器代理程式](agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="d8430-136">[Replication Queue Reader Agent](agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="d8430-137">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="d8430-137">Replication Snapshot Agent</span></span>](agents/replication-snapshot-agent.md)  
  
  
