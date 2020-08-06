---
title: 設定報表和共用資料集處理的逾時值 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c891b4911994ba2814a612439f141d16e4ad12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595632"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a><span data-ttu-id="faedc-102">設定報表和共用資料集處理的逾時值 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="faedc-102">Setting Time-out Values for Report and Shared Dataset Processing (SSRS)</span></span>
  <span data-ttu-id="faedc-103">您可以指定逾時值，以便設定系統資源的使用限制。</span><span class="sxs-lookup"><span data-stu-id="faedc-103">You can specify time-out values to set limits on how system resources are used.</span></span> <span data-ttu-id="faedc-104">報表伺服器支援兩種逾時值：</span><span class="sxs-lookup"><span data-stu-id="faedc-104">Report server supports two time-out values:</span></span>  
  
-   <span data-ttu-id="faedc-105">內嵌資料集查詢逾時值是報表伺服器等候資料庫回應的秒數。</span><span class="sxs-lookup"><span data-stu-id="faedc-105">An embedded dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="faedc-106">此值是在報表中定義的。</span><span class="sxs-lookup"><span data-stu-id="faedc-106">This value is defined in a report.</span></span>  
  
-   <span data-ttu-id="faedc-107">共用資料集查詢逾時值是報表伺服器等候資料庫回應的秒數。</span><span class="sxs-lookup"><span data-stu-id="faedc-107">A shared dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="faedc-108">此值是共用資料集定義的一部分，而且可以在報表伺服器上管理共用資料集時變更。</span><span class="sxs-lookup"><span data-stu-id="faedc-108">This value is part of the shared dataset definition and can be changed when you manage the shared dataset on the report server.</span></span>  
  
-   <span data-ttu-id="faedc-109">報表執行逾時值是報表處理在停止之前，可以繼續的秒數上限。</span><span class="sxs-lookup"><span data-stu-id="faedc-109">A report execution time-out value is the maximum number of seconds that report processing can continue before it is stopped.</span></span> <span data-ttu-id="faedc-110">此值是在系統層級定義的。</span><span class="sxs-lookup"><span data-stu-id="faedc-110">This value is defined at the system level.</span></span> <span data-ttu-id="faedc-111">您可以針對個別報表更改此設定。</span><span class="sxs-lookup"><span data-stu-id="faedc-111">You can vary this setting for individual reports.</span></span>  
  
 <span data-ttu-id="faedc-112">大部分的逾時錯誤會在查詢處理時發生。</span><span class="sxs-lookup"><span data-stu-id="faedc-112">Most time-out errors occur during query processing.</span></span> <span data-ttu-id="faedc-113">如果您遇到逾時錯誤，請試著增加查詢逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-113">If you are encountering time-out errors, try increasing the query time-out value.</span></span> <span data-ttu-id="faedc-114">請務必調整報表執行超時值，使其大於查詢超時。時間週期應足以完成查詢和報表處理。</span><span class="sxs-lookup"><span data-stu-id="faedc-114">Make sure to adjust the report execution time-out value so that it is larger than the query time-out. The time period should be sufficient to complete both query and report processing.</span></span>  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a><span data-ttu-id="faedc-115">設定報表中內嵌資料集的查詢逾時</span><span class="sxs-lookup"><span data-stu-id="faedc-115">Setting a Query Time-Out for an Embedded Dataset in a Report</span></span>  
 <span data-ttu-id="faedc-116">當您定義內嵌資料集時，可在報表撰寫期間指定查詢逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-116">Query time-out values are specified during report authoring when you define an embedded dataset.</span></span> <span data-ttu-id="faedc-117">逾時值會與報表一起儲存在報表定義的 `Timeout` 元素中。</span><span class="sxs-lookup"><span data-stu-id="faedc-117">The time-out value is stored with the report, in the `Timeout` element of the report definition.</span></span> <span data-ttu-id="faedc-118">依預設，此值設定為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="faedc-118">By default, this value is set to 30 seconds.</span></span> <span data-ttu-id="faedc-119">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="faedc-119">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="faedc-120">擁有權限修改已發行報表之屬性的使用者，可以編輯報表定義檔案，重設此值。</span><span class="sxs-lookup"><span data-stu-id="faedc-120">Users who have permission to modify the properties of a published report can reset this value by editing the report definition file.</span></span>  
  
 <span data-ttu-id="faedc-121">您也可以指定資料驅動訂閱的查詢逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-121">You can also specify a query time-out value for data-driven subscriptions.</span></span> <span data-ttu-id="faedc-122">查詢逾時值是在 [資料驅動訂閱] 頁面中指定的。</span><span class="sxs-lookup"><span data-stu-id="faedc-122">The query time-out value is specified in the Data-Driven Subscription pages.</span></span> <span data-ttu-id="faedc-123">您指定的值會決定報表伺服器從訂閱者資料來源擷取資料時，等候查詢處理完成的時間長度。</span><span class="sxs-lookup"><span data-stu-id="faedc-123">The value you specify determines how long the report server waits for query processing to complete when retrieving data from the subscriber data source.</span></span>  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a><span data-ttu-id="faedc-124">設定共用資料集的查詢逾時</span><span class="sxs-lookup"><span data-stu-id="faedc-124">Setting a Query Time-Out for a Shared Dataset</span></span>  
 <span data-ttu-id="faedc-125">當您建立或管理共用資料集時，可在報表伺服器上以秒數指定查詢逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-125">Query time-out values are specified in seconds on the report server when you create or manage a shared dataset.</span></span> <span data-ttu-id="faedc-126">根據預設，這個值是設定為 0 秒，相當於沒有逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-126">By default, this value is set to 0 seconds, which is the equivalent of no time-out value.</span></span> <span data-ttu-id="faedc-127">如需詳細資訊，請參閱 [Manage Shared Datasets](../report-data/manage-shared-datasets.md)(管理共用資料集)。</span><span class="sxs-lookup"><span data-stu-id="faedc-127">For more information, see [Manage Shared Datasets](../report-data/manage-shared-datasets.md).</span></span>  
  
## <a name="setting-a-report-execution-time-out"></a><span data-ttu-id="faedc-128">設定報表執行逾時</span><span class="sxs-lookup"><span data-stu-id="faedc-128">Setting a Report Execution Time-Out</span></span>  
 <span data-ttu-id="faedc-129">您可以設定報表執行逾時值，來限制報表伺服器用於處理報表的時間量。</span><span class="sxs-lookup"><span data-stu-id="faedc-129">You can set the report execution time-out value to limit the amount of time that a report server uses to process a report.</span></span> <span data-ttu-id="faedc-130">報表執行逾時值可以在報表管理員中指定。</span><span class="sxs-lookup"><span data-stu-id="faedc-130">Report execution time-out values can be specified in Report Manager.</span></span> <span data-ttu-id="faedc-131">您可以設定 [站台設定] 頁面中所有報表的預設值，然後覆寫特定報表在 [執行] 屬性頁面中的值。</span><span class="sxs-lookup"><span data-stu-id="faedc-131">You can set a default value for all reports in the Site Settings page, and then override that value in the Execution properties page for a specific report.</span></span> <span data-ttu-id="faedc-132">依預設，此值設定為 1800 秒。</span><span class="sxs-lookup"><span data-stu-id="faedc-132">By default, the value is set to 1800 seconds.</span></span> <span data-ttu-id="faedc-133">如需詳細資訊，請參閱 [設定報表處理屬性](set-report-processing-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="faedc-133">For more information, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span>  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a><span data-ttu-id="faedc-134">如何評估報表執行逾時值</span><span class="sxs-lookup"><span data-stu-id="faedc-134">How Report Execution Time-Out Values are Evaluated</span></span>  
 <span data-ttu-id="faedc-135">報表伺服器會以 60 秒的間隔評估執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="faedc-135">The report server evaluates running jobs at 60 second intervals.</span></span> <span data-ttu-id="faedc-136">每間隔 60 秒，報表伺服器會比較實際的處理時間和報表執行逾時值。</span><span class="sxs-lookup"><span data-stu-id="faedc-136">At each 60 second interval, the report server compares actual process time against the report execution time-out value.</span></span> <span data-ttu-id="faedc-137">如果報表的處理時間超過報表執行逾時值，就會停止報表的處理。</span><span class="sxs-lookup"><span data-stu-id="faedc-137">If the processing time for a report exceeds the report execution time-out value, report processing will stop.</span></span>  
  
 <span data-ttu-id="faedc-138">請注意，如果您指定少於 60 秒的逾時值，當報表伺服器還沒有評估執行中的作業之前，處理就已經在週期內開始和完成，則報表可能會完全執行。</span><span class="sxs-lookup"><span data-stu-id="faedc-138">Note that if you specify a time-out value that is smaller than 60 seconds, the report may execute in full if processing starts and completes during the quiet part of the cycle when the report server is not evaluating running jobs.</span></span> <span data-ttu-id="faedc-139">例如，如果您將報表的逾時值設定為 10 秒，而報表需要 20 秒執行，那麼如果報表在 60 秒週期的較早時刻就開始執行，報表就會完全處理。</span><span class="sxs-lookup"><span data-stu-id="faedc-139">For example, if you set a time-out value of 10 seconds for a report that takes 20 seconds to run, the report will process in full if report execution starts early in the 60 second cycle.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="faedc-140">您可以在 RSReportServer.config 檔案中設定 `RunningRequestsDbCycle` 設定，以變更評估執行中之作業的頻率。</span><span class="sxs-lookup"><span data-stu-id="faedc-140">You can set the `RunningRequestsDbCycle` setting in the RSReportServer.config file to change the frequency of how often running jobs are evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faedc-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faedc-141">See Also</span></span>  
 <span data-ttu-id="faedc-142">[以 SharePoint 整合模式 &#40;Reporting Services 設定處理選項&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="faedc-142">[Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="faedc-143">[Reporting Services 報表伺服器 &#40;原生模式&#41;](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="faedc-143">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="faedc-144">[管理執行中的進程](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="faedc-144">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="faedc-145">報表管理員 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="faedc-145">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
