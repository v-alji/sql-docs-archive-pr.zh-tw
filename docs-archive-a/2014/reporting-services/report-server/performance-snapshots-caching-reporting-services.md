---
title: 效能、快照集、快取 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f171586e136b36bd694fa40b15272f62e1cb1378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700804"
---
# <a name="performance-snapshots-caching-reporting-services"></a><span data-ttu-id="65ee5-102">效能、快照、快取 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="65ee5-102">Performance, Snapshots, Caching (Reporting Services)</span></span>
  <span data-ttu-id="65ee5-103">報表伺服器的效能會受到一些因素組合的影響，包括硬體、存取報表的並行使用者數目、報表中的資料量，以及輸出格式。</span><span class="sxs-lookup"><span data-stu-id="65ee5-103">Report server performance is affected by a combination of factors that include hardware, number of concurrent users accessing reports, the amount of data in a report, and output format.</span></span> <span data-ttu-id="65ee5-104">若要了解安裝特有的效能因素以及哪些補救措施可產生所需的結果，您必須取得基準資料並執行測試。</span><span class="sxs-lookup"><span data-stu-id="65ee5-104">To understand the performance factors that are specific to your installation and which remedies will produce the results you want, you will need to get baseline data and run tests.</span></span> <span data-ttu-id="65ee5-105">如需有關工具和指導方針的詳細資訊，請參閱下列 MSDN 出版品：＜ [Reporting Services 效能最佳化](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) ＞和＜ [在 SQL Server 2005 Reporting Services 報表伺服器上使用 Visual Studio 2005 執行負載測試](https://go.microsoft.com/fwlink/?LinkID=77519)＞。</span><span class="sxs-lookup"><span data-stu-id="65ee5-105">For more information about tools and guidelines, see the following publications on MSDN: [Reporting Services Performance Optimization](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) and [Using Visual Studio 2005 to Perform Load Testing on a SQL Server 2005 Reporting Services Report Server](https://go.microsoft.com/fwlink/?LinkID=77519).</span></span>  
  
 <span data-ttu-id="65ee5-106">要考慮的一般原則包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="65ee5-106">General principles to consider include the following:</span></span>  
  
-   <span data-ttu-id="65ee5-107">報表處理和轉譯是需要大量記憶體的作業。</span><span class="sxs-lookup"><span data-stu-id="65ee5-107">Report processing and rendering are memory intensive operations.</span></span> <span data-ttu-id="65ee5-108">可能的話，請選擇具有大量記憶的電腦。</span><span class="sxs-lookup"><span data-stu-id="65ee5-108">When possible, choose a computer that has a lot of memory.</span></span>  
  
-   <span data-ttu-id="65ee5-109">在個別的電腦上主控報表伺服器與報表伺服器資料庫會比在單一高階電腦上主控這兩個項目提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="65ee5-109">Hosting the report server and the report server database on separate computers tends to provide better performance than hosting both on a single high-end computer.</span></span>  
  
-   <span data-ttu-id="65ee5-110">如果所有報表的處理速度都很慢，請考慮採用向外延展部署，以便讓多個報表伺服器執行個體支援單一報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="65ee5-110">If all reports are processing slowly, consider a scale-out deployment where multiple report server instances support a single report server database.</span></span> <span data-ttu-id="65ee5-111">為了獲得最佳結果，請使用負載平衡軟體，將要求平均分散到部署中。</span><span class="sxs-lookup"><span data-stu-id="65ee5-111">For best results, use load balancing software to distribute requests evenly across the deployment.</span></span>  
  
-   <span data-ttu-id="65ee5-112">如果單一報表的處理速度很慢，而且該報表必須視需要執行，請調整報表資料集查詢。</span><span class="sxs-lookup"><span data-stu-id="65ee5-112">If a single report is processing slowly, tune report dataset queries if the report must run on demand.</span></span> <span data-ttu-id="65ee5-113">您也可以考慮使用您可以快取的共用資料集、快取報表，或將報表當做快照集執行。</span><span class="sxs-lookup"><span data-stu-id="65ee5-113">You might also consider using shared datasets that you can cache, caching the report, or running the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="65ee5-114">如果採用特定格式之所有報表的處理速度很慢 (例如，轉譯成 PDF 時)，請考慮採用檔案共用傳遞、加入更多記憶體，或選擇不同的格式。</span><span class="sxs-lookup"><span data-stu-id="65ee5-114">If all reports process slowly in a specific format (for example, while rendering to PDF), consider file share delivery, adding more memory, or choosing a different format.</span></span>  
  
-   <span data-ttu-id="65ee5-115">若要了解處理某份報表和其他使用標準需要多久，請檢閱報表伺服器執行記錄。</span><span class="sxs-lookup"><span data-stu-id="65ee5-115">To find out how long it takes to process a report and other usage metrics, review the report server execution log.</span></span> <span data-ttu-id="65ee5-116">如需詳細資訊，請參閱[報表伺服器執行記錄和 ExecutionLog3 View](report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="65ee5-116">For more information, see [Report Server Execution Log and the ExecutionLog3 View](report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
-   <span data-ttu-id="65ee5-117">如需有關如何透過微調記憶體管理組態設定來減少效能問題的詳細資訊，請參閱 [設定報表伺服器應用程式的可用記憶體](../report-server/configure-available-memory-for-report-server-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="65ee5-117">For more information about how to mitigate performance issues by tuning memory management configuration settings, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65ee5-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="65ee5-118">In This Section</span></span>  
 [<span data-ttu-id="65ee5-119">監視報表伺服器效能</span><span class="sxs-lookup"><span data-stu-id="65ee5-119">Monitoring Report Server Performance</span></span>](monitoring-report-server-performance.md)  
 <span data-ttu-id="65ee5-120">描述您可以用來追蹤伺服器之處理負載的效能物件。</span><span class="sxs-lookup"><span data-stu-id="65ee5-120">Describes the performance objects you can use to track the processing load on your server.</span></span>  
  
 [<span data-ttu-id="65ee5-121">設定報表處理屬性</span><span class="sxs-lookup"><span data-stu-id="65ee5-121">Set Report Processing Properties</span></span>](set-report-processing-properties.md)  
 <span data-ttu-id="65ee5-122">描述將報表設定為視需要執行、從快取執行或依據排程當成報表快照集執行的方式。</span><span class="sxs-lookup"><span data-stu-id="65ee5-122">Describes ways of configuring a report to run on demand, from cache, or on a schedule as a report snapshot.</span></span>  
  
 [<span data-ttu-id="65ee5-123">設定報表伺服器應用程式的可用記憶體</span><span class="sxs-lookup"><span data-stu-id="65ee5-123">Configure Available Memory for Report Server Applications</span></span>](../report-server/configure-available-memory-for-report-server-applications.md)  
 <span data-ttu-id="65ee5-124">描述如何覆寫預設記憶體管理行為。</span><span class="sxs-lookup"><span data-stu-id="65ee5-124">Describes how you can override default memory management behavior.</span></span>  
  
 [<span data-ttu-id="65ee5-125">快取報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65ee5-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
 <span data-ttu-id="65ee5-126">描述報表伺服器上的報表快取行為。</span><span class="sxs-lookup"><span data-stu-id="65ee5-126">Describes report caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="65ee5-127">快取共用資料集 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65ee5-127">Cache Shared Datasets &#40;SSRS&#41;</span></span>](cache-shared-datasets-ssrs.md)  
 <span data-ttu-id="65ee5-128">描述報表伺服器上的共用資料集快取行為。</span><span class="sxs-lookup"><span data-stu-id="65ee5-128">Describes shared dataset caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="65ee5-129">處理大型報表</span><span class="sxs-lookup"><span data-stu-id="65ee5-129">Process Large Reports</span></span>](process-large-reports.md)  
 <span data-ttu-id="65ee5-130">提供如何設定和散發大型報表的建議。</span><span class="sxs-lookup"><span data-stu-id="65ee5-130">Provides recommendations on how to configure and distribute a large report.</span></span>  
  
 [<span data-ttu-id="65ee5-131">設定報表和共用資料集處理的逾時值 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="65ee5-131">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 <span data-ttu-id="65ee5-132">說明如何設定查詢和報表處理的逾時。</span><span class="sxs-lookup"><span data-stu-id="65ee5-132">Explains how to set time outs on query and report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ee5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65ee5-133">See Also</span></span>  
 <span data-ttu-id="65ee5-134">[管理執行中的處理序](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="65ee5-134">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="65ee5-135">驗證報表執行</span><span class="sxs-lookup"><span data-stu-id="65ee5-135">Verifying a Report Run</span></span>](verifying-a-report-run.md)  
  
  
