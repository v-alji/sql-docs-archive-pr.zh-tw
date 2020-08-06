---
title: MSSQL_REPL027183 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL027183 error
ms.assetid: 52c271ac-1a0e-43d5-85d4-35886d1efd32
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4484318cd6ec6ff4f0b201be69dc9b7544dd2c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709154"
---
# <a name="mssql_repl027183"></a><span data-ttu-id="61031-102">MSSQL_REPL027183</span><span class="sxs-lookup"><span data-stu-id="61031-102">MSSQL_REPL027183</span></span>
    
## <a name="message-details"></a><span data-ttu-id="61031-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="61031-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61031-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="61031-104">Product Name</span></span>|<span data-ttu-id="61031-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="61031-105">SQL Server</span></span>|  
|<span data-ttu-id="61031-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="61031-106">Event ID</span></span>|<span data-ttu-id="61031-107">27183</span><span class="sxs-lookup"><span data-stu-id="61031-107">27183</span></span>|  
|<span data-ttu-id="61031-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="61031-108">Event Source</span></span>|<span data-ttu-id="61031-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="61031-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="61031-110">元件</span><span class="sxs-lookup"><span data-stu-id="61031-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="61031-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="61031-111">Symbolic Name</span></span>||  
|<span data-ttu-id="61031-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="61031-112">Message Text</span></span>|<span data-ttu-id="61031-113">合併處理無法以參數化資料列篩選器來列舉發行項的變更。</span><span class="sxs-lookup"><span data-stu-id="61031-113">The merge process failed to enumerate changes in articles with parameterized row filters.</span></span> <span data-ttu-id="61031-114">如果這個失敗繼續發生，請增加這個處理的查詢逾時、縮短發行集的保留期限，以及改善發行資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="61031-114">If this failure continues, increase the query timeout for this process, reduce the retention period for the publication, and improve indexes on published tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61031-115">說明</span><span class="sxs-lookup"><span data-stu-id="61031-115">Explanation</span></span>  
 <span data-ttu-id="61031-116">如果在已篩選發行集中處理變更時發生「合併代理程式」逾時，則會出現此錯誤。</span><span class="sxs-lookup"><span data-stu-id="61031-116">This error is raised if a Merge Agent timeout occurs while processing changes in a filtered publication.</span></span> <span data-ttu-id="61031-117">逾時可能是由下列問題其中之一造成：</span><span class="sxs-lookup"><span data-stu-id="61031-117">The timeout might be caused by one of the following issues:</span></span>  
  
-   <span data-ttu-id="61031-118">未使用預先計算分割區最佳化。</span><span class="sxs-lookup"><span data-stu-id="61031-118">Not using the precomputed partitions optimization.</span></span>  
  
-   <span data-ttu-id="61031-119">資料行上索引片段已用於篩選。</span><span class="sxs-lookup"><span data-stu-id="61031-119">Index fragmentation on columns used for filtering.</span></span>  
  
-   <span data-ttu-id="61031-120">大型合併中繼資料表，例如 **MSmerge_tombstone**、 **MSmerge_contents**和 **MSmerge_genhistory**。</span><span class="sxs-lookup"><span data-stu-id="61031-120">Large merge metadata tables, such as **MSmerge_tombstone**, **MSmerge_contents**, and **MSmerge_genhistory**.</span></span>  
  
-   <span data-ttu-id="61031-121">已篩選資料表未聯結在唯一索引鍵上，並且聯結包含大量資料表的篩選。</span><span class="sxs-lookup"><span data-stu-id="61031-121">Filtered tables that are not joined on a unique key and join filters that involve a large number of tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61031-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="61031-122">User Action</span></span>  
 <span data-ttu-id="61031-123">若要解決此問題：</span><span class="sxs-lookup"><span data-stu-id="61031-123">To resolve the issue:</span></span>  
  
-   <span data-ttu-id="61031-124">如果您在解決基礎問題時出現此錯誤，則可以增加「合併代理程式」的 **-QueryTimeOut** 參數值，以便處理繼續進行。</span><span class="sxs-lookup"><span data-stu-id="61031-124">Increase the value of the **-QueryTimeOut** parameter for the Merge Agent to allow processing to continue while you address the underlying issues causing the error.</span></span> <span data-ttu-id="61031-125">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="61031-125">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="61031-126">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="61031-126">For more information, see:</span></span>  
  
    -   [<span data-ttu-id="61031-127">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="61031-127">Work with Replication Agent Profiles</span></span>](agents/replication-agent-profiles.md)  
  
    -   [<span data-ttu-id="61031-128">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="61031-128">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
    -   <span data-ttu-id="61031-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md)的最小和最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="61031-129">[Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
-   <span data-ttu-id="61031-130">儘可能使用預先計算分割區最佳化。</span><span class="sxs-lookup"><span data-stu-id="61031-130">Use the precomputed partitions optimization if possible.</span></span> <span data-ttu-id="61031-131">如果符合一些發行集需求，則依預設使用此最佳化。</span><span class="sxs-lookup"><span data-stu-id="61031-131">This optimization is used by default if a number of publication requirements are met.</span></span> <span data-ttu-id="61031-132">如需這些需求的詳細資訊，請參閱[使用預先計算的資料分割最佳化參數化篩選效能](merge/parameterized-filters-optimize-for-precomputed-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="61031-132">For more information about these requirements, see [Optimize Parameterized Filter Performance with Precomputed Partitions](merge/parameterized-filters-optimize-for-precomputed-partitions.md).</span></span> <span data-ttu-id="61031-133">如果發行集不符合這些需求，則請考慮重新設計此發行集。</span><span class="sxs-lookup"><span data-stu-id="61031-133">If the publication does not meet these requirements, consider redesigning the publication.</span></span>  
  
-   <span data-ttu-id="61031-134">為發行集保留期限指定可能的最低設定，因為只有在達到保留期限時，複寫才可以清除發行集與訂閱資料庫中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="61031-134">Specify the lowest setting possible for the publication retention period, because replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="61031-135">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="61031-135">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
-   <span data-ttu-id="61031-136">做為合併式複寫維護的一部份，請不時檢查與合併式複寫相關聯的系統資料表成長： **MSmerge_contents**、 **MSmerge_genhistory**、 **MSmerge_tombstone**、 **MSmerge_current_partition_mappings**和 **MSmerge_past_partition_mappings**。</span><span class="sxs-lookup"><span data-stu-id="61031-136">As part of maintenance for merge replication, occasionally check the growth of the system tables associated with merge replication: **MSmerge_contents**, **MSmerge_genhistory**, and **MSmerge_tombstone**, **MSmerge_current_partition_mappings**, and **MSmerge_past_partition_mappings**.</span></span> <span data-ttu-id="61031-137">定期重新整理資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="61031-137">Periodically re-index these tables.</span></span> <span data-ttu-id="61031-138">如需詳細資訊，請參閱 [重新組織與重建索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="61031-138">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="61031-139">確定用於篩選的資料行索引正確，並在需要時重建這些索引。</span><span class="sxs-lookup"><span data-stu-id="61031-139">Ensure that columns used for filtering are properly indexed and rebuild such indexes if necessary.</span></span> <span data-ttu-id="61031-140">如需詳細資訊，請參閱 [重新組織與重建索引](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="61031-140">For more information, see [Reorganize and Rebuild Indexes](../indexes/indexes.md).</span></span>  
  
-   <span data-ttu-id="61031-141">為基於唯一資料行的聯結篩選設定 **join_unique_key** 屬性。</span><span class="sxs-lookup"><span data-stu-id="61031-141">Set the **join_unique_key** property for join filters that are based on unique columns.</span></span> <span data-ttu-id="61031-142">如需相關資訊，請參閱 [Join Filters](merge/join-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="61031-142">For more information, see [Join Filters](merge/join-filters.md).</span></span>  
  
-   <span data-ttu-id="61031-143">限制聯結篩選階層中資料表的數量。</span><span class="sxs-lookup"><span data-stu-id="61031-143">Limit the number of tables in the join filter hierarchy.</span></span> <span data-ttu-id="61031-144">若您正在產生五個以上資料表的聯結篩選，請考慮其他方案：不要篩選小型、無法變更或主要為查詢資料表的資料表。</span><span class="sxs-lookup"><span data-stu-id="61031-144">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="61031-145">聯結篩選只能用於必須在訂閱中分割的資料表之間。</span><span class="sxs-lookup"><span data-stu-id="61031-145">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="61031-146">在同步處理之間少量變更已篩選的資料表，或更頻繁地執行「合併代理程式」。</span><span class="sxs-lookup"><span data-stu-id="61031-146">Make a smaller number of changes on filtered tables between synchronizations, or run the Merge Agent more frequently.</span></span> <span data-ttu-id="61031-147">如需有關設定同步排程的詳細資訊，請參閱＜ [Specify Synchronization Schedules](specify-synchronization-schedules.md)＞。</span><span class="sxs-lookup"><span data-stu-id="61031-147">For more information about setting synchronization schedules, see [Specify Synchronization Schedules](specify-synchronization-schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61031-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61031-148">See Also</span></span>  
 [<span data-ttu-id="61031-149">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="61031-149">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
