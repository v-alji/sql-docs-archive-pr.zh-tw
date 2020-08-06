---
title: MSSQLSERVER_2814 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26b1fae5b683ed72cb93c3f81981bd41e2f4ad4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596041"
---
# <a name="mssqlserver_2814"></a><span data-ttu-id="08c2c-102">MSSQLSERVER_2814</span><span class="sxs-lookup"><span data-stu-id="08c2c-102">MSSQLSERVER_2814</span></span>
    
## <a name="details"></a><span data-ttu-id="08c2c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="08c2c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08c2c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="08c2c-104">Product Name</span></span>|<span data-ttu-id="08c2c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="08c2c-105">SQL Server</span></span>|  
|<span data-ttu-id="08c2c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="08c2c-106">Event ID</span></span>|<span data-ttu-id="08c2c-107">2814</span><span class="sxs-lookup"><span data-stu-id="08c2c-107">2814</span></span>|  
|<span data-ttu-id="08c2c-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="08c2c-108">Event Source</span></span>|<span data-ttu-id="08c2c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="08c2c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="08c2c-110">元件</span><span class="sxs-lookup"><span data-stu-id="08c2c-110">Component</span></span>|<span data-ttu-id="08c2c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="08c2c-111">SQLEngine</span></span>|  
|<span data-ttu-id="08c2c-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="08c2c-112">Symbolic Name</span></span>|<span data-ttu-id="08c2c-113">PR_POSSIBLE_INFINITE_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="08c2c-113">PR_POSSIBLE_INFINITE_RECOMPILE</span></span>|  
|<span data-ttu-id="08c2c-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="08c2c-114">Message Text</span></span>|<span data-ttu-id="08c2c-115">偵測到 SQLHANDLE %hs、PlanHandle %hs、起始位移 %d、結尾位移 %d 可能發生無限重新編譯。</span><span class="sxs-lookup"><span data-stu-id="08c2c-115">A possible infinite recompile was detected for SQLHANDLE %hs, PlanHandle %hs, starting offset %d, ending offset %d.</span></span> <span data-ttu-id="08c2c-116">上次重新編譯的原因是 %d。</span><span class="sxs-lookup"><span data-stu-id="08c2c-116">The last recompile reason was %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="08c2c-117">說明</span><span class="sxs-lookup"><span data-stu-id="08c2c-117">Explanation</span></span>  
 <span data-ttu-id="08c2c-118">一個或多個陳述式導致此查詢批次重新編譯至少 50 次。</span><span class="sxs-lookup"><span data-stu-id="08c2c-118">One or more statements caused the query batch to recompile at least 50 times.</span></span> <span data-ttu-id="08c2c-119">為了避免進一步重新編譯，您應該更正指定的陳述式。</span><span class="sxs-lookup"><span data-stu-id="08c2c-119">The specified statement should be corrected to avoid further recompilations.</span></span>  
  
 <span data-ttu-id="08c2c-120">下表列出重新編譯的原因。</span><span class="sxs-lookup"><span data-stu-id="08c2c-120">The following table lists the reasons for recompilation.</span></span>  
  
|<span data-ttu-id="08c2c-121">原因代碼</span><span class="sxs-lookup"><span data-stu-id="08c2c-121">Reason code</span></span>|<span data-ttu-id="08c2c-122">描述</span><span class="sxs-lookup"><span data-stu-id="08c2c-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="08c2c-123">1</span><span class="sxs-lookup"><span data-stu-id="08c2c-123">1</span></span>|<span data-ttu-id="08c2c-124">結構描述已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-124">Schema changed</span></span>|  
|<span data-ttu-id="08c2c-125">2</span><span class="sxs-lookup"><span data-stu-id="08c2c-125">2</span></span>|<span data-ttu-id="08c2c-126">統計資料已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-126">Statistics changed</span></span>|  
|<span data-ttu-id="08c2c-127">3</span><span class="sxs-lookup"><span data-stu-id="08c2c-127">3</span></span>|<span data-ttu-id="08c2c-128">延遲編譯</span><span class="sxs-lookup"><span data-stu-id="08c2c-128">Deferred compile</span></span>|  
|<span data-ttu-id="08c2c-129">4</span><span class="sxs-lookup"><span data-stu-id="08c2c-129">4</span></span>|<span data-ttu-id="08c2c-130">Set 選項已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-130">Set option changed</span></span>|  
|<span data-ttu-id="08c2c-131">5</span><span class="sxs-lookup"><span data-stu-id="08c2c-131">5</span></span>|<span data-ttu-id="08c2c-132">Temp 資料表已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-132">Temp table changed</span></span>|  
|<span data-ttu-id="08c2c-133">6</span><span class="sxs-lookup"><span data-stu-id="08c2c-133">6</span></span>|<span data-ttu-id="08c2c-134">遠端資料列集已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-134">Remote rowset changed</span></span>|  
|<span data-ttu-id="08c2c-135">7</span><span class="sxs-lookup"><span data-stu-id="08c2c-135">7</span></span>|<span data-ttu-id="08c2c-136">For Browse 權限已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-136">For Browse permissions changed</span></span>|  
|<span data-ttu-id="08c2c-137">8</span><span class="sxs-lookup"><span data-stu-id="08c2c-137">8</span></span>|<span data-ttu-id="08c2c-138">查詢通知環境已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-138">Query notification environment changed</span></span>|  
|<span data-ttu-id="08c2c-139">9</span><span class="sxs-lookup"><span data-stu-id="08c2c-139">9</span></span>|<span data-ttu-id="08c2c-140">分割區檢視已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-140">Partition view changed</span></span>|  
|<span data-ttu-id="08c2c-141">10</span><span class="sxs-lookup"><span data-stu-id="08c2c-141">10</span></span>|<span data-ttu-id="08c2c-142">資料指標選項已變更</span><span class="sxs-lookup"><span data-stu-id="08c2c-142">Cursor options changed</span></span>|  
|<span data-ttu-id="08c2c-143">11</span><span class="sxs-lookup"><span data-stu-id="08c2c-143">11</span></span>|<span data-ttu-id="08c2c-144">已要求選項 (重新編譯)</span><span class="sxs-lookup"><span data-stu-id="08c2c-144">Option (recompile) requested</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="08c2c-145">使用者動作</span><span class="sxs-lookup"><span data-stu-id="08c2c-145">User Action</span></span>  
  
1.  <span data-ttu-id="08c2c-146">您可以執行下列查詢來檢視導致重新編譯的陳述式。</span><span class="sxs-lookup"><span data-stu-id="08c2c-146">View the statement causing the recompilation by running the following query.</span></span> <span data-ttu-id="08c2c-147">請將 *sql_handle*、*starting_offset*、*ending_offset* 和 *plan_handle* 預留位置取代成錯誤訊息中指定的值。</span><span class="sxs-lookup"><span data-stu-id="08c2c-147">Replace the *sql_handle*, *starting_offset*, *ending_offset*, and *plan_handle* placeholders with the values specified in the error message.</span></span> <span data-ttu-id="08c2c-148">請注意，特定和準備 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的 **database_name** 和 **object_name** 資料行將成為 NULL。</span><span class="sxs-lookup"><span data-stu-id="08c2c-148">Note that the **database_name** and **object_name** columns will be NULL for ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="08c2c-149">SELECT DB_NAME(st.dbid) AS database_name</span><span class="sxs-lookup"><span data-stu-id="08c2c-149">SELECT DB_NAME(st.dbid) AS database_name</span></span>  
  
     <span data-ttu-id="08c2c-150">, OBJECT_NAME(st.objectid) AS object_name</span><span class="sxs-lookup"><span data-stu-id="08c2c-150">, OBJECT_NAME(st.objectid) AS object_name</span></span>  
  
     <span data-ttu-id="08c2c-151">, st.text</span><span class="sxs-lookup"><span data-stu-id="08c2c-151">, st.text</span></span>  
  
     <span data-ttu-id="08c2c-152">FROM sys.dm_exec_query_stats AS qs</span><span class="sxs-lookup"><span data-stu-id="08c2c-152">FROM sys.dm_exec_query_stats AS qs</span></span>  
  
     <span data-ttu-id="08c2c-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span><span class="sxs-lookup"><span data-stu-id="08c2c-153">CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st</span></span>  
  
     <span data-ttu-id="08c2c-154">WHERE qs.statement_start_offset = *starting_offset*</span><span class="sxs-lookup"><span data-stu-id="08c2c-154">WHERE qs.statement_start_offset = *starting_offset*</span></span>  
  
     <span data-ttu-id="08c2c-155">AND qs.statement_end_offset = *ending_offset*</span><span class="sxs-lookup"><span data-stu-id="08c2c-155">AND qs.statement_end_offset = *ending_offset*</span></span>  
  
     <span data-ttu-id="08c2c-156">AND qs.plan_handle = *plan_handle*;</span><span class="sxs-lookup"><span data-stu-id="08c2c-156">AND qs.plan_handle = *plan_handle*;</span></span>  
  
2.  <span data-ttu-id="08c2c-157">為了避免重新編譯，請根據原因代碼的說明，修改陳述式、批次或程序。</span><span class="sxs-lookup"><span data-stu-id="08c2c-157">Based on the reason code description, modify the statement, batch, or procedure to avoid recompilations.</span></span> <span data-ttu-id="08c2c-158">例如，一個預存程序可能會包含一個或多個 SET 陳述式。</span><span class="sxs-lookup"><span data-stu-id="08c2c-158">For example, a stored procedure may contain one or more SET statements.</span></span> <span data-ttu-id="08c2c-159">您應該從此程序中移除這些陳述式。</span><span class="sxs-lookup"><span data-stu-id="08c2c-159">These statements should be removed from the procedure.</span></span> <span data-ttu-id="08c2c-160">如需重新編譯原因和解決方案的其他範例，請參閱 [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10))(SQL Server 2005 中的批次編譯、重新編譯及計畫快取問題)。</span><span class="sxs-lookup"><span data-stu-id="08c2c-160">For additional examples of recompilation causes and resolutions, see [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).</span></span>  
  
3.  <span data-ttu-id="08c2c-161">如果持續發生問題，請連絡 Microsoft 客戶支援服務。</span><span class="sxs-lookup"><span data-stu-id="08c2c-161">If the problem persists, contact Microsoft Customer Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c2c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08c2c-162">See Also</span></span>  
 [<span data-ttu-id="08c2c-163">SQL:StmtRecompile 事件類別</span><span class="sxs-lookup"><span data-stu-id="08c2c-163">SQL:StmtRecompile Event Class</span></span>](../event-classes/sql-stmtrecompile-event-class.md)  
  
  
