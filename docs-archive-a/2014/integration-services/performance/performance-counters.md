---
title: 效能計數器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], performance counters
- performance counters [Integration Services]
- data flow [Integration Services], performance
- counters [Integration Services]
- data flow engine [Integration Services]
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b20ac056894066114883153030943bec1c05963
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595161"
---
# <a name="performance-counters"></a><span data-ttu-id="d3d9f-102">效能計數器</span><span class="sxs-lookup"><span data-stu-id="d3d9f-102">Performance Counters</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="d3d9f-103">會安裝一組您可以用於監視資料流程引擎效能的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-103">installs a set of performance counters that you can use to monitor the performance of the data flow engine.</span></span> <span data-ttu-id="d3d9f-104">例如,，您可以監看 "Buffers spooled" 計數器以判斷是否要在封裝執行時，暫時將資料緩衝區寫入到磁碟中。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-104">For example, you can watch the "Buffers spooled" counter to determine whether data buffers are being written to disk temporarily while a package is running.</span></span> <span data-ttu-id="d3d9f-105">這種交換會降低效能，並指出電腦的記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-105">This swapping reduces performance and indicates that the computer has insufficient memory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3d9f-106">：如果您在執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的電腦上安裝 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]，然後將該電腦升級到 [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]，則升級程序會從電腦中移除 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-106">If you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="d3d9f-107">若要還原電腦上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 效能計數器，請在修復模式中執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-107">To restore the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
 <span data-ttu-id="d3d9f-108">下表描述這些效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-108">The following table describes the performance counters.</span></span>  
  
|<span data-ttu-id="d3d9f-109">效能計數器</span><span class="sxs-lookup"><span data-stu-id="d3d9f-109">Performance counter</span></span>|<span data-ttu-id="d3d9f-110">描述</span><span class="sxs-lookup"><span data-stu-id="d3d9f-110">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="d3d9f-111">BLOB bytes read</span><span class="sxs-lookup"><span data-stu-id="d3d9f-111">BLOB bytes read</span></span>|<span data-ttu-id="d3d9f-112">資料流程引擎已從所有來源讀取之二進位大型物件 (BLOB) 資料的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-112">The number of bytes of binary large object (BLOB) data that the data flow engine has read from all sources.</span></span>|  
|<span data-ttu-id="d3d9f-113">BLOB bytes written</span><span class="sxs-lookup"><span data-stu-id="d3d9f-113">BLOB bytes written</span></span>|<span data-ttu-id="d3d9f-114">資料流程引擎已寫入所有目的地之 BLOB 資料的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-114">The number of bytes of BLOB data that the data flow engine has written to all destinations.</span></span>|  
|<span data-ttu-id="d3d9f-115">BLOB files in use</span><span class="sxs-lookup"><span data-stu-id="d3d9f-115">BLOB files in use</span></span>|<span data-ttu-id="d3d9f-116">資料流程引擎目前用於多工緩衝處理的 BLOB 檔案數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-116">The number of BLOB files that the data flow engine currently is using for spooling.</span></span>|  
|<span data-ttu-id="d3d9f-117">Buffer memory</span><span class="sxs-lookup"><span data-stu-id="d3d9f-117">Buffer memory</span></span>|<span data-ttu-id="d3d9f-118">使用中的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-118">The amount of memory that is in use.</span></span> <span data-ttu-id="d3d9f-119">這可能同時包括實體和虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-119">This may include both physical and virtual memory.</span></span> <span data-ttu-id="d3d9f-120">當這個數目大於實體記憶體的數量時， **Buffers Spooled** 計數會提高，這表示記憶體交換正在增加。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-120">When this number is larger than the amount of physical memory, the **Buffers Spooled** count rises as an indication that memory swapping is increasing.</span></span> <span data-ttu-id="d3d9f-121">增加的記憶體交換會降低資料流程引擎的效能。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-121">Increased memory swapping slows performance of the data flow engine.</span></span>|  
|<span data-ttu-id="d3d9f-122">Buffers in use</span><span class="sxs-lookup"><span data-stu-id="d3d9f-122">Buffers in use</span></span>|<span data-ttu-id="d3d9f-123">所有資料流程元件及資料流程引擎目前正在使用之所有類型的緩衝區物件數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-123">The number of buffer objects, of all types, that all data flow components and the data flow engine is currently using.</span></span>|  
|<span data-ttu-id="d3d9f-124">Buffers Spooled</span><span class="sxs-lookup"><span data-stu-id="d3d9f-124">Buffers spooled</span></span>|<span data-ttu-id="d3d9f-125">目前已寫入磁碟的緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-125">The number of buffers currently written to the disk.</span></span> <span data-ttu-id="d3d9f-126">如果資料流程引擎執行所用的實體記憶體偏低，則會將目前未使用的緩衝區寫入磁碟，然後在需要時重新載入。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-126">If the data flow engine runs low on physical memory, buffers not currently used are written to disk and then reloaded when needed.</span></span>|  
|<span data-ttu-id="d3d9f-127">Flat buffer memory</span><span class="sxs-lookup"><span data-stu-id="d3d9f-127">Flat buffer memory</span></span>|<span data-ttu-id="d3d9f-128">所有一般緩衝區使用的記憶體總數 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-128">The total amount of memory, in bytes, that all flat buffers use.</span></span> <span data-ttu-id="d3d9f-129">一般緩衝區是元件用以儲存資料的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-129">Flat buffers are blocks of memory that a component uses to store data.</span></span> <span data-ttu-id="d3d9f-130">一般緩衝區是按位元組逐個存取的大型位元組區塊。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-130">A flat buffer is a large block of bytes that is accessed byte by byte.</span></span>|  
|<span data-ttu-id="d3d9f-131">Flat buffers in use</span><span class="sxs-lookup"><span data-stu-id="d3d9f-131">Flat buffers in use</span></span>|<span data-ttu-id="d3d9f-132">資料流程引擎所使用的一般緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-132">The number of flat buffers that the Data flow engine uses.</span></span> <span data-ttu-id="d3d9f-133">所有一般緩衝區都是私用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-133">All flat buffers are private buffers.</span></span>|  
|<span data-ttu-id="d3d9f-134">Private buffer memory</span><span class="sxs-lookup"><span data-stu-id="d3d9f-134">Private buffer memory</span></span>|<span data-ttu-id="d3d9f-135">所有私用緩衝區使用中的記憶體總數。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-135">The total amount of memory in use by all private buffers.</span></span> <span data-ttu-id="d3d9f-136">如果資料流程引擎建立緩衝區以支援資料流程，則該緩衝區就不是私用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-136">A buffer is not private if the data flow engine creates it to support data flow.</span></span> <span data-ttu-id="d3d9f-137">私用緩衝區是轉換只將其用於暫存工作的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-137">A private buffer is a buffer that a transformation uses for temporary work only.</span></span> <span data-ttu-id="d3d9f-138">例如，「彙總」轉換使用私用緩衝區執行其工作。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-138">For example, the Aggregation transformation uses private buffers to do its work.</span></span>|  
|<span data-ttu-id="d3d9f-139">Private buffers in use</span><span class="sxs-lookup"><span data-stu-id="d3d9f-139">Private buffers in use</span></span>|<span data-ttu-id="d3d9f-140">轉換所使用的緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-140">The number of buffers that transformations use.</span></span>|  
|<span data-ttu-id="d3d9f-141">Rows read</span><span class="sxs-lookup"><span data-stu-id="d3d9f-141">Rows read</span></span>|<span data-ttu-id="d3d9f-142">來源產生的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-142">The number of rows that a source produces.</span></span> <span data-ttu-id="d3d9f-143">該數目不包括「查閱」轉換從參考資料表讀取的資料列。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-143">The number does not include rows read from reference tables by the Lookup transformation.</span></span>|  
|<span data-ttu-id="d3d9f-144">Rows written</span><span class="sxs-lookup"><span data-stu-id="d3d9f-144">Rows written</span></span>|<span data-ttu-id="d3d9f-145">提供給目的地的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-145">The number of rows offered to a destination.</span></span> <span data-ttu-id="d3d9f-146">該數目並不反映寫入目的地資料存放區的資料列。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-146">The number does not reflect rows written to the destination data store.</span></span>|  
  
 <span data-ttu-id="d3d9f-147">使用「效能 Microsoft Management Console (MMC)」嵌入式管理單元，可建立擷取效能計數器的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-147">You use the Performance Microsoft Management Console (MMC) snap-in to create a log that captures performance counters.</span></span>  
  
 <span data-ttu-id="d3d9f-148">如需如何改善效能的資訊，請參閱 [資料流程效能的功能](../data-flow/data-flow-performance-features.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-148">For information about how to improve performance, see [Data Flow Performance Features](../data-flow/data-flow-performance-features.md).</span></span>  
  
## <a name="obtain-performance-counter-statistics"></a><span data-ttu-id="d3d9f-149">取得效能計數器統計資料</span><span class="sxs-lookup"><span data-stu-id="d3d9f-149">Obtain Performance Counter Statistics</span></span>  
 <span data-ttu-id="d3d9f-150">針對部署到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，您可以使用 [dm_execution_performance_counters &#40;SSISDB 資料庫&#41;](/sql/integration-services/functions-dm-execution-performance-counters) 函數取得效能計數器統計資料。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-150">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can obtain performance counter statistics by using the [dm_execution_performance_counters &#40;SSISDB Database&#41;](/sql/integration-services/functions-dm-execution-performance-counters) function.</span></span>  
  
 <span data-ttu-id="d3d9f-151">在下列範例中，函數會傳回識別碼為 34 之執行中執行作業的統計資料。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-151">In the following example, the function returns statistics for a running execution with an ID of 34.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 <span data-ttu-id="d3d9f-152">在下列範例中，函數會傳回 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上執行之所有執行作業的統計資料。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-152">In the following example, the function returns statistics for all the executions running on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d3d9f-153">如果您是 `ssis_admin` 資料庫角色的成員，則會傳回所有執行中之執行的效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-153">If you are a member of the `ssis_admin` database role, performance statistics for all running executions are returned.</span></span>  <span data-ttu-id="d3d9f-154">如果您不是 `ssis_admin` 資料庫角色的成員，則會傳回您具有讀取權限之執行中執行的效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-154">If you are not a member of the `ssis_admin` database role, performance statistics for the running executions for which you have read permissions, are returned.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="d3d9f-155">相關內容</span><span class="sxs-lookup"><span data-stu-id="d3d9f-155">Related Content</span></span>  
  
-   <span data-ttu-id="d3d9f-156">codeplex.com 上的工具： [Business Intelligence Development Studio 的 SSIS 效能視覺化 (CodePlex 專案)](https://go.microsoft.com/fwlink/?LinkId=146626)。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-156">Tool, [SSIS Performance Visualization for Business Intelligence Development Studio (CodePlex Project)](https://go.microsoft.com/fwlink/?LinkId=146626), on codeplex.com.</span></span>  
  
-   <span data-ttu-id="d3d9f-157">msdn.microsoft.com 上的影片： [測量與了解您企業中的 SSIS 封裝資料效能 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=150497)。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-157">Video, [Measuring and Understanding the Performance of Your SSIS Packages in the Enterprise (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=150497), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="d3d9f-158">support.microsoft.com 上的技術支援文件： [升級至 Windows Server 2008 之後，效能監視器中無法再使用 SSIS 效能計數器](https://go.microsoft.com/fwlink/?LinkId=235319)(機器翻譯)。</span><span class="sxs-lookup"><span data-stu-id="d3d9f-158">Support article, [The SSIS performance counter is no longer available in the Performance Monitor after you upgrade to Windows Server 2008](https://go.microsoft.com/fwlink/?LinkId=235319), on support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d9f-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3d9f-159">See Also</span></span>  
 [<span data-ttu-id="d3d9f-160">執行專案和套件</span><span class="sxs-lookup"><span data-stu-id="d3d9f-160">Execution of Projects and Packages</span></span>](../packages/run-integration-services-ssis-packages.md)  
  
  
