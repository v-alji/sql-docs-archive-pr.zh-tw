---
title: MSSQL_REPL027056 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027056 error
ms.assetid: 92d62f3c-b8ae-482e-a348-2e9a8ee9786e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44fb130321ec54c39559d52e493cc8f3424172fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705038"
---
# <a name="mssql_repl027056"></a><span data-ttu-id="147f8-102">MSSQL_REPL027056</span><span class="sxs-lookup"><span data-stu-id="147f8-102">MSSQL_REPL027056</span></span>
    
## <a name="message-details"></a><span data-ttu-id="147f8-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="147f8-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="147f8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="147f8-104">Product Name</span></span>|<span data-ttu-id="147f8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="147f8-105">SQL Server</span></span>|  
|<span data-ttu-id="147f8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="147f8-106">Event ID</span></span>|<span data-ttu-id="147f8-107">27056</span><span class="sxs-lookup"><span data-stu-id="147f8-107">27056</span></span>|  
|<span data-ttu-id="147f8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="147f8-108">Event Source</span></span>|<span data-ttu-id="147f8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="147f8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="147f8-110">元件</span><span class="sxs-lookup"><span data-stu-id="147f8-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="147f8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="147f8-111">Symbolic Name</span></span>||  
|<span data-ttu-id="147f8-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="147f8-112">Message Text</span></span>|<span data-ttu-id="147f8-113">合併處理無法變更生成集記錄 '%1'。</span><span class="sxs-lookup"><span data-stu-id="147f8-113">The merge process was unable to change generation history at the '%1'.</span></span> <span data-ttu-id="147f8-114">執行疑難排解時，以詳細資訊記錄重新啟動同步處理，並指定要寫入的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="147f8-114">When troubleshooting, restart the synchronization with verbose history logging and specify an output file to which to write.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="147f8-115">說明</span><span class="sxs-lookup"><span data-stu-id="147f8-115">Explanation</span></span>  
 <span data-ttu-id="147f8-116">這個錯誤通常由成長過大之合併式複寫系統資料表中的競爭問題引起。</span><span class="sxs-lookup"><span data-stu-id="147f8-116">This error is typically raised as a result of contention in merge replication system tables that have grown excessively large.</span></span> <span data-ttu-id="147f8-117">大型系統資料表通常是由較長的發行集保留期限所引起，因為在達到保留期限之前，中繼資料必須儲存於這些資料表中。</span><span class="sxs-lookup"><span data-stu-id="147f8-117">Large system tables are typically caused by a long publication retention period, because metadata must be stored in these tables until the retention period is reached.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="147f8-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="147f8-118">User Action</span></span>  
 <span data-ttu-id="147f8-119">**若要解決這個問題：**</span><span class="sxs-lookup"><span data-stu-id="147f8-119">**To resolve the issue:**</span></span>  
  
1.  <span data-ttu-id="147f8-120">減少「合併代理程式」-**DownloadGenerationsPerBatch** 和 **-UploadGenerationsPerBatch** 參數的值，以便在您解決造成此錯誤的基礎問題時讓處理繼續進行。</span><span class="sxs-lookup"><span data-stu-id="147f8-120">Decrease the value of the -**DownloadGenerationsPerBatch** and **-UploadGenerationsPerBatch** parameters for the Merge Agent to allow processing to continue while you address the underlying issue causing the error.</span></span> <span data-ttu-id="147f8-121">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="147f8-121">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="147f8-122">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="147f8-122">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="147f8-123">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="147f8-123">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="147f8-124">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="147f8-124">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="147f8-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="147f8-125">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
2.  <span data-ttu-id="147f8-126">為發行集保留期限指定儘可能低的設定。</span><span class="sxs-lookup"><span data-stu-id="147f8-126">Specify the lowest setting possible for the publication retention period.</span></span> <span data-ttu-id="147f8-127">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="147f8-127">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
3.  <span data-ttu-id="147f8-128">做為合併式複寫維護的一部份，請不時檢查與合併式複寫相關聯的系統資料表成長： **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**和 **MSmerge_past_partition_mappings**。</span><span class="sxs-lookup"><span data-stu-id="147f8-128">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="147f8-129">定期重新整理資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="147f8-129">Periodically re-index these tables.</span></span> <span data-ttu-id="147f8-130">如需詳細資訊，請參閱 [重新組織與重建索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="147f8-130">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147f8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147f8-131">See Also</span></span>  
 [<span data-ttu-id="147f8-132">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="147f8-132">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
