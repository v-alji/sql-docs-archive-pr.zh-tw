---
title: " (查詢執行的選項： SQL Server： Advanced Page) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionAdvanced
ms.assetid: 3ec788c7-22c3-4216-9ad0-81a168d17074
author: rothja
ms.author: jroth
ms.openlocfilehash: 3efc3dc8b42fc08969cc1afb85d4e629f6759e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599647"
---
# <a name="options-query-executionsql-serveradvanced-page"></a><span data-ttu-id="190f6-102">選項 (查詢執行：SQL Server：進階頁面)</span><span class="sxs-lookup"><span data-stu-id="190f6-102">Options (Query Execution:SQL Server:Advanced Page)</span></span>
  <span data-ttu-id="190f6-103">使用 SET 命令有許多選項可用。</span><span class="sxs-lookup"><span data-stu-id="190f6-103">Several options are available using the SET command.</span></span> <span data-ttu-id="190f6-104">使用此頁面來指定 **設定** 選項，以在 SQL Server 查詢編輯器中執行 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="190f6-104">Use this page to specify a **set** option for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries in the SQL Server Query Editor.</span></span> <span data-ttu-id="190f6-105">它們對於其他程式碼編輯器沒有影響。</span><span class="sxs-lookup"><span data-stu-id="190f6-105">They have no effect on other code editors.</span></span> <span data-ttu-id="190f6-106">這些選項的變更僅適用於新的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="190f6-106">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="190f6-107">若要變更目前查詢的選項，請按一下 **[查詢]** 功能表上的 **[查詢選項]** ，或按一下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢視窗的快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="190f6-107">To change the options for the current queries, click **Query Options** on the **Query** menu or the shortcut menu of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window.</span></span> <span data-ttu-id="190f6-108">在 **[執行]** 下，按一下 **[進階]**。</span><span class="sxs-lookup"><span data-stu-id="190f6-108">Under **Execution**, click **Advanced**.</span></span> <span data-ttu-id="190f6-109">如需上述各項目的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="190f6-109">For more information on each of these, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="options"></a><span data-ttu-id="190f6-110">選項</span><span class="sxs-lookup"><span data-stu-id="190f6-110">Options</span></span>  
 <span data-ttu-id="190f6-111">**SET NOCOUNT**</span><span class="sxs-lookup"><span data-stu-id="190f6-111">**SET NOCOUNT**</span></span>  
 <span data-ttu-id="190f6-112">不會以結果集的訊息傳回資料列數的計數。</span><span class="sxs-lookup"><span data-stu-id="190f6-112">Does not return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="190f6-113">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-113">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-114">**SET NOEXEC**</span><span class="sxs-lookup"><span data-stu-id="190f6-114">**SET NOEXEC**</span></span>  
 <span data-ttu-id="190f6-115">不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="190f6-115">Does not run the query.</span></span> <span data-ttu-id="190f6-116">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-116">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-117">**SET PARSEONLY**</span><span class="sxs-lookup"><span data-stu-id="190f6-117">**SET PARSEONLY**</span></span>  
 <span data-ttu-id="190f6-118">檢查每個查詢的語法，但不會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="190f6-118">Checks the syntax of each query but does not run the queries.</span></span> <span data-ttu-id="190f6-119">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-119">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-120">**SET CONCAT_NULL_YIELDS_NULL**</span><span class="sxs-lookup"><span data-stu-id="190f6-120">**SET CONCAT_NULL_YIELDS_NULL**</span></span>  
 <span data-ttu-id="190f6-121">如果選取此核取方塊，串連現有值與 NULL 的查詢，一律會傳回 NULL 的結果。</span><span class="sxs-lookup"><span data-stu-id="190f6-121">When this check box is selected, queries that concatenate an existing value with a NULL, always return a NULL as the result.</span></span> <span data-ttu-id="190f6-122">如果清除此核取方塊，現有的值與 NULL 串連，則會傳回現有的值。</span><span class="sxs-lookup"><span data-stu-id="190f6-122">When this check box is cleared, an existing value concatenated with a NULL, returns the existing value.</span></span> <span data-ttu-id="190f6-123">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="190f6-123">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="190f6-124">**SET ARITHABORT**</span><span class="sxs-lookup"><span data-stu-id="190f6-124">**SET ARITHABORT**</span></span>  
 <span data-ttu-id="190f6-125">如果選取此核取方塊，INSERT、DELETE 或 UPDATE 陳述式在運算式評估期間發現算術錯誤 (溢位、除以零或網域錯誤) 時，就會結束查詢或批次。</span><span class="sxs-lookup"><span data-stu-id="190f6-125">When this check box is selected, when an INSERT, DELETE, or UPDATE statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="190f6-126">如果清除此核取方塊，在可能的情況下就會為該值提供 NULL，而查詢會繼續進行，並在結果中包含訊息。</span><span class="sxs-lookup"><span data-stu-id="190f6-126">When this check box is cleared, a NULL is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="190f6-127">如需詳細資訊，請參閱 [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="190f6-127">For more information, see [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).</span></span> <span data-ttu-id="190f6-128">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="190f6-128">This check box is selected by default.</span></span>  
  
 <span data-ttu-id="190f6-129">**SET SHOWPLAN_TEXT**</span><span class="sxs-lookup"><span data-stu-id="190f6-129">**SET SHOWPLAN_TEXT**</span></span>  
 <span data-ttu-id="190f6-130">如果選取此核取方塊，查詢計畫就會以文字格式傳回每個查詢。</span><span class="sxs-lookup"><span data-stu-id="190f6-130">When this check box is selected, the query plan is returned in text format with each query.</span></span> <span data-ttu-id="190f6-131">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-131">This check box cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-132">**SET STATISTICS TIME**</span><span class="sxs-lookup"><span data-stu-id="190f6-132">**SET STATISTICS TIME**</span></span>  
 <span data-ttu-id="190f6-133">如果選取此核取方塊，則每個查詢就會一併傳回時間統計資料。</span><span class="sxs-lookup"><span data-stu-id="190f6-133">When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="190f6-134">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-134">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-135">**SET STATISTICS IO**</span><span class="sxs-lookup"><span data-stu-id="190f6-135">**SET STATISTICS IO**</span></span>  
 <span data-ttu-id="190f6-136">如果選取此核取方塊，則每個查詢就會傳回關於輸入與輸出的統計資料。</span><span class="sxs-lookup"><span data-stu-id="190f6-136">When this check box is selected, statistics regarding input and output are returned with each query.</span></span> <span data-ttu-id="190f6-137">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-137">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-138">**SET TRANSACTION ISOLATION LEVEL**</span><span class="sxs-lookup"><span data-stu-id="190f6-138">**SET TRANSACTION ISOLATION LEVEL**</span></span>  
 <span data-ttu-id="190f6-139">依預設，會設定 READ COMMITTED 交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="190f6-139">The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="190f6-140">如需詳細資訊，請參閱 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="190f6-140">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="190f6-141">無法使用 SNAPSHOT 交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="190f6-141">SNAPSHOT transaction isolation level is not available.</span></span> <span data-ttu-id="190f6-142">若要使用 SNAPSHOT 隔離，請加入下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="190f6-142">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>  
  
```  
SET TRANSACTION ISOLATION LEVEL SNAPSHOT;  
GO  
```  
  
 <span data-ttu-id="190f6-143">**SET DEADLOCK PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="190f6-143">**SET DEADLOCK PRIORITY**</span></span>  
 <span data-ttu-id="190f6-144">預設值為「標準」，可在死結發生時讓每個查詢都有相同的優先權。</span><span class="sxs-lookup"><span data-stu-id="190f6-144">The default value of Normal allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="190f6-145">如果您要此查詢在發生任何死結衝突時失敗，並選取為要結束的查詢，請選取「低」優先權。</span><span class="sxs-lookup"><span data-stu-id="190f6-145">Select a priority of Low if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>  
  
 <span data-ttu-id="190f6-146">**SET LOCK TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="190f6-146">**SET LOCK TIMEOUT**</span></span>  
 <span data-ttu-id="190f6-147">預設值 -1 指出完成交易之前會保持鎖定。</span><span class="sxs-lookup"><span data-stu-id="190f6-147">The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="190f6-148">值為 0 表示根本不等候，並在發生鎖定時立刻傳回訊息。</span><span class="sxs-lookup"><span data-stu-id="190f6-148">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="190f6-149">提供大於 0 毫秒的值，即可指定當交易的鎖定時間超過指定值，就結束交易。</span><span class="sxs-lookup"><span data-stu-id="190f6-149">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>  
  
 <span data-ttu-id="190f6-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="190f6-150">**SET QUERY_GOVERNOR_COST_LIMIT**</span></span>  
 <span data-ttu-id="190f6-151">使用 **QUERY_GOVERNOR_COST_LIMIT** 選項，即可指定查詢執行的時間上限。</span><span class="sxs-lookup"><span data-stu-id="190f6-151">Use the **QUERY_GOVERNOR_COST_LIMIT** option to specify an upper limit for the time in which a query can run.</span></span> <span data-ttu-id="190f6-152">查詢成本代表在特定的硬體組態上，預估完成查詢所需的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="190f6-152">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="190f6-153">預設值為 0 表示查詢執行沒有時間長度的限制。</span><span class="sxs-lookup"><span data-stu-id="190f6-153">The default setting of 0 indicates no limit to the length of time a query will run.</span></span>  
  
 <span data-ttu-id="190f6-154">**抑制提供者訊息標頭**</span><span class="sxs-lookup"><span data-stu-id="190f6-154">**Suppress provider message headers**</span></span>  
 <span data-ttu-id="190f6-155">選取此核取方塊時，不會顯示來自提供者 (例如 SQLClient 提供者) 的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="190f6-155">When this check box is selected, status messages from the provider (such as the SQLClient provider) are not displayed.</span></span> <span data-ttu-id="190f6-156">依預設，這個核取方塊為已選取。</span><span class="sxs-lookup"><span data-stu-id="190f6-156">This check box is selected by default.</span></span> <span data-ttu-id="190f6-157">當疑難排解查詢於提供者層級失敗時，清除此核取方塊即可查看提供者訊息。</span><span class="sxs-lookup"><span data-stu-id="190f6-157">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>  
  
 <span data-ttu-id="190f6-158">**查詢執行後中斷連接**</span><span class="sxs-lookup"><span data-stu-id="190f6-158">**Disconnect after the query executes**</span></span>  
 <span data-ttu-id="190f6-159">如果選取此核取方塊，查詢完成後會結束 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的連接。</span><span class="sxs-lookup"><span data-stu-id="190f6-159">When this check box is selected, the connection to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is terminated after the query completes.</span></span> <span data-ttu-id="190f6-160">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="190f6-160">This check box is cleared by default.</span></span>  
  
 <span data-ttu-id="190f6-161">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="190f6-161">**Reset to Default**</span></span>  
 <span data-ttu-id="190f6-162">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="190f6-162">Resets all values on this page to the original default values.</span></span>  
  
  
