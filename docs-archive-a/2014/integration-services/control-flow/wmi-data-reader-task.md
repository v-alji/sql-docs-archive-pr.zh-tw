---
title: WMI 資料讀取器工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d2f16a28e8b6c94c7275468dedb6d2dfec76d8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592797"
---
# <a name="wmi-data-reader-task"></a><span data-ttu-id="9ca70-102">WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="9ca70-102">WMI Data Reader Task</span></span>
  <span data-ttu-id="9ca70-103">「WMI 資料讀取器」工作使用「Windows Management Instrumentation (WMI) 查詢語言」執行查詢，該查詢語言會從 WMI 傳回有關電腦系統的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ca70-103">The WMI Data Reader task runs queries using the Windows Management Instrumentation (WMI) Query Language that returns information from WMI about a computer system.</span></span> <span data-ttu-id="9ca70-104">您可將「WMI 資料讀取器」工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="9ca70-104">You can use the WMI Data Reader task for the following purposes:</span></span>  
  
-   <span data-ttu-id="9ca70-105">查詢本機或遠端電腦上的 Windows 事件記錄檔，並將相關資訊寫入檔案或變數。</span><span class="sxs-lookup"><span data-stu-id="9ca70-105">Query the Windows event logs on a local or remote computer and write the information to a file or variable.</span></span>  
  
-   <span data-ttu-id="9ca70-106">取得硬體元件之存在、狀態或屬性的相關資訊，然後使用這些資訊判斷是否應該執行控制流程中的其他工作。</span><span class="sxs-lookup"><span data-stu-id="9ca70-106">Obtain information about the presence, state, or properties of hardware components, and then use this information to determine whether other tasks in the control flow should run.</span></span>  
  
-   <span data-ttu-id="9ca70-107">取得應用程式的清單，並判斷每個應用程式的安裝版本。</span><span class="sxs-lookup"><span data-stu-id="9ca70-107">Get a list of applications and determine what version of each application is installed.</span></span>  
  
 <span data-ttu-id="9ca70-108">您可以利用下列方式設定「WMI 資料讀取器」工作：</span><span class="sxs-lookup"><span data-stu-id="9ca70-108">You can configure the WMI Data Reader task in the following ways:</span></span>  
  
-   <span data-ttu-id="9ca70-109">指定要使用的 WMI 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="9ca70-109">Specify the WMI connection manager to use.</span></span>  
  
-   <span data-ttu-id="9ca70-110">指定 WQL 查詢的來源。</span><span class="sxs-lookup"><span data-stu-id="9ca70-110">Specify the source of the WQL query.</span></span> <span data-ttu-id="9ca70-111">查詢可以儲存在工作屬性中，也可以儲存在工作之外的變數或檔案中。</span><span class="sxs-lookup"><span data-stu-id="9ca70-111">The query can be stored in a task property, or the query can be stored outside the task, in a variable or a file.</span></span>  
  
-   <span data-ttu-id="9ca70-112">定義 WQL 查詢結果的格式。</span><span class="sxs-lookup"><span data-stu-id="9ca70-112">Define the format of the WQL query results.</span></span> <span data-ttu-id="9ca70-113">該工作支援資料表、屬性名稱/值配對或屬性值格式。</span><span class="sxs-lookup"><span data-stu-id="9ca70-113">The task supports a table, property name/value pair, or property value format.</span></span>  
  
-   <span data-ttu-id="9ca70-114">指定查詢的目的地。</span><span class="sxs-lookup"><span data-stu-id="9ca70-114">Specify the destination of the query.</span></span> <span data-ttu-id="9ca70-115">目的地可以是變數或檔案。</span><span class="sxs-lookup"><span data-stu-id="9ca70-115">The destination can be a variable or a file.</span></span>  
  
-   <span data-ttu-id="9ca70-116">指示是否覆寫、保留或附加查詢目的地。</span><span class="sxs-lookup"><span data-stu-id="9ca70-116">Indicate whether the query destination is overwritten, kept, or appended.</span></span>  
  
 <span data-ttu-id="9ca70-117">如果來源或目的地是一個檔案，則「WMI 資料讀取器」工作會使用「檔案」連接管理員連接到該檔案。</span><span class="sxs-lookup"><span data-stu-id="9ca70-117">If the source or destination is a file, the WMI Data Reader task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="9ca70-118">如需相關資訊，請參閱 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca70-118">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="9ca70-119">「WMI 資料讀取器」工作使用 WMI 連接管理員連接到可從中讀取 WMI 資訊的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ca70-119">The WMI Data Reader task uses a WMI connection manager to connect to the server from which it reads WMI information.</span></span> <span data-ttu-id="9ca70-120">如需相關資訊，請參閱 [WMI Connection Manager](../connection-manager/wmi-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca70-120">For more information, see [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="wql-query"></a><span data-ttu-id="9ca70-121">WQL 查詢</span><span class="sxs-lookup"><span data-stu-id="9ca70-121">WQL Query</span></span>  
 <span data-ttu-id="9ca70-122">WQL 是 SQL 用語，其包含的延伸模組可支援 WMI 事件通知和其他 WMI 特定功能。</span><span class="sxs-lookup"><span data-stu-id="9ca70-122">WQL is a dialect of SQL with extensions to support WMI event notification and other WMI-specific features.</span></span> <span data-ttu-id="9ca70-123">如需有關 WQL 的詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022)中的 Windows Management Instrumentation 文件集。</span><span class="sxs-lookup"><span data-stu-id="9ca70-123">For more information about WQL, see the Windows Management Instrumentation documentation in the [MSDN Library](https://go.microsoft.com/fwlink/?linkid=7022).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ca70-124">不同 Windows 版本的 WMI 類別也有所不同。</span><span class="sxs-lookup"><span data-stu-id="9ca70-124">WMI classes vary between versions of Windows.</span></span>  
  
 <span data-ttu-id="9ca70-125">下列 WQL 查詢會傳回「應用程式」記錄事件中的項目。</span><span class="sxs-lookup"><span data-stu-id="9ca70-125">The following WQL query returns entries in the Application log event.</span></span>  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 <span data-ttu-id="9ca70-126">以下 WQL 查詢傳回邏輯磁碟資訊。</span><span class="sxs-lookup"><span data-stu-id="9ca70-126">The following WQL query returns logical disk information.</span></span>  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 <span data-ttu-id="9ca70-127">以下 WQL 查詢將「快速修復工程」(QFE) 更新的清單傳回至作業系統。</span><span class="sxs-lookup"><span data-stu-id="9ca70-127">The following WQL query returns a list of the quick fix engineering (QFE) updates to the operating system.</span></span>  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a><span data-ttu-id="9ca70-128">WMI 資料讀取器工作上可用的自訂記錄訊息</span><span class="sxs-lookup"><span data-stu-id="9ca70-128">Custom Logging Messages Available on the WMI Data Reader Task</span></span>  
 <span data-ttu-id="9ca70-129">下表列出「WMI 資料讀取器」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="9ca70-129">The following table lists the custom log entries for the WMI Data Reader task.</span></span> <span data-ttu-id="9ca70-130">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="9ca70-130">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="9ca70-131">記錄項目</span><span class="sxs-lookup"><span data-stu-id="9ca70-131">Log entry</span></span>|<span data-ttu-id="9ca70-132">描述</span><span class="sxs-lookup"><span data-stu-id="9ca70-132">Description</span></span>|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|<span data-ttu-id="9ca70-133">指出工作已經開始讀取 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="9ca70-133">Indicates that the task began to read WMI data.</span></span>|  
|`WMIDataReaderOperation`|<span data-ttu-id="9ca70-134">報告工作已執行的 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="9ca70-134">Reports the WQL query that the task ran.</span></span>|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a><span data-ttu-id="9ca70-135">設定 WMI 資料讀取器工作</span><span class="sxs-lookup"><span data-stu-id="9ca70-135">Configuration of the WMI Data Reader Task</span></span>  
 <span data-ttu-id="9ca70-136">您可以程式設計方式或透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9ca70-136">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="9ca70-137">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="9ca70-137">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="9ca70-138">WMI 資料讀取器工作編輯器 &#40;WMI 選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="9ca70-138">WMI Data Reader Task Editor &#40;WMI Options Page&#41;</span></span>](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [<span data-ttu-id="9ca70-139">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="9ca70-139">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="9ca70-140">如需有關如何以程式設計方式設定這些屬性的詳細資訊，請按以下主題：</span><span class="sxs-lookup"><span data-stu-id="9ca70-140">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="9ca70-141">相關工作</span><span class="sxs-lookup"><span data-stu-id="9ca70-141">Related Tasks</span></span>  
 <span data-ttu-id="9ca70-142">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="9ca70-142">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="9ca70-143">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="9ca70-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ca70-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ca70-144">See Also</span></span>  
 <span data-ttu-id="9ca70-145">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="9ca70-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="9ca70-146">控制流程</span><span class="sxs-lookup"><span data-stu-id="9ca70-146">Control Flow</span></span>](control-flow.md)  
  
  
