---
title: 重新執行需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], replaying traces
- traces [SQL Server], replaying
- replaying traces
- TSQL_Replay template [SQL Server]
ms.assetid: 0e01dfc7-84b9-47f6-8bf7-b0656df4fa7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 65546f6820765286b558d2043e0155a79a07eb58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705734"
---
# <a name="replay-requirements"></a><span data-ttu-id="9669e-102">重新執行需求</span><span class="sxs-lookup"><span data-stu-id="9669e-102">Replay Requirements</span></span>
  <span data-ttu-id="9669e-103">若要使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 或分散式重新執行公用程式來重新執行追蹤資料，您必須在追蹤中擷取特定的事件類別和資料行集合。</span><span class="sxs-lookup"><span data-stu-id="9669e-103">In order to replay trace data with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or the Distributed Replay Utility, a specific set of event classes and columns must be captured in the trace.</span></span> <span data-ttu-id="9669e-104">如果 **TSQL_Replay** 追蹤範本用來設定之後用於重新執行的追蹤，預設將啟用這些設定。</span><span class="sxs-lookup"><span data-stu-id="9669e-104">These settings are enabled by default if the **TSQL_Replay** trace template is used to configure a trace that is later used for replay.</span></span> <span data-ttu-id="9669e-105">本主題會說明這些設定和其他重新執行需求。</span><span class="sxs-lookup"><span data-stu-id="9669e-105">This topic describes these settings and other replay requirements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9669e-106">我們建議您使用分散式重新執行公用程式來重新執行密集的 OLTP 應用程式 (具有許多使用中並行連接或高輸送量)。</span><span class="sxs-lookup"><span data-stu-id="9669e-106">We recommend using the Distributed Replay Utility for replaying an intensive OLTP application (with many active concurrent connections or high throughput).</span></span> <span data-ttu-id="9669e-107">分散式重新執行公用程式可以從多部電腦重新執行追蹤資料，並有效模擬關鍵任務的工作負載。</span><span class="sxs-lookup"><span data-stu-id="9669e-107">The Distributed Replay Utility can replay trace data from multiple computers, better simulating a mission-critical workload.</span></span> <span data-ttu-id="9669e-108">如需詳細資訊，請參閱 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="9669e-108">For more information, see [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md).</span></span>  
  
## <a name="event-classes-required-for-replay"></a><span data-ttu-id="9669e-109">重新執行所需的事件類別</span><span class="sxs-lookup"><span data-stu-id="9669e-109">Event Classes Required for Replay</span></span>  
 <span data-ttu-id="9669e-110">若要由 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]重新執行，除了您要監視的其他任何事件類別以外，還必須在追蹤中擷取下列事件類別集合：</span><span class="sxs-lookup"><span data-stu-id="9669e-110">To be replayed by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the following set of event classes, in addition to any other event classes you want to monitor, must be captured in the trace:</span></span>  
  
-   <span data-ttu-id="9669e-111">**CursorClose**(只有重新執行伺服端資料指標時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-111">**CursorClose (** only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="9669e-112">**CursorExecute** (只有重新執行伺服端資料指標時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-112">**CursorExecute** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="9669e-113">**CursorOpen** (只有重新執行伺服端資料指標時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-113">**CursorOpen** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="9669e-114">**CursorPrepare** (只有重新執行伺服端資料指標時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-114">**CursorPrepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="9669e-115">**CursorUnprepare** (只有重新執行伺服端資料指標時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-115">**CursorUnprepare** (only required when replaying server-side cursors)</span></span>  
  
-   <span data-ttu-id="9669e-116">**稽核登入**</span><span class="sxs-lookup"><span data-stu-id="9669e-116">**Audit Login**</span></span>  
  
-   <span data-ttu-id="9669e-117">**稽核登出**</span><span class="sxs-lookup"><span data-stu-id="9669e-117">**Audit Logout**</span></span>  
  
-   <span data-ttu-id="9669e-118">**ExistingConnection**</span><span class="sxs-lookup"><span data-stu-id="9669e-118">**ExistingConnection**</span></span>  
  
-   <span data-ttu-id="9669e-119">**RPC Output Parameter**</span><span class="sxs-lookup"><span data-stu-id="9669e-119">**RPC Output Parameter**</span></span>  
  
-   <span data-ttu-id="9669e-120">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="9669e-120">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="9669e-121">**RPC:Starting**</span><span class="sxs-lookup"><span data-stu-id="9669e-121">**RPC:Starting**</span></span>  
  
-   <span data-ttu-id="9669e-122">**Exec Prepared SQL** (只有重新執行伺服器端備妥的 SQL 陳述式時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-122">**Exec Prepared SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="9669e-123">**Prepare SQL** (只有重新執行伺服端備妥的 SQL 陳述式時才需要)</span><span class="sxs-lookup"><span data-stu-id="9669e-123">**Prepare SQL** (only required when replaying server-side prepared SQL statements)</span></span>  
  
-   <span data-ttu-id="9669e-124">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="9669e-124">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="9669e-125">**SQL:BatchStarting**</span><span class="sxs-lookup"><span data-stu-id="9669e-125">**SQL:BatchStarting**</span></span>  
  
## <a name="data-columns-required-for-replay"></a><span data-ttu-id="9669e-126">重新執行所需的資料行</span><span class="sxs-lookup"><span data-stu-id="9669e-126">Data Columns Required for Replay</span></span>  
 <span data-ttu-id="9669e-127">若要能夠重新執行追蹤，除了要擷取的其他任何資料行之外，還必須在追蹤中擷取以下資料行：</span><span class="sxs-lookup"><span data-stu-id="9669e-127">In addition to any other data columns you want to capture, the following data columns must be captured in a trace to allow the trace to be replayed:</span></span>  
  
-   <span data-ttu-id="9669e-128">**Event Class**</span><span class="sxs-lookup"><span data-stu-id="9669e-128">**Event Class**</span></span>  
  
-   <span data-ttu-id="9669e-129">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="9669e-129">**EventSequence**</span></span>  
  
-   <span data-ttu-id="9669e-130">**TextData**</span><span class="sxs-lookup"><span data-stu-id="9669e-130">**TextData**</span></span>  
  
-   <span data-ttu-id="9669e-131">**應用程式名稱**</span><span class="sxs-lookup"><span data-stu-id="9669e-131">**Application Name**</span></span>  
  
-   <span data-ttu-id="9669e-132">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="9669e-132">**LoginName**</span></span>  
  
-   <span data-ttu-id="9669e-133">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="9669e-133">**DatabaseName**</span></span>  
  
-   <span data-ttu-id="9669e-134">**資料庫識別碼**</span><span class="sxs-lookup"><span data-stu-id="9669e-134">**Database ID**</span></span>  
  
-   <span data-ttu-id="9669e-135">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="9669e-135">**ClientProcessID**</span></span>  
  
-   <span data-ttu-id="9669e-136">**HostName**</span><span class="sxs-lookup"><span data-stu-id="9669e-136">**HostName**</span></span>  
  
-   <span data-ttu-id="9669e-137">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="9669e-137">**ServerName**</span></span>  
  
-   <span data-ttu-id="9669e-138">**Binary Data**</span><span class="sxs-lookup"><span data-stu-id="9669e-138">**Binary Data**</span></span>  
  
-   <span data-ttu-id="9669e-139">**SPID**</span><span class="sxs-lookup"><span data-stu-id="9669e-139">**SPID**</span></span>  
  
-   <span data-ttu-id="9669e-140">**Start Time**</span><span class="sxs-lookup"><span data-stu-id="9669e-140">**Start Time**</span></span>  
  
-   <span data-ttu-id="9669e-141">**EndTime**</span><span class="sxs-lookup"><span data-stu-id="9669e-141">**EndTime**</span></span>  
  
-   <span data-ttu-id="9669e-142">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="9669e-142">**IsSystem**</span></span>  
  
-   <span data-ttu-id="9669e-143">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="9669e-143">**NTDomainName**</span></span>  
  
-   <span data-ttu-id="9669e-144">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="9669e-144">**NTUserName**</span></span>  
  
-   <span data-ttu-id="9669e-145">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="9669e-145">**Error**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9669e-146">對追蹤使用追蹤範本 **TSQL_Replay** ，擷取重新執行的資料。</span><span class="sxs-lookup"><span data-stu-id="9669e-146">Use the trace template **TSQL_Replay** for traces that capture data for replay.</span></span>  
  
## <a name="other-replay-requirements"></a><span data-ttu-id="9669e-147">其他重新執行需求</span><span class="sxs-lookup"><span data-stu-id="9669e-147">Other Replay Requirements</span></span>  
 <span data-ttu-id="9669e-148">在 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，重新執行會檢查出現的必要事件和資料行。</span><span class="sxs-lookup"><span data-stu-id="9669e-148">In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], replay checks for the presence of required events and columns.</span></span> <span data-ttu-id="9669e-149">這個變更可協助改善重新執行的精確度，而且當有必要資料遺失時，進行重新執行的疑難排解就不需要猜測。</span><span class="sxs-lookup"><span data-stu-id="9669e-149">This change helps improve the accuracy of replay and takes the guesswork out of troubleshooting replay when required data is missing.</span></span> <span data-ttu-id="9669e-150">當追蹤內遺失必要的資料時，重新執行會傳回一則錯誤，並停止重新執行該檔案。</span><span class="sxs-lookup"><span data-stu-id="9669e-150">Replay returns an error and stops replaying a file when required data is missing from a trace.</span></span>  
  
 <span data-ttu-id="9669e-151">若要在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的伺服器 (目標)，而非原始追蹤的伺服器 (來源) 重新執行追蹤，請確定已完成下列各項：</span><span class="sxs-lookup"><span data-stu-id="9669e-151">To replay a trace against a server (the target) on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running other than the server originally traced (the source), make sure the following has been done:</span></span>  
  
-   <span data-ttu-id="9669e-152">追蹤中包含的所有登入與使用者必須已在目標上建立，而且要與來源一樣在相同的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="9669e-152">All logins and users contained in the trace must be created already on the target and in the same database as the source.</span></span>  
  
-   <span data-ttu-id="9669e-153">目標中的所有登入與使用者，其權限必須與在來源中具有的權限相同。</span><span class="sxs-lookup"><span data-stu-id="9669e-153">All logins and users in the target must have the same permissions they had in the source.</span></span>  
  
-   <span data-ttu-id="9669e-154">所有登入密碼必須與執行重新執行的使用者之密碼一樣。</span><span class="sxs-lookup"><span data-stu-id="9669e-154">All login passwords must be the same as those of the user that executes the replay.</span></span>  
  
-   <span data-ttu-id="9669e-155">目標上的資料庫識別碼必須與來源上的一樣。</span><span class="sxs-lookup"><span data-stu-id="9669e-155">The database IDs on the target ideally should be the same as those on the source.</span></span> <span data-ttu-id="9669e-156">不過，如果不相同，若追蹤內有 **DatabaseName** 的話， 就可以據以執行比對作業。</span><span class="sxs-lookup"><span data-stu-id="9669e-156">However, if they are not the same, matching can be performed based on **DatabaseName** if it is present in the trace.</span></span>  
  
-   <span data-ttu-id="9669e-157">追蹤中包含之每個登入的預設資料庫必須設成 (在目標上) 登入的個別目標資料庫。</span><span class="sxs-lookup"><span data-stu-id="9669e-157">The default database for each login contained in the trace must be set (on the target) to the respective target database of the login.</span></span> <span data-ttu-id="9669e-158">例如，要重新執行的追蹤包含 **Fred**登入的活動，其位於來源的資料庫 **Fred_Db** 中。</span><span class="sxs-lookup"><span data-stu-id="9669e-158">For example, the trace to be replayed contains activity for the login, **Fred**, in the database **Fred_Db** on the source.</span></span> <span data-ttu-id="9669e-159">因此在目標上， **Fred**登入的預設資料庫必須設成符合 **Fred_Db** 的資料庫 (即使資料庫名稱不同亦然)。</span><span class="sxs-lookup"><span data-stu-id="9669e-159">Therefore, on the target, the default database for the login, **Fred**, must be set to the database that matches **Fred_Db** (even if the database name is different).</span></span> <span data-ttu-id="9669e-160">若要設定登入的預設資料庫，可使用 **sp_defaultdb** 系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="9669e-160">To set the default database of the login, use the **sp_defaultdb** system stored procedure.</span></span>  
  
 <span data-ttu-id="9669e-161">重新執行與找不到或不正確之登入相關的事件，會造成重新執行錯誤，但重新執行作業仍會繼續。</span><span class="sxs-lookup"><span data-stu-id="9669e-161">Replaying events associated with missing or incorrect logins results in replay errors, but the replay operation continues.</span></span>  
  
 <span data-ttu-id="9669e-162">如需有關重做追蹤時所需之權限的詳細資訊，請參閱＜ [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9669e-162">For information about what permissions are required to replay a trace, see [Permissions Required to Run SQL Server Profiler](sql-server-profiler.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9669e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9669e-163">See Also</span></span>  
 <span data-ttu-id="9669e-164">[重新執行追蹤資料表 &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9669e-164">[Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9669e-165">[重新執行追蹤檔案 &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9669e-165">[Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9669e-166">[SQL Server 事件類別參考](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9669e-166">[SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md) </span></span>  
 <span data-ttu-id="9669e-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9669e-167">[sp_defaultdb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) </span></span>  
 [<span data-ttu-id="9669e-168">SQL Server Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="9669e-168">SQL Server Distributed Replay</span></span>](../distributed-replay/sql-server-distributed-replay.md)  
  
  
