---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4161428767ce78726436c0cf794f5250140d35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697945"
---
# <a name="mssql_eng021076"></a><span data-ttu-id="42dba-102">MSSQL_ENG021076</span><span class="sxs-lookup"><span data-stu-id="42dba-102">MSSQL_ENG021076</span></span>
    
## <a name="message-details"></a><span data-ttu-id="42dba-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="42dba-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42dba-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="42dba-104">Product Name</span></span>|<span data-ttu-id="42dba-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="42dba-105">SQL Server</span></span>|  
|<span data-ttu-id="42dba-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="42dba-106">Event ID</span></span>|<span data-ttu-id="42dba-107">21076</span><span class="sxs-lookup"><span data-stu-id="42dba-107">21076</span></span>|  
|<span data-ttu-id="42dba-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="42dba-108">Event Source</span></span>|<span data-ttu-id="42dba-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="42dba-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="42dba-110">元件</span><span class="sxs-lookup"><span data-stu-id="42dba-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="42dba-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="42dba-111">Symbolic Name</span></span>||  
|<span data-ttu-id="42dba-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="42dba-112">Message Text</span></span>|<span data-ttu-id="42dba-113">發行項 '%s' 的初始快照集仍然無法使用。</span><span class="sxs-lookup"><span data-stu-id="42dba-113">The initial snapshot for article '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="42dba-114">說明</span><span class="sxs-lookup"><span data-stu-id="42dba-114">Explanation</span></span>  
 <span data-ttu-id="42dba-115">如果在「快照集代理程式」完成快照集的產生之前啟動「散發代理程式」，會引發錯誤 MSSQL_ENG021076。</span><span class="sxs-lookup"><span data-stu-id="42dba-115">Error MSSQL_ENG021076 can be raised if the Distribution Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span> <span data-ttu-id="42dba-116">只有在發行集包含單一發行項時才會引發該錯誤。</span><span class="sxs-lookup"><span data-stu-id="42dba-116">This error is raised only if the publication contains a single article.</span></span> <span data-ttu-id="42dba-117">如果發行集包含一個以上發行項，則會引發錯誤 MSSQL_ENG021075。</span><span class="sxs-lookup"><span data-stu-id="42dba-117">If the publication contains more than one article, MSSQL_ENG021075 is raised instead.</span></span> <span data-ttu-id="42dba-118">如需詳細資訊，請參閱 [MSSQL_ENG021075](mssql-eng021075.md)。</span><span class="sxs-lookup"><span data-stu-id="42dba-118">For more information, see [MSSQL_ENG021075](mssql-eng021075.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="42dba-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="42dba-119">User Action</span></span>  
 <span data-ttu-id="42dba-120">如果在建立訂閱或上次選擇重新初始化訂閱後未啟動發行集的「快照集代理程式」，請啟動「快照集代理程式」，並讓其在啟動「散發代理程式」之前完成。</span><span class="sxs-lookup"><span data-stu-id="42dba-120">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent.</span></span> <span data-ttu-id="42dba-121">如需詳細資訊，請參閱[建立和套用快照集](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="42dba-121">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="42dba-122">若快照集代理程式未完成，請檢查快照集代理程式記錄，以便找出錯誤並加以解決。</span><span class="sxs-lookup"><span data-stu-id="42dba-122">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="42dba-123">如需有關在「複寫監視器」中檢視代理程式狀態和錯誤詳細資料的資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="42dba-123">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="42dba-124">若錯誤繼續發生，請增加代理程式的記錄，並指定記錄的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="42dba-124">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="42dba-125">視錯誤內容的不同，可提供導致錯誤的步驟和 (或) 其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="42dba-125">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42dba-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42dba-126">See Also</span></span>  
 [<span data-ttu-id="42dba-127">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="42dba-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
