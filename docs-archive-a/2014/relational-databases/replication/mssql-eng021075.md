---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f2428038326681f5f8eb877e5c3017ced30f00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598290"
---
# <a name="mssql_eng021075"></a><span data-ttu-id="19523-102">MSSQL_ENG021075</span><span class="sxs-lookup"><span data-stu-id="19523-102">MSSQL_ENG021075</span></span>
    
## <a name="message-details"></a><span data-ttu-id="19523-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="19523-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19523-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19523-104">Product Name</span></span>|<span data-ttu-id="19523-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19523-105">SQL Server</span></span>|  
|<span data-ttu-id="19523-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19523-106">Event ID</span></span>|<span data-ttu-id="19523-107">21075</span><span class="sxs-lookup"><span data-stu-id="19523-107">21075</span></span>|  
|<span data-ttu-id="19523-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="19523-108">Event Source</span></span>|<span data-ttu-id="19523-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19523-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19523-110">元件</span><span class="sxs-lookup"><span data-stu-id="19523-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="19523-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19523-111">Symbolic Name</span></span>||  
|<span data-ttu-id="19523-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19523-112">Message Text</span></span>|<span data-ttu-id="19523-113">發行集 '%s' 的初始快照集尚無法使用。</span><span class="sxs-lookup"><span data-stu-id="19523-113">The initial snapshot for publication '%s' is not yet available.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19523-114">說明</span><span class="sxs-lookup"><span data-stu-id="19523-114">Explanation</span></span>  
 <span data-ttu-id="19523-115">如果在「快照集代理程式」完成快照集的產生之前啟動「散發代理程式」或「合併代理程式」，會引發錯誤 MSSQL_ENG021075。</span><span class="sxs-lookup"><span data-stu-id="19523-115">Error MSSQL_ENG021075 is raised if the Distribution Agent or Merge Agent is started before the Snapshot Agent has finished generating the snapshot.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19523-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19523-116">User Action</span></span>  
 <span data-ttu-id="19523-117">如果在建立訂閱或上次選擇重新初始化訂閱後未啟動發行集的「快照集代理程式」，請啟動「快照集代理程式」，並讓其在啟動「散發代理程式」或「合併代理程式」之前完成。</span><span class="sxs-lookup"><span data-stu-id="19523-117">If the Snapshot Agent for the publication has not been started since the subscription was created, or if it has not been started since the last time you chose to reinitialize the subscription, start the Snapshot Agent and let it complete before starting the Distribution Agent or Merge Agent.</span></span> <span data-ttu-id="19523-118">如需詳細資訊，請參閱[建立和套用快照集](create-and-apply-the-snapshot.md)。</span><span class="sxs-lookup"><span data-stu-id="19523-118">For more information, see [Create and Apply the Snapshot](create-and-apply-the-snapshot.md).</span></span>  
  
 <span data-ttu-id="19523-119">若快照集代理程式未完成，請檢查快照集代理程式記錄，以便找出錯誤並加以解決。</span><span class="sxs-lookup"><span data-stu-id="19523-119">If the Snapshot Agent does not complete, check the Snapshot Agent history for errors and address them.</span></span> <span data-ttu-id="19523-120">如需有關在「複寫監視器」中檢視代理程式狀態和錯誤詳細資料的資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="19523-120">For information about viewing agent status and error details in Replication Monitor, see [View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="19523-121">若錯誤繼續發生，請增加代理程式的記錄，並指定記錄的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="19523-121">If the error continues to occur, increase the logging of the agent and specify an output file for the log.</span></span> <span data-ttu-id="19523-122">視錯誤內容的不同，可提供導致錯誤的步驟和 (或) 其他錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="19523-122">Depending on the context of the error, this could provide the steps leading up to the error and/or additional error messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19523-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19523-123">See Also</span></span>  
 [<span data-ttu-id="19523-124">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="19523-124">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
