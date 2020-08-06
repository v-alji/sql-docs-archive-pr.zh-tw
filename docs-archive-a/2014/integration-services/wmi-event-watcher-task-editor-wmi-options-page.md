---
title: Wmi 事件監看員工作編輯器 (WMI 選項頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7d95501f6442df3723261c970c7a90f48cbdc87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703081"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a><span data-ttu-id="c935d-102">WMI 事件監看員工作編輯器 (WMI 選項頁面)</span><span class="sxs-lookup"><span data-stu-id="c935d-102">WMI Event Watcher Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="c935d-103">使用 [WMI 事件監看員工作編輯器]  對話方塊的 [WMI 選項]  頁面，即可指定 Windows Management Instrumentation 查詢語言 (WQL) 查詢的來源，以及 WMI 事件監看員工作如何回應 Microsoft Windows Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="c935d-103">Use the **WMI Options** page of the **WMI Event Watcher Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and how the WMI Event Watcher task responds to Microsoft Windows Instrumentation (WMI) events.</span></span>  
  
 <span data-ttu-id="c935d-104">若要了解這項工作，請參閱 [WMI 事件監看員工作](control-flow/wmi-event-watcher-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c935d-104">To learn about this task, see [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md).</span></span> <span data-ttu-id="c935d-105">如需 WMI 查詢語言 (WQL) 的詳細資訊，請參閱 MSDN Library 中的 Windows Management Instrumentation 主題 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(使用 WQL 查詢)。</span><span class="sxs-lookup"><span data-stu-id="c935d-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="c935d-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="c935d-106">Static Options</span></span>  
 <span data-ttu-id="c935d-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="c935d-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="c935d-108">在清單中選取 WMI 連線管理員，或按一下 \<**New WMI Connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c935d-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="c935d-109">**相關主題：** [WMI 連線管理員](connection-manager/wmi-connection-manager.md)、[WMI 連線管理員編輯器](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="c935d-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="c935d-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="c935d-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="c935d-111">選取工作執行之 WQL 查詢的來源類型。</span><span class="sxs-lookup"><span data-stu-id="c935d-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="c935d-112">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="c935d-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="c935d-113">值</span><span class="sxs-lookup"><span data-stu-id="c935d-113">Value</span></span>|<span data-ttu-id="c935d-114">描述</span><span class="sxs-lookup"><span data-stu-id="c935d-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c935d-115">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="c935d-115">**Direct input**</span></span>|<span data-ttu-id="c935d-116">設定 WQL 查詢的來源。</span><span class="sxs-lookup"><span data-stu-id="c935d-116">Set the source to a WQL query.</span></span> <span data-ttu-id="c935d-117">選取此值會顯示動態選項 [WQLQuerySource]  。</span><span class="sxs-lookup"><span data-stu-id="c935d-117">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="c935d-118">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="c935d-118">**File connection**</span></span>|<span data-ttu-id="c935d-119">選取包含 WQL 查詢的檔案。</span><span class="sxs-lookup"><span data-stu-id="c935d-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="c935d-120">選取此值會顯示動態選項 [WQLQuerySource]  。</span><span class="sxs-lookup"><span data-stu-id="c935d-120">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
|<span data-ttu-id="c935d-121">**變數**</span><span class="sxs-lookup"><span data-stu-id="c935d-121">**Variable**</span></span>|<span data-ttu-id="c935d-122">將來源設定為定義 WQL 查詢的變數。</span><span class="sxs-lookup"><span data-stu-id="c935d-122">Set the source to a variable that defines WQL query.</span></span> <span data-ttu-id="c935d-123">選取此值會顯示動態選項 [WQLQuerySource]  。</span><span class="sxs-lookup"><span data-stu-id="c935d-123">Selecting this value displays the dynamic option, **WQLQuerySource**.</span></span>|  
  
 <span data-ttu-id="c935d-124">**ActionAtEvent**</span><span class="sxs-lookup"><span data-stu-id="c935d-124">**ActionAtEvent**</span></span>  
 <span data-ttu-id="c935d-125">指定 WMI 事件是否記錄事件並起始 [!INCLUDE[ssIS](../includes/ssis-md.md)] 動作，或僅記錄事件。</span><span class="sxs-lookup"><span data-stu-id="c935d-125">Specify whether the WMI event logs the event and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] action, or only logs the event.</span></span>  
  
 <span data-ttu-id="c935d-126">**AfterEvent**</span><span class="sxs-lookup"><span data-stu-id="c935d-126">**AfterEvent**</span></span>  
 <span data-ttu-id="c935d-127">指定工作接收到 WMI 事件之後成功或失敗，或是工作會繼續監看事件再次發生。</span><span class="sxs-lookup"><span data-stu-id="c935d-127">Specify whether the task succeeds or fails after it receives the WMI event, or if the task continues watching for the event to occur again.</span></span>  
  
 <span data-ttu-id="c935d-128">**ActionAtTimeout**</span><span class="sxs-lookup"><span data-stu-id="c935d-128">**ActionAtTimeout**</span></span>  
 <span data-ttu-id="c935d-129">指定工作是否記錄 WMI 查詢逾時並起始 [!INCLUDE[ssIS](../includes/ssis-md.md)] 事件作為回應，或僅記錄逾時。</span><span class="sxs-lookup"><span data-stu-id="c935d-129">Specify whether the task logs a WMI query time-out and initiates an [!INCLUDE[ssIS](../includes/ssis-md.md)] event in response, or only logs the time-out.</span></span>  
  
 <span data-ttu-id="c935d-130">**AfterTimeout**</span><span class="sxs-lookup"><span data-stu-id="c935d-130">**AfterTimeout**</span></span>  
 <span data-ttu-id="c935d-131">指定工作回應逾時成功或失敗，或是工作會繼續監看另一個逾時再次發生。</span><span class="sxs-lookup"><span data-stu-id="c935d-131">Specify whether the task succeeds or fails in response to a time-out, or if the task continues watching for another time-out to recur.</span></span>  
  
 <span data-ttu-id="c935d-132">**NumberOfEvents**</span><span class="sxs-lookup"><span data-stu-id="c935d-132">**NumberOfEvents**</span></span>  
 <span data-ttu-id="c935d-133">指定要監看的事件數目。</span><span class="sxs-lookup"><span data-stu-id="c935d-133">Specify the number of events to watch for.</span></span>  
  
 <span data-ttu-id="c935d-134">**逾時**</span><span class="sxs-lookup"><span data-stu-id="c935d-134">**Timeout**</span></span>  
 <span data-ttu-id="c935d-135">指定要等候事件發生的秒數。</span><span class="sxs-lookup"><span data-stu-id="c935d-135">Specify the number of seconds to wait for the event to occur.</span></span> <span data-ttu-id="c935d-136">值為 0 表示沒有逾時在作用中。</span><span class="sxs-lookup"><span data-stu-id="c935d-136">A value of 0 means that no time-out is in effect.</span></span>  
  
## <a name="wqlquerysource-dynamic-options"></a><span data-ttu-id="c935d-137">WQLQuerySource 動態選項</span><span class="sxs-lookup"><span data-stu-id="c935d-137">WQLQuerySource Dynamic Options</span></span>  
  
### <a name="wqlquerysource--direct-input"></a><span data-ttu-id="c935d-138">WQLQuerySource = 直接輸入</span><span class="sxs-lookup"><span data-stu-id="c935d-138">WQLQuerySource = Direct input</span></span>  
 <span data-ttu-id="c935d-139">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="c935d-139">**WQLQuerySource**</span></span>  
 <span data-ttu-id="c935d-140">提供查詢，或按一下省略符號按鈕 (...)，然後使用 [WQL 查詢]  對話方塊輸入查詢。</span><span class="sxs-lookup"><span data-stu-id="c935d-140">Provide a query, or click the ellipsis button (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysource--file-connection"></a><span data-ttu-id="c935d-141">WQLQuerySource = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="c935d-141">WQLQuerySource = File connection</span></span>  
 <span data-ttu-id="c935d-142">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="c935d-142">**WQLQuerySource**</span></span>  
 <span data-ttu-id="c935d-143">在清單中選取檔案連線管理員，或按一下 \<**New connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c935d-143">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="c935d-144">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="c935d-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysource--variable"></a><span data-ttu-id="c935d-145">WQLQuerySource = 變數</span><span class="sxs-lookup"><span data-stu-id="c935d-145">WQLQuerySource = Variable</span></span>  
 <span data-ttu-id="c935d-146">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="c935d-146">**WQLQuerySource**</span></span>  
 <span data-ttu-id="c935d-147">在清單中選取變數，或按一下 \<**New variable...**> 來建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="c935d-147">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="c935d-148">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="c935d-148">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c935d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c935d-149">See Also</span></span>  
 <span data-ttu-id="c935d-150">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c935d-150">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="c935d-151">[[WMI 事件監看員工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="c935d-151">[WMI Event Watcher Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="c935d-152">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="c935d-152">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="c935d-153">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="c935d-153">WMI Data Reader Task</span></span>](control-flow/wmi-data-reader-task.md)  
  
  
