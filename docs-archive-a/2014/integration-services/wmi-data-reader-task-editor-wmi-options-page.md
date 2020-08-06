---
title: Wmi 資料讀取器工作編輯器 (WMI 選項頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cfb28e7f8f352f708085bf664757391a05869752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599553"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a><span data-ttu-id="d4804-102">WMI 資料讀取器工作編輯器 (WMI 選項頁面)</span><span class="sxs-lookup"><span data-stu-id="d4804-102">WMI Data Reader Task Editor (WMI Options Page)</span></span>
  <span data-ttu-id="d4804-103">使用 [WMI 資料讀取器工作編輯器]  對話方塊的 [WMI 選項]  頁面，來指定 Windows Management Instrumentation 查詢語言 (WQL) 查詢的來源和查詢結果的目的地。</span><span class="sxs-lookup"><span data-stu-id="d4804-103">Use the **WMI Options** page of the **WMI Data Reader Task Editor** dialog box to specify the source of the Windows Management Instrumentation Query Language (WQL) query and the destination of the query result.</span></span>  
  
 <span data-ttu-id="d4804-104">若要了解這個工作，請參閱＜ [WMI Data Reader Task](control-flow/wmi-data-reader-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d4804-104">To learn about this task, see [WMI Data Reader Task](control-flow/wmi-data-reader-task.md).</span></span> <span data-ttu-id="d4804-105">如需 WMI 查詢語言 (WQL) 的詳細資訊，請參閱 MSDN Library 中的 Windows Management Instrumentation 主題 [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045)(使用 WQL 查詢)。</span><span class="sxs-lookup"><span data-stu-id="d4804-105">For more information about WMI Query Language (WQL), see the Windows Management Instrumentation topic, [Querying with WQL](https://go.microsoft.com/fwlink/?LinkId=79045), in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="d4804-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="d4804-106">Static Options</span></span>  
 <span data-ttu-id="d4804-107">**WMIConnectionName**</span><span class="sxs-lookup"><span data-stu-id="d4804-107">**WMIConnectionName**</span></span>  
 <span data-ttu-id="d4804-108">在清單中選取 WMI 連線管理員，或按一下 \<**New WMI Connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d4804-108">Select a WMI connection manager in the list, or click \<**New WMI Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d4804-109">**相關主題：** [WMI 連線管理員](connection-manager/wmi-connection-manager.md)、[WMI 連線管理員編輯器](../../2014/integration-services/wmi-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d4804-109">**Related Topics:** [WMI Connection Manager](connection-manager/wmi-connection-manager.md), [WMI Connection Manager Editor](../../2014/integration-services/wmi-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="d4804-110">**WQLQuerySourceType**</span><span class="sxs-lookup"><span data-stu-id="d4804-110">**WQLQuerySourceType**</span></span>  
 <span data-ttu-id="d4804-111">選取工作執行之 WQL 查詢的來源類型。</span><span class="sxs-lookup"><span data-stu-id="d4804-111">Select the source type of the WQL query that the task runs.</span></span> <span data-ttu-id="d4804-112">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="d4804-112">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d4804-113">值</span><span class="sxs-lookup"><span data-stu-id="d4804-113">Value</span></span>|<span data-ttu-id="d4804-114">描述</span><span class="sxs-lookup"><span data-stu-id="d4804-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4804-115">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="d4804-115">**Direct input**</span></span>|<span data-ttu-id="d4804-116">設定 WQL 查詢的來源。</span><span class="sxs-lookup"><span data-stu-id="d4804-116">Set the source to a WQL query.</span></span> <span data-ttu-id="d4804-117">選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="d4804-117">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="d4804-118">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="d4804-118">**File connection**</span></span>|<span data-ttu-id="d4804-119">選取包含 WQL 查詢的檔案。</span><span class="sxs-lookup"><span data-stu-id="d4804-119">Select a file that contains the WQL query.</span></span> <span data-ttu-id="d4804-120">選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="d4804-120">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
|<span data-ttu-id="d4804-121">**變數**</span><span class="sxs-lookup"><span data-stu-id="d4804-121">**Variable**</span></span>|<span data-ttu-id="d4804-122">將來源設定為定義 WQL 查詢的變數。</span><span class="sxs-lookup"><span data-stu-id="d4804-122">Set the source to a variable that defines the WQL query.</span></span> <span data-ttu-id="d4804-123">選取這個值就會顯示 **[WQLQuerySourceType]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="d4804-123">Selecting this value displays the dynamic option **WQLQuerySourceType**.</span></span>|  
  
 <span data-ttu-id="d4804-124">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="d4804-124">**OutputType**</span></span>  
 <span data-ttu-id="d4804-125">指定輸出應為資料表、屬性值或屬性名稱和值。</span><span class="sxs-lookup"><span data-stu-id="d4804-125">Specify whether the output should be a data table, property value, or property name and value.</span></span>  
  
 <span data-ttu-id="d4804-126">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="d4804-126">**OverwriteDestination**</span></span>  
 <span data-ttu-id="d4804-127">指定是要保留、覆寫還是附加至目的地檔案或變數中的原始資料。</span><span class="sxs-lookup"><span data-stu-id="d4804-127">Specifies whether to keep, overwrite, or append to the original data in the destination file or variable.</span></span>  
  
 <span data-ttu-id="d4804-128">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="d4804-128">**DestinationType**</span></span>  
 <span data-ttu-id="d4804-129">選取此工作執行之 WQL 查詢的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="d4804-129">Select the destination type of the WQL query that the task runs.</span></span> <span data-ttu-id="d4804-130">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="d4804-130">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="d4804-131">值</span><span class="sxs-lookup"><span data-stu-id="d4804-131">Value</span></span>|<span data-ttu-id="d4804-132">描述</span><span class="sxs-lookup"><span data-stu-id="d4804-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4804-133">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="d4804-133">**File connection**</span></span>|<span data-ttu-id="d4804-134">選取檔案以儲存 WQL 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="d4804-134">Select a file to save the results of the WQL query in.</span></span> <span data-ttu-id="d4804-135">選取此值會顯示動態選項 **[DestinationType]** 。</span><span class="sxs-lookup"><span data-stu-id="d4804-135">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
|<span data-ttu-id="d4804-136">**變數**</span><span class="sxs-lookup"><span data-stu-id="d4804-136">**Variable**</span></span>|<span data-ttu-id="d4804-137">設定變數以儲存 WQL 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="d4804-137">Set the variable to store the results of the WQL query in.</span></span> <span data-ttu-id="d4804-138">選取此值會顯示動態選項 **[DestinationType]** 。</span><span class="sxs-lookup"><span data-stu-id="d4804-138">Selecting this value displays the dynamic option, **DestinationType**.</span></span>|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a><span data-ttu-id="d4804-139">WQLQuerySourceType 動態選項</span><span class="sxs-lookup"><span data-stu-id="d4804-139">WQLQuerySourceType Dynamic Options</span></span>  
  
### <a name="wqlquerysourcetype--direct-input"></a><span data-ttu-id="d4804-140">WQLQuerySourceType = 直接輸入</span><span class="sxs-lookup"><span data-stu-id="d4804-140">WQLQuerySourceType = Direct input</span></span>  
 <span data-ttu-id="d4804-141">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="d4804-141">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d4804-142">提供查詢，或按一下省略符號 (...)，然後使用 [WQL 查詢]  對話方塊輸入查詢。</span><span class="sxs-lookup"><span data-stu-id="d4804-142">Provide a query, or click the ellipsis (...) and enter a query using the **WQL Query** dialog box.</span></span>  
  
### <a name="wqlquerysourcetype--file-connection"></a><span data-ttu-id="d4804-143">WQLQuerySourceType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="d4804-143">WQLQuerySourceType = File connection</span></span>  
 <span data-ttu-id="d4804-144">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="d4804-144">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d4804-145">在清單中選取檔案連線管理員，或按一下 \<**New connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d4804-145">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d4804-146">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d4804-146">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="wqlquerysourcetype--variable"></a><span data-ttu-id="d4804-147">WQLQuerySourceType = 變數</span><span class="sxs-lookup"><span data-stu-id="d4804-147">WQLQuerySourceType = Variable</span></span>  
 <span data-ttu-id="d4804-148">**WQLQuerySource**</span><span class="sxs-lookup"><span data-stu-id="d4804-148">**WQLQuerySource**</span></span>  
 <span data-ttu-id="d4804-149">在清單中選取變數，或按一下 \<**New variable...**> 來建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="d4804-149">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d4804-150">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d4804-150">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="destinationtype-dynamic-options"></a><span data-ttu-id="d4804-151">DestinationType 動態選項</span><span class="sxs-lookup"><span data-stu-id="d4804-151">DestinationType Dynamic Options</span></span>  
  
### <a name="destinationtype--file-connection"></a><span data-ttu-id="d4804-152">DestinationType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="d4804-152">DestinationType = File connection</span></span>  
 <span data-ttu-id="d4804-153">**目的地**</span><span class="sxs-lookup"><span data-stu-id="d4804-153">**Destination**</span></span>  
 <span data-ttu-id="d4804-154">在清單中選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="d4804-154">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="d4804-155">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="d4804-155">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="destinationtype--variable"></a><span data-ttu-id="d4804-156">DestinationType = 變數</span><span class="sxs-lookup"><span data-stu-id="d4804-156">DestinationType = Variable</span></span>  
 <span data-ttu-id="d4804-157">**目的地**</span><span class="sxs-lookup"><span data-stu-id="d4804-157">**Destination**</span></span>  
 <span data-ttu-id="d4804-158">在清單中選取變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="d4804-158">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="d4804-159">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="d4804-159">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4804-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4804-160">See Also</span></span>  
 <span data-ttu-id="d4804-161">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d4804-161">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d4804-162">[WMI 資料讀取器工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d4804-162">[WMI Data Reader Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d4804-163">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="d4804-163">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="d4804-164">WMI 事件監看員工作</span><span class="sxs-lookup"><span data-stu-id="d4804-164">WMI Event Watcher Task</span></span>](control-flow/wmi-event-watcher-task.md)  
  
  
