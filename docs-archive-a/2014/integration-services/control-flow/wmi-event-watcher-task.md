---
title: WMI 事件監看員工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be20624e5ccdf665e6274f647c342498e9c0f0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708514"
---
# <a name="wmi-event-watcher-task"></a><span data-ttu-id="06e90-102">WMI 事件監看員工作</span><span class="sxs-lookup"><span data-stu-id="06e90-102">WMI Event Watcher Task</span></span>
  <span data-ttu-id="06e90-103">「WMI 事件監看員」工作使用 Management Instrumentation 查詢語言 (WQL) 事件查詢來監看 Windows Management Instrumentation (WMI) 事件，以指定感興趣的事件。</span><span class="sxs-lookup"><span data-stu-id="06e90-103">The WMI Event Watcher task watches for a Windows Management Instrumentation (WMI) event using a Management Instrumentation Query Language (WQL) event query to specify events of interest.</span></span> <span data-ttu-id="06e90-104">您可將「WMI 事件監看員」工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="06e90-104">You can use the WMI Event Watcher task for the following purposes:</span></span>  
  
-   <span data-ttu-id="06e90-105">等待檔案已加入資料夾的通知，然後起始檔案的處理。</span><span class="sxs-lookup"><span data-stu-id="06e90-105">Wait for notification that files have been added to a folder and then initiate the processing of the file.</span></span>  
  
-   <span data-ttu-id="06e90-106">當伺服器的可用記憶體降至低於指定的百分比時，執行刪除檔案的封裝。</span><span class="sxs-lookup"><span data-stu-id="06e90-106">Run a package that deletes files when the available memory on a server drops lower than a specified percentage.</span></span>  
  
-   <span data-ttu-id="06e90-107">監看應用程式的安裝，然後執行使用此應用程式的封裝。</span><span class="sxs-lookup"><span data-stu-id="06e90-107">Watch for installation of an application, and then run a package that uses the application.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="06e90-108">包含讀取 WMI 資訊的工作。</span><span class="sxs-lookup"><span data-stu-id="06e90-108">includes a task that reads WMI information.</span></span>  
  
 <span data-ttu-id="06e90-109">如需有關這項工作的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="06e90-109">For more information about this task, click the following topic:</span></span>  
  
-   [<span data-ttu-id="06e90-110">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="06e90-110">WMI Data Reader Task</span></span>](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a><span data-ttu-id="06e90-111">WQL 查詢</span><span class="sxs-lookup"><span data-stu-id="06e90-111">WQL Queries</span></span>  
 <span data-ttu-id="06e90-112">WQL 是 SQL 用語，其包含的延伸模組可支援 WMI 事件通知和其他 WMI 特定功能。</span><span class="sxs-lookup"><span data-stu-id="06e90-112">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="06e90-113">如需有關 WQL 的詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553)中的 Windows Management Instrumentation 文件集。</span><span class="sxs-lookup"><span data-stu-id="06e90-113">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06e90-114">不同 Windows 版本的 WMI 類別也有所不同。</span><span class="sxs-lookup"><span data-stu-id="06e90-114">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="06e90-115">以下查詢監看 CPU 使用超過 40% 時發出的通知。</span><span class="sxs-lookup"><span data-stu-id="06e90-115">The following query watches for notification that the CPU use is more than 40 percent.</span></span>  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 <span data-ttu-id="06e90-116">以下查詢監看檔案加入資料夾後發出的通知。</span><span class="sxs-lookup"><span data-stu-id="06e90-116">The following query watches for notification that a file has been added to a folder.</span></span>  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a><span data-ttu-id="06e90-117">WMI 事件監看員工作上可用的自訂記錄訊息</span><span class="sxs-lookup"><span data-stu-id="06e90-117">Custom Logging Messages Available on the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="06e90-118">下表列出「WMI 事件監看員」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="06e90-118">The following table lists the custom log entries for the WMI Event Watcher task.</span></span> <span data-ttu-id="06e90-119">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="06e90-119">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="06e90-120">記錄項目</span><span class="sxs-lookup"><span data-stu-id="06e90-120">Log entry</span></span>|<span data-ttu-id="06e90-121">描述</span><span class="sxs-lookup"><span data-stu-id="06e90-121">Description</span></span>|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|<span data-ttu-id="06e90-122">指出發生了工作正在進行監視的事件。</span><span class="sxs-lookup"><span data-stu-id="06e90-122">Indicates that an event occurred that the task was monitoring.</span></span>|  
|`WMIEventWatcherTimedout`|<span data-ttu-id="06e90-123">指出工作已經逾時。</span><span class="sxs-lookup"><span data-stu-id="06e90-123">Indicates that the task timed out.</span></span>|  
|`WMIEventWatcherWatchingForWMIEvents`|<span data-ttu-id="06e90-124">指出工作已經開始執行 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="06e90-124">Indicates that the task began to execute the WQL query.</span></span> <span data-ttu-id="06e90-125">項目包含查詢。</span><span class="sxs-lookup"><span data-stu-id="06e90-125">The entry includes the query.</span></span>|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="06e90-126">WMI 事件監看員工作的組態</span><span class="sxs-lookup"><span data-stu-id="06e90-126">Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="06e90-127">您可以利用下列方式設定「WMI 資料讀取器」工作：</span><span class="sxs-lookup"><span data-stu-id="06e90-127">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="06e90-128">指定要使用的 WMI 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="06e90-128">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="06e90-129">指定 WQL 查詢的來源。</span><span class="sxs-lookup"><span data-stu-id="06e90-129">Specify the source of the WQL query.</span></span> <span data-ttu-id="06e90-130">來源可以在工作的外部，可以是一個變數或檔案，或者查詢可儲存於工作屬性內。</span><span class="sxs-lookup"><span data-stu-id="06e90-130">The source can be external to the task, a variable or a file, or the query can be stored in a task property.</span></span>  
  
-   <span data-ttu-id="06e90-131">指定發生 WMI 事件時工作採取的行動。</span><span class="sxs-lookup"><span data-stu-id="06e90-131">Specify the action that the task takes when the WMI event occurs.</span></span> <span data-ttu-id="06e90-132">您可以記錄事件通知和事件後的狀態，或者引發自訂 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 事件，以提供與 WMI 事件、通知及事件後狀態相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="06e90-132">You can log the event notification and the status after the event, or raise custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] events that provide information associated with the WMI event, the notification, and the status after the event.</span></span>  
  
-   <span data-ttu-id="06e90-133">定義工作回應事件的方式。</span><span class="sxs-lookup"><span data-stu-id="06e90-133">Define how the task responds to the event.</span></span> <span data-ttu-id="06e90-134">工作可以根據事件設定為成功或失敗，也可以讓工作只再次監看事件。</span><span class="sxs-lookup"><span data-stu-id="06e90-134">The task can be configured to succeed or fail, depending on the event, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="06e90-135">指定 WMI 查詢逾時後工作採取的行動。您可以記錄逾時及逾時後的狀態，或者引發一個自訂 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 事件，用來指示 WMI 事件逾時，並記錄逾時和逾時狀態。</span><span class="sxs-lookup"><span data-stu-id="06e90-135">Specify the action the task takes when the WMI query times out. You can log the time-out and the status after time-out, or raise a custom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] event, indicating that the WMI event timed out and logging the time-out and time-out status.</span></span>  
  
-   <span data-ttu-id="06e90-136">定義工作回應逾時的方式。工作可設定為成功或失敗，也可以讓工作只再次監看事件。</span><span class="sxs-lookup"><span data-stu-id="06e90-136">Define how the task responds to the time-out. The task can be configured to succeed or fail, or the task can just watch for the event again.</span></span>  
  
-   <span data-ttu-id="06e90-137">指定工作監看事件的次數。</span><span class="sxs-lookup"><span data-stu-id="06e90-137">Specify the number of times the task watches for the event.</span></span>  
  
-   <span data-ttu-id="06e90-138">指定逾時。</span><span class="sxs-lookup"><span data-stu-id="06e90-138">Specify the time-out.</span></span>  
  
 <span data-ttu-id="06e90-139">如果來源是一個檔案，則「WMI 事件監看員」工作會使用「檔案」連接管理員以連接到檔案。</span><span class="sxs-lookup"><span data-stu-id="06e90-139">If the source is a file, the WMI Event Watcher task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="06e90-140">如需相關資訊，請參閱 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="06e90-140">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="06e90-141">「WMI 事件監看員」工作使用 WMI 連接管理員連接到可從中讀取 WMI 資訊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="06e90-141">The WMI Event Watcher task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="06e90-142">如需相關資訊，請參閱 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="06e90-142">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
 <span data-ttu-id="06e90-143">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="06e90-143">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="06e90-144">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="06e90-144">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="06e90-145">WMI 事件監看員工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="06e90-145">WMI Event Watcher Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="06e90-146">WMI 事件監看員工作編輯器 &#40;WMI 選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="06e90-146">WMI Event Watcher Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="06e90-147">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="06e90-147">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="06e90-148">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="06e90-148">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="06e90-149">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="06e90-149">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a><span data-ttu-id="06e90-150">WMI 事件監看員工作的程式設計組態</span><span class="sxs-lookup"><span data-stu-id="06e90-150">Programmatic Configuration of the WMI Event Watcher Task</span></span>  
 <span data-ttu-id="06e90-151">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="06e90-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  
