---
title: 效能的監視與微調 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- instances of SQL Server, monitoring performance
- monitoring server performance [SQL Server]
- Database Engine [SQL Server], performance
- monitoring performance [SQL Server], about performance
- server performance [SQL Server]
- monitoring performance [SQL Server]
- database performance [SQL Server], about performance
- tuning databases [SQL Server], about performance
- status information [SQL Server], performance monitoring
- database monitoring [SQL Server], about performance
- monitoring [SQL Server], queries performance
- server performance [SQL Server], about performance
- tuning databases [SQL Server]
- database performance [SQL Server]
- monitoring [SQL Server], server performance
- database monitoring [SQL Server]
- monitoring server performance [SQL Server], about monitoring server performance
ms.assetid: 87f23f03-0f19-4b2e-bfae-efa378f7a0d4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe07bdf01df6c4b61a64c6ee78de313a21d62f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594022"
---
# <a name="monitor-and-tune-for-performance"></a><span data-ttu-id="4b521-102">效能的監視與微調</span><span class="sxs-lookup"><span data-stu-id="4b521-102">Monitor and Tune for Performance</span></span>
  <span data-ttu-id="4b521-103">監視資料庫的目標在於評估伺服器的執行效能。</span><span class="sxs-lookup"><span data-stu-id="4b521-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="4b521-104">有效的監視包括定期建立目前效能的快照集以隔離造成問題的處理序，以及持續蒐集資料來追蹤效能趨勢。</span><span class="sxs-lookup"><span data-stu-id="4b521-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span>  
  
 <span data-ttu-id="4b521-105">持續進行的資料庫效能評估可協助您將回應時間降到最低並產生最大產能，以達最佳效能。</span><span class="sxs-lookup"><span data-stu-id="4b521-105">Ongoing evaluation of the database performance helps you minimize response times and maximize throughput, yielding optimal performance.</span></span> <span data-ttu-id="4b521-106">有效率的網路流量、磁碟 I/O 與 CPU 使用量是達到最佳效能的關鍵。</span><span class="sxs-lookup"><span data-stu-id="4b521-106">Efficient network traffic, disk I/O, and CPU usage are key to peak performance.</span></span> <span data-ttu-id="4b521-107">您必須徹底分析應用程式需求、了解資料的邏輯與實體結構、評估資料庫使用，以及商議使用衝突的折衷方案，如線上交易處理 (Online Transaction Processing，OLTP) 之於決策支援。</span><span class="sxs-lookup"><span data-stu-id="4b521-107">You need to thoroughly analyze the application requirements, understand the logical and physical structure of the data, assess database usage, and negotiate tradeoffs between conflicting uses such as online transaction processing (OLTP) versus decision support.</span></span>  
  
## <a name="benefits-of-monitoring-and-tuning-databases-for-performance"></a><span data-ttu-id="4b521-108">監視和微調資料庫效能的優點</span><span class="sxs-lookup"><span data-stu-id="4b521-108">Benefits of Monitoring and Tuning Databases for Performance</span></span>  
 <span data-ttu-id="4b521-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Microsoft Windows 作業系統提供公用程式，可讓您檢視資料庫的目前狀況，並隨著狀況變更來追蹤效能。</span><span class="sxs-lookup"><span data-stu-id="4b521-109">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the Microsoft Windows operating system provide utilities that allow you to view the current condition of the database and to track performance as conditions change.</span></span> <span data-ttu-id="4b521-110">有各種工具和技巧可以用來監視 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4b521-110">There are a variety of tools and techniques that can be used to monitor [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4b521-111">了解如何監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可協助您：</span><span class="sxs-lookup"><span data-stu-id="4b521-111">Understanding how to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can help you:</span></span>  
  
-   <span data-ttu-id="4b521-112">判斷是否可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="4b521-112">Determine whether you can improve performance.</span></span> <span data-ttu-id="4b521-113">例如，監視常用查詢的回應時間，您可以判斷是否需要變更資料表的查詢或索引。</span><span class="sxs-lookup"><span data-stu-id="4b521-113">For example, by monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables are required.</span></span>  
  
-   <span data-ttu-id="4b521-114">評估使用者活動。</span><span class="sxs-lookup"><span data-stu-id="4b521-114">Evaluate user activity.</span></span> <span data-ttu-id="4b521-115">例如，藉由監視嘗試連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的使用者，您可以判斷安全性是否設定適當，並測試應用程式和開發系統。</span><span class="sxs-lookup"><span data-stu-id="4b521-115">For example, by monitoring users trying to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span> <span data-ttu-id="4b521-116">例如，藉由監視執行中的 SQL 查詢，您可以判斷查詢是否撰寫正確並產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="4b521-116">For example, by monitoring SQL queries as they are executed, you can determine whether they are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="4b521-117">對問題進行疑難排解或對應用程式元件進行偵錯，例如預存程序。</span><span class="sxs-lookup"><span data-stu-id="4b521-117">Troubleshoot any problems or debug application components, such as stored procedures.</span></span>  
  
### <a name="monitoring-in-a-dynamic-environment"></a><span data-ttu-id="4b521-118">動態環境中的監視</span><span class="sxs-lookup"><span data-stu-id="4b521-118">Monitoring in a Dynamic Environment</span></span>  
 <span data-ttu-id="4b521-119">因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是在動態環境下提供服務，所以監視很重要。</span><span class="sxs-lookup"><span data-stu-id="4b521-119">Monitoring is important because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a service in a dynamic environment.</span></span> <span data-ttu-id="4b521-120">變更條件會導致效能變更。</span><span class="sxs-lookup"><span data-stu-id="4b521-120">Changing conditions result in changing performance.</span></span> <span data-ttu-id="4b521-121">評估過程中，當使用者數目增加、使用者存取與連接方式變更、資料庫內容成長、用戶端應用程式變更、應用程式中的資料變更、查詢變得更複雜，以及網路流量提高時，效能也會跟著變更。</span><span class="sxs-lookup"><span data-stu-id="4b521-121">In your evaluations, you can see performance changes as the number of users increases, user access and connection methods change, database contents grow, client applications change, data in the applications changes, queries become more complex, and network traffic rises.</span></span> <span data-ttu-id="4b521-122">藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具來監視效能， 您可以找出條件變更或複雜查詢與某些效能變更之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="4b521-122">By using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools to monitor performance, you can associate some changes in performance with changing conditions and complex queries.</span></span> <span data-ttu-id="4b521-123">下列案例提供了範例：</span><span class="sxs-lookup"><span data-stu-id="4b521-123">The following scenarios provide examples:</span></span>  
  
-   <span data-ttu-id="4b521-124">藉由監視常用查詢的回應時間，您可以判斷是否需要變更執行查詢之資料表的查詢或索引。</span><span class="sxs-lookup"><span data-stu-id="4b521-124">By monitoring the response times for frequently used queries, you can determine whether changes to the query or indexes on the tables where the queries execute are required.</span></span>  
  
-   <span data-ttu-id="4b521-125">藉由監視執行中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，您可以判斷查詢是否撰寫正確並產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="4b521-125">By monitoring [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as they are executed, you can determine whether the queries are written correctly and producing the expected results.</span></span>  
  
-   <span data-ttu-id="4b521-126">藉由監視嘗試連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的使用者，您可以判斷安全性是否適當地設定，並對應用程式或開發系統進行測試。</span><span class="sxs-lookup"><span data-stu-id="4b521-126">By monitoring users that try to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can determine whether security is set up adequately and test applications or development systems.</span></span>  
  
 <span data-ttu-id="4b521-127">回應時間就是將結果集的第一個資料列傳回給使用者所需的時間長度，以視覺化確認的形式表示查詢已經過處理了。</span><span class="sxs-lookup"><span data-stu-id="4b521-127">Response time is the length of time required for the first row of the result set to be returned to the user in the form of visual confirmation that a query is being processed.</span></span> <span data-ttu-id="4b521-128">輸送量是指在指定的期間內，伺服器所處理的查詢總數。</span><span class="sxs-lookup"><span data-stu-id="4b521-128">Throughput is the total number of queries handled by the server during a specified period of time.</span></span>  
  
 <span data-ttu-id="4b521-129">隨著使用者數目的增加，伺服器資源的爭奪現象也會隨之增加，連帶使回應時間增加，整體輸送量降低。</span><span class="sxs-lookup"><span data-stu-id="4b521-129">As the number of users increases, so does the competition for a server's resources, which in turn increases response time and decreases overall throughput.</span></span>  
  
## <a name="monitoring-and-tuning-performance-tasks"></a><span data-ttu-id="4b521-130">監視和微調效能工作</span><span class="sxs-lookup"><span data-stu-id="4b521-130">Monitoring and Tuning Performance Tasks</span></span>  
  
|<span data-ttu-id="4b521-131">工作描述</span><span class="sxs-lookup"><span data-stu-id="4b521-131">Task Description</span></span>|<span data-ttu-id="4b521-132">主題</span><span class="sxs-lookup"><span data-stu-id="4b521-132">Topic</span></span>|  
|----------------------|-----------|  
|[<span data-ttu-id="4b521-133">監視 SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="4b521-133">Monitor SQL Server Components</span></span>](monitor-sql-server-components.md)|<span data-ttu-id="4b521-134">提供有效地監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之任何元件所需的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="4b521-134">Provides the necessary steps required to effectively monitor any component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4b521-135">效能監視及微調工具</span><span class="sxs-lookup"><span data-stu-id="4b521-135">Performance Monitoring and Tuning Tools</span></span>](performance-monitoring-and-tuning-tools.md)|<span data-ttu-id="4b521-136">列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監視和微調工具。</span><span class="sxs-lookup"><span data-stu-id="4b521-136">Lists the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] monitoring and tuning tools.</span></span>|  
|[<span data-ttu-id="4b521-137">建立效能基準</span><span class="sxs-lookup"><span data-stu-id="4b521-137">Establish a Performance Baseline</span></span>](establish-a-performance-baseline.md)|<span data-ttu-id="4b521-138">提供有關如何建立效能比較基準的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b521-138">Provides information about how to establish a performance baseline.</span></span>|  
|[<span data-ttu-id="4b521-139">隔離效能問題</span><span class="sxs-lookup"><span data-stu-id="4b521-139">Isolate Performance Problems</span></span>](isolate-performance-problems.md)|<span data-ttu-id="4b521-140">描述如何隔離資料庫效能問題。</span><span class="sxs-lookup"><span data-stu-id="4b521-140">Describes how to isolate database performance problems.</span></span>|  
|[<span data-ttu-id="4b521-141">找出瓶頸</span><span class="sxs-lookup"><span data-stu-id="4b521-141">Identify Bottlenecks</span></span>](identify-bottlenecks.md)|<span data-ttu-id="4b521-142">描述如何監視和追蹤伺服器效能，以找出瓶頸。</span><span class="sxs-lookup"><span data-stu-id="4b521-142">Describes how to monitor and track server performance to identify bottlenecks.</span></span>|  
|[<span data-ttu-id="4b521-143">伺服器效能與活動監視</span><span class="sxs-lookup"><span data-stu-id="4b521-143">Server Performance and Activity Monitoring</span></span>](server-performance-and-activity-monitoring.md)|<span data-ttu-id="4b521-144">描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 效能和活動監視工具。</span><span class="sxs-lookup"><span data-stu-id="4b521-144">Describes how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span>|  
|[<span data-ttu-id="4b521-145">顯示並儲存執行計畫</span><span class="sxs-lookup"><span data-stu-id="4b521-145">Display and Save Execution Plans</span></span>](display-and-save-execution-plans.md)|<span data-ttu-id="4b521-146">描述如何顯示執行計畫，以及如何將執行計畫儲存至 XML 格式的檔案。</span><span class="sxs-lookup"><span data-stu-id="4b521-146">Describes how to display and save execution plans to a file in XML format.</span></span>|  
|[<span data-ttu-id="4b521-147">使用查詢存放區監視效能</span><span class="sxs-lookup"><span data-stu-id="4b521-147">Monitoring Performance By Using the Query Store</span></span>](monitoring-performance-by-using-the-query-store.md)|<span data-ttu-id="4b521-148">查詢存放區會自動擷取查詢、計劃和執行階段統計資料的歷程記錄，並加以保留供您檢閱。</span><span class="sxs-lookup"><span data-stu-id="4b521-148">The Query Store automatically captures a history of queries, plans, and runtime statistics, and retains these for your review.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b521-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b521-149">See Also</span></span>  
 <span data-ttu-id="4b521-150">[將整個企業的管理自動化](../../ssms/agent/automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="4b521-150">[Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="4b521-151">[Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="4b521-151">[Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="4b521-152">[監視資源使用量 &#40;系統監視器&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="4b521-152">[Monitor Resource Usage &#40;System Monitor&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 [<span data-ttu-id="4b521-153">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="4b521-153">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
