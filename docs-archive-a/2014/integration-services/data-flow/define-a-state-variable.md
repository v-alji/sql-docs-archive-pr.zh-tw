---
title: 定義狀態變數 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 45d66152-883a-49a7-a877-2e8ab45f8f79
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5214b3512ea0113d1abace61a76033e5531ac99f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709821"
---
# <a name="define-a-state-variable"></a><span data-ttu-id="49b99-102">定義狀態變數</span><span class="sxs-lookup"><span data-stu-id="49b99-102">Define a State Variable</span></span>
  <span data-ttu-id="49b99-103">此程序描述如何定義 CDC 狀態儲存所在的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="49b99-103">This procedure describes how to define a package variable where the CDC state is stored.</span></span>  
  
 <span data-ttu-id="49b99-104">CDC 狀態變數是由 CDC 控制工作所載入、初始化及更新，並且由 CDC 來源資料流程元件用來判斷變更記錄目前的處理範圍。</span><span class="sxs-lookup"><span data-stu-id="49b99-104">The CDC state variable is loaded, initialized, and updated by the CDC Control task and is used by the CDC Source data flow component to determine the current processing range for change records.</span></span> <span data-ttu-id="49b99-105">CDC 狀態變數可定義於 CDC 控制工作和 CDC 來源通用的任何容器上。</span><span class="sxs-lookup"><span data-stu-id="49b99-105">The CDC state variable can be defined on any container common to the CDC Control task and the CDC source.</span></span> <span data-ttu-id="49b99-106">這可以是在封裝層級，但也可以是在其他容器，如迴圈容器。</span><span class="sxs-lookup"><span data-stu-id="49b99-106">This may be at the package level but may also be on other containers such as a loop container.</span></span>  
  
 <span data-ttu-id="49b99-107">不建議手動修改 CDC 狀態變數值，但這有助於您了解其內容。</span><span class="sxs-lookup"><span data-stu-id="49b99-107">Manually modifying the CDC state variable value is not recommended, however it can be useful to understand its contents.</span></span>  
  
 <span data-ttu-id="49b99-108">下表提供 CDC 狀態變數值各項元件的進階說明。</span><span class="sxs-lookup"><span data-stu-id="49b99-108">The following table provides a high-level description of the components of the CDC state variable value.</span></span>  
  
|<span data-ttu-id="49b99-109">元件</span><span class="sxs-lookup"><span data-stu-id="49b99-109">Component</span></span>|<span data-ttu-id="49b99-110">描述</span><span class="sxs-lookup"><span data-stu-id="49b99-110">Description</span></span>|  
|---------------|-----------------|  
|`<state-name>`|<span data-ttu-id="49b99-111">此為目前 CDC 狀態的名稱。</span><span class="sxs-lookup"><span data-stu-id="49b99-111">This is the name of the current CDC state.</span></span>|  
|`CS`|<span data-ttu-id="49b99-112">此標示目前處理範圍的起點 (Current Start)。</span><span class="sxs-lookup"><span data-stu-id="49b99-112">This marks the current processing range start point (Current Start).</span></span>|  
|`<cs-lsn>`|<span data-ttu-id="49b99-113">此為上一個 CDC 回合最後處理的 LSN (記錄序號)。</span><span class="sxs-lookup"><span data-stu-id="49b99-113">This is the last (Log Sequence Number) LSN processed in the previous CDC run.</span></span>|  
|`CE`|<span data-ttu-id="49b99-114">此標示目前處理範圍的終點 (Current End)。</span><span class="sxs-lookup"><span data-stu-id="49b99-114">This marks the current processing range end point (Current End).</span></span> <span data-ttu-id="49b99-115">CDC 狀態中若存在 CE 元件，代表目前正在處理 CDC 封裝，或是 CDC 封裝在其 CDC 處理範圍未處理完全之前即已失敗。</span><span class="sxs-lookup"><span data-stu-id="49b99-115">The presence of the CE component in the CDC state is an indication that either a CDC package is currently processing or that a CDC package failed before fully processing its CDC processing range.</span></span>|  
|`<ce-lsn>`|<span data-ttu-id="49b99-116">此為目前 CDC 回合要處理的最後一個 LSN。</span><span class="sxs-lookup"><span data-stu-id="49b99-116">This is the last LSN to be processed in the current CDC Run.</span></span> <span data-ttu-id="49b99-117">處理的最後一個序號一律假設為最大值 (0xFFF...)。</span><span class="sxs-lookup"><span data-stu-id="49b99-117">It is always assumed that the last sequence number to be processed is the maximum (0xFFF...).</span></span>|  
|`IR`|<span data-ttu-id="49b99-118">此標示初始處理範圍。</span><span class="sxs-lookup"><span data-stu-id="49b99-118">This marks the initial processing range.</span></span>|  
|`<ir-start>`|<span data-ttu-id="49b99-119">此為初始載入剛要開始前之異動的 LSN。</span><span class="sxs-lookup"><span data-stu-id="49b99-119">This is an LSN of a change just before the initial load began.</span></span>|  
|`<ir-end>`|<span data-ttu-id="49b99-120">此為初始載入才剛結束後之異動的 LSN。</span><span class="sxs-lookup"><span data-stu-id="49b99-120">This is an LSN of a change just after the initial load ended.</span></span>|  
|`TS`|<span data-ttu-id="49b99-121">此標示上次 CDC 狀態更新的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="49b99-121">This marks the timestamp for the last CDC state update.</span></span>|  
|**\<timestamp>**|<span data-ttu-id="49b99-122">此為 64 位元 System.DateTime.UtcNow 屬性的十進位表示法。</span><span class="sxs-lookup"><span data-stu-id="49b99-122">This is a decimal representation of the 64-bit, System.DateTime.UtcNow property.</span></span>|  
|`ER`|<span data-ttu-id="49b99-123">此將在上次作業失敗時出現，且包含錯誤原因的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="49b99-123">This appears when the last operation failed and includes a short description of the cause of the error.</span></span> <span data-ttu-id="49b99-124">若存在此元件，則其一定出現於最後。</span><span class="sxs-lookup"><span data-stu-id="49b99-124">If this component is present, it will always appear last.</span></span>|  
|`<short-error-text>`|<span data-ttu-id="49b99-125">此為簡短的錯誤描述。</span><span class="sxs-lookup"><span data-stu-id="49b99-125">This is the short error description.</span></span>|  
  
 <span data-ttu-id="49b99-126">每個 LSN 和序號都是編碼為多達 20 位數的十六進位字串，代表 Binary(10) 的 LSN 值。</span><span class="sxs-lookup"><span data-stu-id="49b99-126">The LSNs and sequence numbers are each encoded as a hexadecimal string of up to 20 digits representing the LSN value of Binary(10).</span></span>  
  
 <span data-ttu-id="49b99-127">下表描述可能的 CDC 狀態值。</span><span class="sxs-lookup"><span data-stu-id="49b99-127">The following table describes the possible CDC state values.</span></span>  
  
|<span data-ttu-id="49b99-128">State</span><span class="sxs-lookup"><span data-stu-id="49b99-128">State</span></span>|<span data-ttu-id="49b99-129">描述</span><span class="sxs-lookup"><span data-stu-id="49b99-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49b99-130">(INITIAL)</span><span class="sxs-lookup"><span data-stu-id="49b99-130">(INITIAL)</span></span>|<span data-ttu-id="49b99-131">這是目前的 CDC 群組上有任何封裝執行之前的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-131">This is the initial state before the any package was run on the current CDC group.</span></span> <span data-ttu-id="49b99-132">這也是 CDC 狀態為空白時呈現的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-132">This is also the state when the CDC state is empty.</span></span>|  
|<span data-ttu-id="49b99-133">ILSTART (初始載入開始)</span><span class="sxs-lookup"><span data-stu-id="49b99-133">ILSTART (Initial Load Started)</span></span>|<span data-ttu-id="49b99-134">這是在 CDC 控制工作的 `MarkInitialLoadStart` 作業呼叫之後，初始載入封裝開始時的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-134">This is the state when the initial load package starts, after the `MarkInitialLoadStart` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="49b99-135">ILEND (初始載入結束)</span><span class="sxs-lookup"><span data-stu-id="49b99-135">ILEND (Initial Load Ended)</span></span>|<span data-ttu-id="49b99-136">這是在 CDC 控制工作的 `MarkInitialLoadEnd` 作業呼叫之後，初始載入封裝順利結束時的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-136">This is the state when the initial load package ends successfully, after the `MarkInitialLoadEnd` operation call to the CDC Control task.</span></span>|  
|<span data-ttu-id="49b99-137">ILUPDATE (初始載入更新)</span><span class="sxs-lookup"><span data-stu-id="49b99-137">ILUPDATE (Initial Load Update)</span></span>|<span data-ttu-id="49b99-138">這是緊接於初始載入之後而仍在處理初始處理範圍期間執行 Trickle 摘要更新封裝時的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-138">This is the state on the runs of the trickle feed update package following the initial load, while still processing the initial processing range.</span></span> <span data-ttu-id="49b99-139">發生於 CDC 控制工作的 `GetProcessingRange` 作業呼叫之後。</span><span class="sxs-lookup"><span data-stu-id="49b99-139">This is after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="49b99-140">如果使用了 __$reprocessing 資料行，其值就會設定為 1，表示封裝可能要重新處理已經位於目標上的資料列。</span><span class="sxs-lookup"><span data-stu-id="49b99-140">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="49b99-141">TFEND (Trickle 摘要更新結束)</span><span class="sxs-lookup"><span data-stu-id="49b99-141">TFEND (Trickle-Feed Update Ended)</span></span>|<span data-ttu-id="49b99-142">這是一般 CDC 回合所預期的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-142">This is the state expected for regular CDC runs.</span></span> <span data-ttu-id="49b99-143">這種狀態表示上一個回合已順利完成，而且可以啟動具有新處理範圍的新回合。</span><span class="sxs-lookup"><span data-stu-id="49b99-143">It indicates that the previous run completed successfully and that a new run with a new processing range can be started.</span></span>|  
|<span data-ttu-id="49b99-144">TFSTART</span><span class="sxs-lookup"><span data-stu-id="49b99-144">TFSTART</span></span>|<span data-ttu-id="49b99-145">這是在 CDC 控制工作的 `GetProcessingRange` 作業呼叫之後，非初次執行 Trickle 摘要更新封裝時的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-145">This is the state on a non-initial run of the trickle feed update package, after the `GetProcessingRange` operation call to the CDC Control task.</span></span><br /><br /> <span data-ttu-id="49b99-146">這表示一般 CDC 回合已啟動，但卻沒有完成或者尚未徹底完成 (`MarkProcessedRange`)。</span><span class="sxs-lookup"><span data-stu-id="49b99-146">This indicates that a regular CDC run is started but has not finished or has not yet finished, cleanly (`MarkProcessedRange`).</span></span>|  
|<span data-ttu-id="49b99-147">TFREDO (重新處理 Trickle 摘要更新)</span><span class="sxs-lookup"><span data-stu-id="49b99-147">TFREDO (Reprocessing Trickle-Feed Updates)</span></span>|<span data-ttu-id="49b99-148">這是在 TFSTART 之後發生 `GetProcessingRange` 時的狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-148">This is the state on a `GetProcessingRange` that occurs after TFSTART.</span></span> <span data-ttu-id="49b99-149">這種狀態表示上一個回合並未順利完成。</span><span class="sxs-lookup"><span data-stu-id="49b99-149">This indicates that the previous run did not complete successfully.</span></span><br /><br /> <span data-ttu-id="49b99-150">如果使用了 __$reprocessing 資料行，其值就會設定為 1，表示封裝可能要重新處理已經位於目標上的資料列。</span><span class="sxs-lookup"><span data-stu-id="49b99-150">If using the __$reprocessing column, it is set to 1 to indicate that the package may be re-processing rows already at the target.</span></span>|  
|<span data-ttu-id="49b99-151">ERROR</span><span class="sxs-lookup"><span data-stu-id="49b99-151">ERROR</span></span>|<span data-ttu-id="49b99-152">CDC 群組處於 ERROR 狀態。</span><span class="sxs-lookup"><span data-stu-id="49b99-152">The CDC group is in an ERROR state.</span></span>|  
  
 <span data-ttu-id="49b99-153">以下是 CDC 狀態變數值的範例。</span><span class="sxs-lookup"><span data-stu-id="49b99-153">The following are examples of CDC state variable values.</span></span>  
  
-   <span data-ttu-id="49b99-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="49b99-154">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="49b99-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span><span class="sxs-lookup"><span data-stu-id="49b99-155">ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/</span></span>  
  
-   <span data-ttu-id="49b99-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span><span class="sxs-lookup"><span data-stu-id="49b99-156">TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/</span></span>  
  
-   <span data-ttu-id="49b99-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span><span class="sxs-lookup"><span data-stu-id="49b99-157">TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/</span></span>  
  
-   <span data-ttu-id="49b99-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span><span class="sxs-lookup"><span data-stu-id="49b99-158">TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/</span></span>  
  
### <a name="to-define-a-cdc-state-variable"></a><span data-ttu-id="49b99-159">若要定義 CDC 狀態變數</span><span class="sxs-lookup"><span data-stu-id="49b99-159">To define a CDC state variable</span></span>  
  
1.  <span data-ttu-id="49b99-160">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟有需要定義變數之 CDC 流程的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="49b99-160">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] package that has the CDC flow where you need to define the variable.</span></span>  
  
2.  <span data-ttu-id="49b99-161">按一下 **[封裝總管]** 索引標籤，並加入新的變數。</span><span class="sxs-lookup"><span data-stu-id="49b99-161">Click the **Package Explorer** tab, and add a new variable.</span></span>  
  
3.  <span data-ttu-id="49b99-162">為變數指定可辨識的名稱，做為狀態變數。</span><span class="sxs-lookup"><span data-stu-id="49b99-162">Give the variable a name that you can recognize as your state variable.</span></span>  
  
4.  <span data-ttu-id="49b99-163">為變數指定 **字串** 資料類型。</span><span class="sxs-lookup"><span data-stu-id="49b99-163">Give the variable a **String** data type.</span></span>  
  
 <span data-ttu-id="49b99-164">不要指定變數值做為其定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="49b99-164">Do not give the variable a value as part of its definition.</span></span> <span data-ttu-id="49b99-165">此值必須是由 CDC 控制工作所設定。</span><span class="sxs-lookup"><span data-stu-id="49b99-165">The value must be set by the CDC Control task.</span></span>  
  
 <span data-ttu-id="49b99-166">如果您打算將 CDC 控制工作與 **[自動狀態持續性]** 搭配使用，CDC 狀態變數將會從您指定的資料庫狀態資料表讀取，並在其值變更時更新回該相同的資料表。</span><span class="sxs-lookup"><span data-stu-id="49b99-166">If you plan to use the CDC Control task with **Automatic State Persistence**, the CDC State variable will be read from the database state table you specify and will be updated back to that same table when its value changes.</span></span> <span data-ttu-id="49b99-167">如需有關狀態變數的詳細資訊，請參閱＜ [CDC Control Task](../control-flow/cdc-control-task.md)＞和＜ [CDC Control Task Editor](../cdc-control-task-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="49b99-167">For more information about the State table, see [CDC Control Task](../control-flow/cdc-control-task.md)and [CDC Control Task Editor](../cdc-control-task-editor.md).</span></span>  
  
 <span data-ttu-id="49b99-168">如果您不打算將 CDC 控制工作與 [自動狀態持續性] 搭配使用，則必須從上次封裝執行時儲存其值的永續性儲存體中載入變數值，並在目前處理範圍已完成處理時將變數值寫回該永續性儲存體。</span><span class="sxs-lookup"><span data-stu-id="49b99-168">If you are not using the CDC Control task with Automatic State Persistence then you must load the variable value from persistent storage where its value was saved the last time the package ran and to write it back to the persistent storage when the processing of the current processing range was completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b99-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49b99-169">See Also</span></span>  
 <span data-ttu-id="49b99-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span><span class="sxs-lookup"><span data-stu-id="49b99-170">[CDC Control Task](../control-flow/cdc-control-task.md) </span></span>  
 [<span data-ttu-id="49b99-171">CDC 控制工作編輯器</span><span class="sxs-lookup"><span data-stu-id="49b99-171">CDC Control Task Editor</span></span>](../cdc-control-task-editor.md)  
  
  
