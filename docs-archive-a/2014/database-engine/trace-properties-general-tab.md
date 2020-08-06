---
title: '[ (一般] 索引標籤) 的追蹤屬性 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.general.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: 25227268-143b-477e-aac9-8268bcaf2078
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 30de30c88db35a41f8f118b6545d56a78b2dec79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708577"
---
# <a name="trace-properties-general-tab"></a><span data-ttu-id="0b438-102">追蹤屬性 (一般索引標籤)</span><span class="sxs-lookup"><span data-stu-id="0b438-102">Trace Properties (General Tab)</span></span>
  <span data-ttu-id="0b438-103">使用 **[追蹤屬性]** 對話方塊的 **[一般]** 索引標籤，來檢視或指定追蹤的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b438-103">Use the **General** tab of the **Trace Properties** dialog box to view or specify properties of a trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b438-104">選項</span><span class="sxs-lookup"><span data-stu-id="0b438-104">Options</span></span>  
 <span data-ttu-id="0b438-105">**追蹤名稱**</span><span class="sxs-lookup"><span data-stu-id="0b438-105">**Trace name**</span></span>  
 <span data-ttu-id="0b438-106">指定追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b438-106">Specify the name of the trace.</span></span>  
  
 <span data-ttu-id="0b438-107">**追蹤提供者名稱**</span><span class="sxs-lookup"><span data-stu-id="0b438-107">**Trace provider name**</span></span>  
 <span data-ttu-id="0b438-108">顯示要追蹤之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="0b438-108">Shows the name of the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that will be traced.</span></span> <span data-ttu-id="0b438-109">此欄位自動以連接時指定的伺服器名稱來擴展。</span><span class="sxs-lookup"><span data-stu-id="0b438-109">This field is populated automatically with the name of the server that you specified when you connected.</span></span> <span data-ttu-id="0b438-110">若要變更追蹤提供者的名稱，請按一下 **[取消]** 以關閉對話方塊，並啟動新追蹤。</span><span class="sxs-lookup"><span data-stu-id="0b438-110">To change the name of the trace provider, click **Cancel** to close the dialog box, and start a new trace.</span></span>  
  
 <span data-ttu-id="0b438-111">**追蹤提供者類型**</span><span class="sxs-lookup"><span data-stu-id="0b438-111">**Trace provider type**</span></span>  
 <span data-ttu-id="0b438-112">顯示提供追蹤的伺服器類型。</span><span class="sxs-lookup"><span data-stu-id="0b438-112">Shows the server type that is providing the trace.</span></span> <span data-ttu-id="0b438-113">追蹤定義檔案自動擴展 **[追蹤提供者類型]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="0b438-113">The trace definition file populates the **Trace provider type** field automatically.</span></span> <span data-ttu-id="0b438-114">您無法修改此欄位。</span><span class="sxs-lookup"><span data-stu-id="0b438-114">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="0b438-115">**version**</span><span class="sxs-lookup"><span data-stu-id="0b438-115">**version**</span></span>  
 <span data-ttu-id="0b438-116">顯示提供追蹤的伺服器版本。</span><span class="sxs-lookup"><span data-stu-id="0b438-116">Shows the version of the server that is providing the trace.</span></span> <span data-ttu-id="0b438-117">追蹤定義檔案自動擴展 **[版本]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="0b438-117">The trace definition file populates the **Version** field automatically.</span></span> <span data-ttu-id="0b438-118">您無法修改此欄位。</span><span class="sxs-lookup"><span data-stu-id="0b438-118">You cannot modify this field.</span></span>  
  
 <span data-ttu-id="0b438-119">**使用範本**</span><span class="sxs-lookup"><span data-stu-id="0b438-119">**Use the template**</span></span>  
 <span data-ttu-id="0b438-120">從範本目錄中選取範本。</span><span class="sxs-lookup"><span data-stu-id="0b438-120">Select a template from the template directory.</span></span> <span data-ttu-id="0b438-121">目錄會使用專為目前追蹤提供者類型所建立的預設範本以及使用者自訂範本，進行目錄的擴展。</span><span class="sxs-lookup"><span data-stu-id="0b438-121">The directory is populated with the default templates and any user-defined templates created for the current trace provider type.</span></span>  
  
 <span data-ttu-id="0b438-122">**儲存至檔案**</span><span class="sxs-lookup"><span data-stu-id="0b438-122">**Save to file**</span></span>  
 <span data-ttu-id="0b438-123">將追蹤資料擷取到 .trc 檔。</span><span class="sxs-lookup"><span data-stu-id="0b438-123">Capture the trace data to a .trc file.</span></span> <span data-ttu-id="0b438-124">儲存追蹤資料對日後檢閱與分析很有用。</span><span class="sxs-lookup"><span data-stu-id="0b438-124">Saving trace data is useful for later review and analysis.</span></span>  
  
 <span data-ttu-id="0b438-125">**設定最大檔案大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="0b438-125">**Set maximum file size (MB)**</span></span>  
 <span data-ttu-id="0b438-126">如果您選擇將追蹤資料儲存至檔案，您必須指定追蹤檔案的大小上限。</span><span class="sxs-lookup"><span data-stu-id="0b438-126">If you choose to save the trace data to a file, you must specify the maximum size of the trace file.</span></span> <span data-ttu-id="0b438-127">預設值為 5 MB。</span><span class="sxs-lookup"><span data-stu-id="0b438-127">The default is 5 megabytes (MB).</span></span> <span data-ttu-id="0b438-128">只由存放檔案的檔案系統 (NTFS, FAT) 限制大小上限。</span><span class="sxs-lookup"><span data-stu-id="0b438-128">The maximum size is limited only by the file system (NTFS, FAT) where the file is saved.</span></span>  
  
 <span data-ttu-id="0b438-129">\<Graphic>**另存**新檔</span><span class="sxs-lookup"><span data-stu-id="0b438-129">\<Graphic> **Save As**</span></span>  
 <span data-ttu-id="0b438-130">選取儲存之後，您可以選取此圖示以變更檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0b438-130">After you have selected to save, you can select this icon to change the file name.</span></span>  
  
 <span data-ttu-id="0b438-131">**啟用檔案換用**</span><span class="sxs-lookup"><span data-stu-id="0b438-131">**Enable file rollover**</span></span>  
 <span data-ttu-id="0b438-132">選取以啟用其他檔案的建立，以在達到檔案大小上限時接受追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="0b438-132">Select to enable the creation of additional files to accept the trace data when the maximum file size is reached.</span></span> <span data-ttu-id="0b438-133">每個新檔案名稱皆包含原始 .trc 檔案名稱，並循序編號。</span><span class="sxs-lookup"><span data-stu-id="0b438-133">Each new file name consists of the original .trc file name, numbered sequentially.</span></span> <span data-ttu-id="0b438-134">例如，一旦達到檔案大小上限， **NewTrace.trc** 隨即關閉，並開啟新檔案 **NewTrace_1.trc**，接著是 **NewTrace_2.trc**等等。</span><span class="sxs-lookup"><span data-stu-id="0b438-134">For example, once it reaches maximum file size, **NewTrace.trc** closes, and a new file, **NewTrace_1.trc**, opens, followed by **NewTrace_2.trc**, and so on.</span></span> <span data-ttu-id="0b438-135">依預設，將追蹤儲存至檔案時，檔案換用為已啟用。</span><span class="sxs-lookup"><span data-stu-id="0b438-135">File rollover is enabled by default when you save a trace to a file.</span></span>  
  
 <span data-ttu-id="0b438-136">**伺服器處理追蹤資料**</span><span class="sxs-lookup"><span data-stu-id="0b438-136">**Server processes trace data**</span></span>  
 <span data-ttu-id="0b438-137">指定執行追蹤的伺服器應處理追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="0b438-137">Specify that the server running the trace should process the trace data.</span></span> <span data-ttu-id="0b438-138">使用此選項會降低追蹤所造成的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="0b438-138">Using this option reduces the performance overhead incurred by tracing.</span></span> <span data-ttu-id="0b438-139">如果選取此選項，即使在負荷過重的狀況下仍不會略過任何事件。</span><span class="sxs-lookup"><span data-stu-id="0b438-139">If selected, no events are skipped even under stress conditions.</span></span> <span data-ttu-id="0b438-140">如果清除此核取方塊，則 SQL Server Profiler 會執行此處理，而在負荷過重的狀況下有可能不追蹤某些事件。</span><span class="sxs-lookup"><span data-stu-id="0b438-140">If this check box is cleared, processing is performed by SQL Server Profiler, and there is a possibility that some events are not traced under stress conditions.</span></span>  
  
 <span data-ttu-id="0b438-141">**儲存至資料表**</span><span class="sxs-lookup"><span data-stu-id="0b438-141">**Save to table**</span></span>  
 <span data-ttu-id="0b438-142">將追蹤資料擷取到資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="0b438-142">Capture the trace data to a database table.</span></span> <span data-ttu-id="0b438-143">儲存追蹤資料對日後檢閱與分析很有用。</span><span class="sxs-lookup"><span data-stu-id="0b438-143">Saving trace data is useful for later review and analysis.</span></span> <span data-ttu-id="0b438-144">不過，將追蹤資料儲存至資料表，可能導致儲存追蹤的伺服器負擔過重。</span><span class="sxs-lookup"><span data-stu-id="0b438-144">However, saving trace data to a table can incur significant overhead on the server where the trace is being saved.</span></span> <span data-ttu-id="0b438-145">可能的話，不要將追蹤資料表儲存在被追蹤的同一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0b438-145">If possible, do not save the trace table on the same server that is being traced.</span></span>  
  
 <span data-ttu-id="0b438-146">\<Graphic>**目的地資料表**</span><span class="sxs-lookup"><span data-stu-id="0b438-146">\<Graphic> **Destination Table**</span></span>  
 <span data-ttu-id="0b438-147">選取將追蹤資料儲存至資料庫資料表之後，您可以選取此圖示以變更資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="0b438-147">After you have selected to save the trace data to a database table, you can select this icon to change the table name.</span></span>  
  
 <span data-ttu-id="0b438-148">**設定最大資料列數 (單位: 千)**</span><span class="sxs-lookup"><span data-stu-id="0b438-148">**Set maximum rows (in thousands)**</span></span>  
 <span data-ttu-id="0b438-149">指定儲存資料的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="0b438-149">Specify the largest number of rows in which to save data.</span></span> <span data-ttu-id="0b438-150">預設為 1000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="0b438-150">The default is 1000 rows.</span></span>  
  
 <span data-ttu-id="0b438-151">**啟用追蹤停止時間**</span><span class="sxs-lookup"><span data-stu-id="0b438-151">**Enable trace stop time**</span></span>  
 <span data-ttu-id="0b438-152">設定追蹤結束與自動關閉的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="0b438-152">Set the date and time for the trace to end and close itself.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b438-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b438-153">See Also</span></span>  
 [<span data-ttu-id="0b438-154">建立追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="0b438-154">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
  
