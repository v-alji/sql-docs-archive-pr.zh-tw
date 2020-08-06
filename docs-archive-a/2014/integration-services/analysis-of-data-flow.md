---
title: 資料流程的分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 184b53d3e982cd80d7c9c0909538a751585ae21d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593530"
---
# <a name="analysis-of-data-flow"></a><span data-ttu-id="e58a4-102">資料流程分析</span><span class="sxs-lookup"><span data-stu-id="e58a4-102">Analysis of Data Flow</span></span>
  <span data-ttu-id="e58a4-103">您可以使用 [ [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` 資料庫] 視圖來分析封裝的資料流程。</span><span class="sxs-lookup"><span data-stu-id="e58a4-103">You can use the [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md)`SSISDB` database view to analyze the data flow of packages.</span></span> <span data-ttu-id="e58a4-104">每當資料流程元件傳送資料至下游元件，此檢視就會顯示一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e58a4-104">This view displays a row each time a data flow component sends data to a downstream component.</span></span> <span data-ttu-id="e58a4-105">您可以使用這項資訊深入了解傳送至每個元件的資料列。</span><span class="sxs-lookup"><span data-stu-id="e58a4-105">The information can be used to gain a deeper understanding of the rows that are sent to each component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e58a4-106">您必須將記錄層次設定為 [詳細資訊]  ，以透過 catalog.execution_data_statistics 檢視來擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="e58a4-106">The logging level must be set to **Verbose** in order to capture information with the catalog.execution_data_statistics view.</span></span>  
  
 <span data-ttu-id="e58a4-107">下列範例顯示在封裝元件之間傳送的資料列數。</span><span class="sxs-lookup"><span data-stu-id="e58a4-107">The following example displays the number of rows sent between components of a package.</span></span>  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 <span data-ttu-id="e58a4-108">下列範例計算針對特定執行，每個元件每毫秒所傳送的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="e58a4-108">The following example calculates the number of rows per millisecond sent by each component for a specific execution.</span></span> <span data-ttu-id="e58a4-109">計算值包括：</span><span class="sxs-lookup"><span data-stu-id="e58a4-109">The calculated values are:</span></span>  
  
-   <span data-ttu-id="e58a4-110">**total_rows** - 元件傳送的所有資料列總和</span><span class="sxs-lookup"><span data-stu-id="e58a4-110">**total_rows** - the sum of all the rows sent by the component</span></span>  
  
-   <span data-ttu-id="e58a4-111">**wall_clock_time_ms** - 每個元件經過的執行時間總計 (以毫秒為單位)</span><span class="sxs-lookup"><span data-stu-id="e58a4-111">**wall_clock_time_ms** - the total elapsed execution time, in milliseconds, for each component</span></span>  
  
-   <span data-ttu-id="e58a4-112">**num_rows_per_millisecond** - 每個元件每毫秒傳送的資料列數</span><span class="sxs-lookup"><span data-stu-id="e58a4-112">**num_rows_per_millisecond** - the number of rows per millisecond sent by each component</span></span>  
  
 <span data-ttu-id="e58a4-113">`HAVING`子句是用來防止計算中發生零除的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e58a4-113">The `HAVING` clause is used to prevent a divide-by-zero error in the calculations.</span></span>  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a><span data-ttu-id="e58a4-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="e58a4-114">Related Tasks</span></span>  
 [<span data-ttu-id="e58a4-115">偵錯資料流程</span><span class="sxs-lookup"><span data-stu-id="e58a4-115">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
 [<span data-ttu-id="e58a4-116">套件執行的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="e58a4-116">Troubleshooting Tools for Package Execution</span></span>](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a><span data-ttu-id="e58a4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58a4-117">See Also</span></span>  
 [<span data-ttu-id="e58a4-118">資料流程中的資料</span><span class="sxs-lookup"><span data-stu-id="e58a4-118">Data in Data Flows</span></span>](data-flow/data-in-data-flows.md)  
  
  
