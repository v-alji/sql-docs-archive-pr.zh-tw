---
title: 記錄檔屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3761ce3dca232db8968a2a7cba083dcc5554d792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710846"
---
# <a name="log-properties"></a><span data-ttu-id="56fda-102">記錄屬性</span><span class="sxs-lookup"><span data-stu-id="56fda-102">Log Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="56fda-103">支援下表列出的記錄伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="56fda-103">supports the log server properties listed in the following tables.</span></span> <span data-ttu-id="56fda-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="56fda-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
## <a name="general"></a><span data-ttu-id="56fda-105">一般</span><span class="sxs-lookup"><span data-stu-id="56fda-105">General</span></span>  
 `File`  
 <span data-ttu-id="56fda-106">此為字串屬性，識別伺服器記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fda-106">A string property that identifies the name of the server log file.</span></span> <span data-ttu-id="56fda-107">這個屬性只適用於當記錄會儲存到磁碟檔案，而非資料庫資料表時 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="56fda-107">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="56fda-108">此屬性的預設值為 msmdsrv.log。</span><span class="sxs-lookup"><span data-stu-id="56fda-108">The default value for this property is msmdsrv.log.</span></span>  
  
 `FileBufferSize`  
 <span data-ttu-id="56fda-109">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MessageLogs`  
 <span data-ttu-id="56fda-110">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="error-log"></a><span data-ttu-id="56fda-111">錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="56fda-111">Error Log</span></span>  
 <span data-ttu-id="56fda-112">您可以在伺服器執行個體層級設定這些屬性，以修改顯示在其他工具和設計師中之錯誤組態的預設值。</span><span class="sxs-lookup"><span data-stu-id="56fda-112">You can set these properties at the server instance level to modify the default values for Error Configuration that appear in other tools and designers.</span></span> <span data-ttu-id="56fda-113">如需詳細資訊，請參閱[Cube、資料分割和維度處理的錯誤設定 &#40;SSAS-](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)多維度&#41;和 <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="56fda-113">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md) and <xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A> for more information.</span></span>  
  
 <span data-ttu-id="56fda-114">**ErrorLog\ErrorLogFileName**</span><span class="sxs-lookup"><span data-stu-id="56fda-114">**ErrorLog\ErrorLogFileName**</span></span>  
 <span data-ttu-id="56fda-115">此屬性在伺服器執行處理作業期間，用來作為預設值。</span><span class="sxs-lookup"><span data-stu-id="56fda-115">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="56fda-116">**ErrorLog\ErrorLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="56fda-116">**ErrorLog\ErrorLogFileSize**</span></span>  
 <span data-ttu-id="56fda-117">此屬性在伺服器執行處理作業期間，用來作為預設值。</span><span class="sxs-lookup"><span data-stu-id="56fda-117">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="56fda-118">**ErrorLog\KeyErrorAction**</span><span class="sxs-lookup"><span data-stu-id="56fda-118">**ErrorLog\KeyErrorAction**</span></span>  
 <span data-ttu-id="56fda-119">指定伺服器在 錯誤發生時所採取的動作`KeyNotFound`。</span><span class="sxs-lookup"><span data-stu-id="56fda-119">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="56fda-120">此錯誤的有效回應包括：</span><span class="sxs-lookup"><span data-stu-id="56fda-120">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="56fda-121">`ConvertToUnknown` 會要求伺服器將錯誤索引鍵值配置給未知的成員。</span><span class="sxs-lookup"><span data-stu-id="56fda-121">`ConvertToUnknown` tells the server to allocate the error key value to the unknown member.</span></span>  
  
-   <span data-ttu-id="56fda-122">`DiscardRecord` 會要求伺服器排除這個記錄。</span><span class="sxs-lookup"><span data-stu-id="56fda-122">`DiscardRecord` tells the server to exclude the record.</span></span>  
  
 <span data-ttu-id="56fda-123">**ErrorLog\KeyErrorLogFile**</span><span class="sxs-lookup"><span data-stu-id="56fda-123">**ErrorLog\KeyErrorLogFile**</span></span>  
 <span data-ttu-id="56fda-124">這是副檔名必須為 .log 的使用者定義檔案名稱，位於服務帳戶具有讀寫權限的資料夾內。</span><span class="sxs-lookup"><span data-stu-id="56fda-124">This is a user-defined filename that must have a .log file extension, located in a folder on which the service account has read-write permissions.</span></span> <span data-ttu-id="56fda-125">此記錄檔只會包含處理期間產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="56fda-125">This log file will only contain errors generated during processing.</span></span> <span data-ttu-id="56fda-126">如果需要更詳細的資訊，請使用飛行記錄器。</span><span class="sxs-lookup"><span data-stu-id="56fda-126">Use the Flight Recorder if you require more detailed information.</span></span>  
  
 <span data-ttu-id="56fda-127">**ErrorLog\KeyErrorLimit**</span><span class="sxs-lookup"><span data-stu-id="56fda-127">**ErrorLog\KeyErrorLimit**</span></span>  
 <span data-ttu-id="56fda-128">這是伺服器允許的資料完整性錯誤數上限，達到此上限之後，即無法繼續處理。</span><span class="sxs-lookup"><span data-stu-id="56fda-128">This is the maximum number of data integrity errors that the server will allow before failing the processing.</span></span> <span data-ttu-id="56fda-129">值為 -1 表示沒有限制。</span><span class="sxs-lookup"><span data-stu-id="56fda-129">A value of -1 indicates that there is no limit.</span></span> <span data-ttu-id="56fda-130">預設值為 0，表示在發生第一個錯誤之後停止處理。</span><span class="sxs-lookup"><span data-stu-id="56fda-130">The default is 0, which means processing stops after the first error occurs.</span></span> <span data-ttu-id="56fda-131">您也可以將其設為整數。</span><span class="sxs-lookup"><span data-stu-id="56fda-131">You can also set it to a whole number.</span></span>  
  
 <span data-ttu-id="56fda-132">**ErrorLog\KeyErrorLimitAction**</span><span class="sxs-lookup"><span data-stu-id="56fda-132">**ErrorLog\KeyErrorLimitAction**</span></span>  
 <span data-ttu-id="56fda-133">指定伺服器在索引鍵錯誤數目達到上限時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56fda-133">Specifies the action taken by the server when the number of key errors has reached the upper limit.</span></span> <span data-ttu-id="56fda-134">此動作的有效回應包括：</span><span class="sxs-lookup"><span data-stu-id="56fda-134">Valid responses to this action include:</span></span>  
  
-   <span data-ttu-id="56fda-135">`StopProcessing` 告知伺服器應於達到錯誤限制時停止處理。</span><span class="sxs-lookup"><span data-stu-id="56fda-135">`StopProcessing` tells the server to stop processing when the error limit is reached.</span></span>  
  
-   <span data-ttu-id="56fda-136">`StopLogging` 告知伺服器應於達到錯誤限制時停止記錄錯誤，但仍讓處理作業繼續進行。</span><span class="sxs-lookup"><span data-stu-id="56fda-136">`StopLogging` tells the server to stop logging errors when the error limit is reached, but allow processing to continue.</span></span>  
  
 <span data-ttu-id="56fda-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span><span class="sxs-lookup"><span data-stu-id="56fda-137">**ErrorLog\ LogErrorTypes\KeyNotFound**</span></span>  
 <span data-ttu-id="56fda-138">指定伺服器在 錯誤發生時所採取的動作`KeyNotFound`。</span><span class="sxs-lookup"><span data-stu-id="56fda-138">Specifies the action taken by the server when a `KeyNotFound` error occurs.</span></span> <span data-ttu-id="56fda-139">此錯誤的有效回應包括：</span><span class="sxs-lookup"><span data-stu-id="56fda-139">Valid responses to this error include:</span></span>  
  
-   <span data-ttu-id="56fda-140">`IgnoreError` 會要求伺服器繼續處理，但不記錄錯誤或將其計入索引鍵錯誤限制。</span><span class="sxs-lookup"><span data-stu-id="56fda-140">`IgnoreError` tells the server to continue processing without logging the error or counting it towards the key error limit.</span></span> <span data-ttu-id="56fda-141">如果忽略錯誤，您僅允許繼續處理，而不將錯誤加入錯誤計數，或將其記錄至畫面或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="56fda-141">By ignoring the error, you simply allow processing to continue without adding to the error count or logging it to the screen or log file.</span></span> <span data-ttu-id="56fda-142">有問題的記錄發生資料完整性問題，無法加入資料庫。</span><span class="sxs-lookup"><span data-stu-id="56fda-142">The record in question has a data integrity problem and cannot be added to the database.</span></span> <span data-ttu-id="56fda-143">依據 `KeyErrorAction` 屬性的判斷，該記錄將會被捨棄或彙總至未知的成員。</span><span class="sxs-lookup"><span data-stu-id="56fda-143">The record will either be discarded or aggregated to Unknown Member, as determined by the `KeyErrorAction` property.</span></span>  
  
-   <span data-ttu-id="56fda-144">`ReportAndContinue` 告知伺服器應記錄錯誤並將其計數算入索引鍵錯誤限制，接著繼續處理。</span><span class="sxs-lookup"><span data-stu-id="56fda-144">`ReportAndContinue` tells the server to log the error, count it towards the key error limit, and continue processing.</span></span> <span data-ttu-id="56fda-145">觸發錯誤的記錄會被捨棄，或是轉換成未知的成員。</span><span class="sxs-lookup"><span data-stu-id="56fda-145">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
-   <span data-ttu-id="56fda-146">`ReportAndStop` 告知伺服器應記錄錯誤並立即停止處理，而無視於索引鍵錯誤限制。</span><span class="sxs-lookup"><span data-stu-id="56fda-146">`ReportAndStop` tells the server to log the error and stop processing immediately, regardless of the key error limit.</span></span> <span data-ttu-id="56fda-147">觸發錯誤的記錄會被捨棄，或是轉換成未知的成員。</span><span class="sxs-lookup"><span data-stu-id="56fda-147">The record triggering the error is discarded or converted to Unknown Member.</span></span>  
  
 <span data-ttu-id="56fda-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span><span class="sxs-lookup"><span data-stu-id="56fda-148">**ErrorLog\ LogErrorTypes\KeyDuplicate**</span></span>  
 <span data-ttu-id="56fda-149">指定伺服器在發現索引鍵重複狀況時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56fda-149">Specifies the action taken by the server when a duplicate key is found.</span></span> <span data-ttu-id="56fda-150">`IgnoreError`有效值包括 `ReportAndContinue` (繼續處理，就像沒有發生錯誤一樣)、`ReportAndStop` (記錄錯誤並繼續處理)，以及  (記錄錯誤並立即停止處理，即使錯誤計數未達錯誤限制也一樣)。</span><span class="sxs-lookup"><span data-stu-id="56fda-150">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="56fda-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span><span class="sxs-lookup"><span data-stu-id="56fda-151">**ErrorLog\ LogErrorTypes\NullKeyConvertedToUnknown**</span></span>  
 <span data-ttu-id="56fda-152">指定伺服器在 Null 索引鍵轉換為未知的成員時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56fda-152">Specifies the action taken by the server when a null key has been converted to Unknown Member.</span></span> <span data-ttu-id="56fda-153">`IgnoreError`有效值包括 `ReportAndContinue` (繼續處理，就像沒有發生錯誤一樣)、`ReportAndStop` (記錄錯誤並繼續處理)，以及  (記錄錯誤並立即停止處理，即使錯誤計數未達錯誤限制也一樣)。</span><span class="sxs-lookup"><span data-stu-id="56fda-153">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="56fda-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span><span class="sxs-lookup"><span data-stu-id="56fda-154">**ErrorLog\ LogErrorTypes\NullKeyNotAllowed**</span></span>  
 <span data-ttu-id="56fda-155">`NullProcessing`指定伺服器在維度屬性的 `Error` 設為 時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56fda-155">Specifies the action taken by the server when `NullProcessing` is set to `Error` for a dimension attribute.</span></span> <span data-ttu-id="56fda-156">當給定的屬性中不允許 Null 值時，會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="56fda-156">An error is generated when a null value is not allowed in a given attribute.</span></span> <span data-ttu-id="56fda-157">此錯誤組態屬性會通知下一個步驟，也就是報告錯誤並繼續處理，直到達到錯誤限制為止。</span><span class="sxs-lookup"><span data-stu-id="56fda-157">This error configuration property informs the next step, which is to report the error and continue processing until the error limit is reached.</span></span> <span data-ttu-id="56fda-158">`IgnoreError`有效值包括 `ReportAndContinue` (繼續處理，就像沒有發生錯誤一樣)、`ReportAndStop` (記錄錯誤並繼續處理)，以及  (記錄錯誤並立即停止處理，即使錯誤計數未達錯誤限制也一樣)。</span><span class="sxs-lookup"><span data-stu-id="56fda-158">Valid values include `IgnoreError` to continue processing as if the error did not occur, `ReportAndContinue` to log the error and continue processing, and `ReportAndStop` to log the error and stop processing immediately, even if the error count is below the error limit.</span></span>  
  
 <span data-ttu-id="56fda-159">**ErrorLog\ LogErrorTypes\CalculationError**</span><span class="sxs-lookup"><span data-stu-id="56fda-159">**ErrorLog\ LogErrorTypes\CalculationError**</span></span>  
 <span data-ttu-id="56fda-160">此屬性在伺服器執行處理作業期間，用來作為預設值。</span><span class="sxs-lookup"><span data-stu-id="56fda-160">A property used as a default during processing operation performed by the server.</span></span>  
  
 <span data-ttu-id="56fda-161">**ErrorLog\IgnoreDataTruncation**</span><span class="sxs-lookup"><span data-stu-id="56fda-161">**ErrorLog\IgnoreDataTruncation**</span></span>  
 <span data-ttu-id="56fda-162">此屬性在伺服器執行處理作業期間，用來作為預設值。</span><span class="sxs-lookup"><span data-stu-id="56fda-162">A property used as a default during processing operation performed by the server.</span></span>  
  
## <a name="exception"></a><span data-ttu-id="56fda-163">例外狀況</span><span class="sxs-lookup"><span data-stu-id="56fda-163">Exception</span></span>  
 <span data-ttu-id="56fda-164">**Exception\CreateAndSendCrashReports**</span><span class="sxs-lookup"><span data-stu-id="56fda-164">**Exception\CreateAndSendCrashReports**</span></span>  
 <span data-ttu-id="56fda-165">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-165">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-166">**Exception\CrashReportsFolder**</span><span class="sxs-lookup"><span data-stu-id="56fda-166">**Exception\CrashReportsFolder**</span></span>  
 <span data-ttu-id="56fda-167">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-167">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-168">**Exception\SQLDumperFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="56fda-168">**Exception\SQLDumperFlagsOn**</span></span>  
 <span data-ttu-id="56fda-169">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-170">**Exception\SQLDumperFlagsOff**</span><span class="sxs-lookup"><span data-stu-id="56fda-170">**Exception\SQLDumperFlagsOff**</span></span>  
 <span data-ttu-id="56fda-171">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-172">**Exception\MiniDumpFlagsOn**</span><span class="sxs-lookup"><span data-stu-id="56fda-172">**Exception\MiniDumpFlagsOn**</span></span>  
 <span data-ttu-id="56fda-173">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-173">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-174">**Exception\MinidumpErrorList**</span><span class="sxs-lookup"><span data-stu-id="56fda-174">**Exception\MinidumpErrorList**</span></span>  
 <span data-ttu-id="56fda-175">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-175">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="flight-recorder"></a><span data-ttu-id="56fda-176">飛行記錄器</span><span class="sxs-lookup"><span data-stu-id="56fda-176">Flight Recorder</span></span>  
 <span data-ttu-id="56fda-177">**FlightRecorder\Enabled**</span><span class="sxs-lookup"><span data-stu-id="56fda-177">**FlightRecorder\Enabled**</span></span>  
 <span data-ttu-id="56fda-178">此為布林值屬性，指出是否啟用飛行記錄器功能。</span><span class="sxs-lookup"><span data-stu-id="56fda-178">A Boolean property that indicates whether the flight recorder feature is enabled.</span></span>  
  
 <span data-ttu-id="56fda-179">**FlightRecorder\FileSizeMB**</span><span class="sxs-lookup"><span data-stu-id="56fda-179">**FlightRecorder\FileSizeMB**</span></span>  
 <span data-ttu-id="56fda-180">此為帶正負號的 32 位元整數屬性，定義飛行記錄器磁碟檔案的大小 (以 MB 表示)。</span><span class="sxs-lookup"><span data-stu-id="56fda-180">A signed 32-bit integer property that defines the size of the flight recorder disk file, in megabytes.</span></span>  
  
 <span data-ttu-id="56fda-181">**FlightRecorder\LogDurationSec**</span><span class="sxs-lookup"><span data-stu-id="56fda-181">**FlightRecorder\LogDurationSec**</span></span>  
 <span data-ttu-id="56fda-182">此為帶正負號的 32 位元整數屬性，定義飛行記錄器換用的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="56fda-182">A signed 32-bit integer property that defines the frequency that the flight recorder is rolled over, in seconds.</span></span>  
  
 <span data-ttu-id="56fda-183">**FlightRecorder\SnapshotDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="56fda-183">**FlightRecorder\SnapshotDefinitionFile**</span></span>  
 <span data-ttu-id="56fda-184">此為字串屬性，定義快照集定義檔案的名稱，包含採取快照集時，發給伺服器的探索命令。</span><span class="sxs-lookup"><span data-stu-id="56fda-184">A string property that defines the name of the snapshot definition file, containing discover commands that are issued to the server when a snapshot is taken.</span></span>  
  
 <span data-ttu-id="56fda-185">此屬性的預設值是空白，因而會預設為 FlightRecorderSnapshotDef.xml 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="56fda-185">The default value for this property is blank, which in turn defaults to file name FlightRecorderSnapshotDef.xml.</span></span>  
  
 <span data-ttu-id="56fda-186">**FlightRecorder\SnapshotFrequencySec**</span><span class="sxs-lookup"><span data-stu-id="56fda-186">**FlightRecorder\SnapshotFrequencySec**</span></span>  
 <span data-ttu-id="56fda-187">此為帶正負號的 32 位元整數屬性，定義快照集頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="56fda-187">A signed 32-bit integer property that defines the snapshot frequency, in seconds.</span></span>  
  
 <span data-ttu-id="56fda-188">**FlightRecorder\TraceDefinitionFile**</span><span class="sxs-lookup"><span data-stu-id="56fda-188">**FlightRecorder\TraceDefinitionFile**</span></span>  
 <span data-ttu-id="56fda-189">此為字串屬性，指定飛行記錄器追蹤定義檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fda-189">A string property that specifies the name of the flight recorder trace definition file.</span></span>  
  
 <span data-ttu-id="56fda-190">此屬性的預設值是空白，因而會預設為 FlightRecorderTraceDef.xml。</span><span class="sxs-lookup"><span data-stu-id="56fda-190">The default value for this property is blank, which in turn defaults to FlightRecorderTraceDef.xml.</span></span>  
  
## <a name="query-log"></a><span data-ttu-id="56fda-191">查詢記錄</span><span class="sxs-lookup"><span data-stu-id="56fda-191">Query Log</span></span>  
 <span data-ttu-id="56fda-192">**適用物件：** 僅限多維度伺服器模式</span><span class="sxs-lookup"><span data-stu-id="56fda-192">**Applies to:** Multidimensional server mode only</span></span>  
  
 <span data-ttu-id="56fda-193">**QueryLog\QueryLogFileName**</span><span class="sxs-lookup"><span data-stu-id="56fda-193">**QueryLog\QueryLogFileName**</span></span>  
 <span data-ttu-id="56fda-194">此為字串屬性，指定查詢記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fda-194">A string property that specifies the name of the query log file.</span></span> <span data-ttu-id="56fda-195">這個屬性只適用於當記錄會儲存到磁碟檔案，而非資料庫資料表時 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="56fda-195">This property only applies when a disk file is used for logging, as opposed to a database table (the default behavior).</span></span>  
  
 <span data-ttu-id="56fda-196">**QueryLog\QueryLogSampling**</span><span class="sxs-lookup"><span data-stu-id="56fda-196">**QueryLog\QueryLogSampling**</span></span>  
 <span data-ttu-id="56fda-197">此為帶正負號的 32 位元整數屬性，指定查詢記錄取樣率。</span><span class="sxs-lookup"><span data-stu-id="56fda-197">A signed 32-bit integer property that specifies the query log sampling rate.</span></span>  
  
 <span data-ttu-id="56fda-198">此屬性的預設值為 10，表示每 10 筆伺服器查詢會記錄 1 筆。</span><span class="sxs-lookup"><span data-stu-id="56fda-198">The default value for this property is 10, meaning that 1 out of every 10 server queries is logged.</span></span>  
  
 <span data-ttu-id="56fda-199">**QueryLog\QueryLogFileSize**</span><span class="sxs-lookup"><span data-stu-id="56fda-199">**QueryLog\QueryLogFileSize**</span></span>  
 <span data-ttu-id="56fda-200">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-200">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-201">**QueryLog\QueryLogConnectionString**</span><span class="sxs-lookup"><span data-stu-id="56fda-201">**QueryLog\QueryLogConnectionString**</span></span>  
 <span data-ttu-id="56fda-202">此為字串屬性，指定查詢記錄資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="56fda-202">A string property that specifies the connection to the query log database.</span></span>  
  
 <span data-ttu-id="56fda-203">**QueryLog\QueryLogTableName**</span><span class="sxs-lookup"><span data-stu-id="56fda-203">**QueryLog\QueryLogTableName**</span></span>  
 <span data-ttu-id="56fda-204">此為字串屬性，指定查詢記錄資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="56fda-204">A string property that specifies the name of the query log table.</span></span>  
  
 <span data-ttu-id="56fda-205">此屬性的預設值為 OlapQueryLog。</span><span class="sxs-lookup"><span data-stu-id="56fda-205">The default value for this property is OlapQueryLog.</span></span>  
  
 <span data-ttu-id="56fda-206">**QueryLog\CreateQueryLogTable**</span><span class="sxs-lookup"><span data-stu-id="56fda-206">**QueryLog\CreateQueryLogTable**</span></span>  
 <span data-ttu-id="56fda-207">此為布林值屬性，指定是否建立查詢記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="56fda-207">A Boolean property that specifies whether to create the query log table.</span></span>  
  
 <span data-ttu-id="56fda-208">此屬性的預設值為 False，表示伺服器不會自動建立記錄資料表，也不會記錄查詢事件。</span><span class="sxs-lookup"><span data-stu-id="56fda-208">The default value for this property is false, which indicates the server will not automatically create the log table and will not log query events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56fda-209">如需設定查詢記錄的詳細資訊，請參閱[Analysis Services 中的記錄作業](../instances/log-operations-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56fda-209">For more information about configuring the query log, see [Log operations in Analysis Services](../instances/log-operations-in-analysis-services.md).</span></span>  
  
## <a name="trace"></a><span data-ttu-id="56fda-210">追蹤</span><span class="sxs-lookup"><span data-stu-id="56fda-210">Trace</span></span>  
 <span data-ttu-id="56fda-211">**Trace\TraceBackgroundDistributionPeriod**</span><span class="sxs-lookup"><span data-stu-id="56fda-211">**Trace\TraceBackgroundDistributionPeriod**</span></span>  
 <span data-ttu-id="56fda-212">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-212">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-213">**Trace\TraceBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="56fda-213">**Trace\TraceBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="56fda-214">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-215">**Trace\TraceFileBufferSize**</span><span class="sxs-lookup"><span data-stu-id="56fda-215">**Trace\TraceFileBufferSize**</span></span>  
 <span data-ttu-id="56fda-216">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-216">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-217">**Trace\TraceFileWriteTrailerPeriod**</span><span class="sxs-lookup"><span data-stu-id="56fda-217">**Trace\TraceFileWriteTrailerPeriod**</span></span>  
 <span data-ttu-id="56fda-218">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-219">**Trace\TraceMaxRowsetSize**</span><span class="sxs-lookup"><span data-stu-id="56fda-219">**Trace\TraceMaxRowsetSize**</span></span>  
 <span data-ttu-id="56fda-220">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-221">**Trace\TraceProtocolTraffic**</span><span class="sxs-lookup"><span data-stu-id="56fda-221">**Trace\TraceProtocolTraffic**</span></span>  
 <span data-ttu-id="56fda-222">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-222">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-223">**Trace\TraceQueryResponseTextChunkSize**</span><span class="sxs-lookup"><span data-stu-id="56fda-223">**Trace\TraceQueryResponseTextChunkSize**</span></span>  
 <span data-ttu-id="56fda-224">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-225">**Trace\TraceReportFQDN**</span><span class="sxs-lookup"><span data-stu-id="56fda-225">**Trace\TraceReportFQDN**</span></span>  
 <span data-ttu-id="56fda-226">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-226">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-227">**Trace\TraceRequestParameters**</span><span class="sxs-lookup"><span data-stu-id="56fda-227">**Trace\TraceRequestParameters**</span></span>  
 <span data-ttu-id="56fda-228">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="56fda-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span><span class="sxs-lookup"><span data-stu-id="56fda-229">**Trace\TraceRowsetBackgroundFlushPeriod**</span></span>  
 <span data-ttu-id="56fda-230">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="56fda-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fda-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56fda-231">See Also</span></span>  
 <span data-ttu-id="56fda-232">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="56fda-232">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="56fda-233">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="56fda-233">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
