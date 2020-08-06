---
title: 指令碼工作範例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 920d2ee5cc2e64db1048d10522d9be644794e55b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701290"
---
# <a name="script-task-examples"></a><span data-ttu-id="d385b-102">指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="d385b-102">Script Task Examples</span></span>
  <span data-ttu-id="d385b-103">指令碼工作是多用途的工具，可用於封裝中以滿足 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所含的工作無法達成的幾乎任何需求。</span><span class="sxs-lookup"><span data-stu-id="d385b-103">The Script task is a multi-purpose tool that you can use in a package to fill almost any requirement that is not met by the tasks included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="d385b-104">本主題列出指令碼工作程式碼範例，以示範某些可用的功能。</span><span class="sxs-lookup"><span data-stu-id="d385b-104">This topic lists Script task code samples that demonstrate some of the available functionality.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d385b-105">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用這些指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="d385b-105">If you want to create tasks that you can more easily reuse across multiple packages, consider using the code in these Script task samples as the starting point for custom tasks.</span></span> <span data-ttu-id="d385b-106">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d385b-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d385b-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="d385b-107">In This Section</span></span>  
  
### <a name="example-topics"></a><span data-ttu-id="d385b-108">範例主題</span><span class="sxs-lookup"><span data-stu-id="d385b-108">Example Topics</span></span>  
 <span data-ttu-id="d385b-109">本章節包含程式碼範例，以示範各種可合併到 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 指令碼工作中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 類別：</span><span class="sxs-lookup"><span data-stu-id="d385b-109">This section contains code examples that demonstrate various uses of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that you can incorporate into an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task:</span></span>  
  
 [<span data-ttu-id="d385b-110">以指令碼工作偵測空的一般檔案</span><span class="sxs-lookup"><span data-stu-id="d385b-110">Detecting an Empty Flat File with the Script Task</span></span>](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 <span data-ttu-id="d385b-111">檢查一般檔案以判斷它是否包含資料列，並將結果儲存到變數中，以供在控制流程分支中使用。</span><span class="sxs-lookup"><span data-stu-id="d385b-111">Checks a flat file to determine whether it contains rows of data, and saves the result to a variable for use in control flow branching.</span></span>  
  
 [<span data-ttu-id="d385b-112">以指令碼工作收集 Foreach 迴圈的清單</span><span class="sxs-lookup"><span data-stu-id="d385b-112">Gathering a List for the ForEach Loop with the Script Task</span></span>](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 <span data-ttu-id="d385b-113">蒐集符合使用者指定的準則之檔案清單，並填入變數以供稍後由 Foreach From Variable 列舉值使用。</span><span class="sxs-lookup"><span data-stu-id="d385b-113">Gathers a list of files that meet user-specified criteria, and populates a variable for later use by the Foreach from Variable Enumerator.</span></span>  
  
 [<span data-ttu-id="d385b-114">以指令碼工作查詢 Active Directory</span><span class="sxs-lookup"><span data-stu-id="d385b-114">Querying the Active Directory with the Script Task</span></span>](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 <span data-ttu-id="d385b-115">使用 System.DirectoryServices 命名空間中的類別，根據 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 變數值，從 Active Directory 擷取使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="d385b-115">Retrieves user information from Active Directory based on the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, by using classes in the System.DirectoryServices namespace.</span></span>  
  
 [<span data-ttu-id="d385b-116">以指令碼工作監視效能計數器</span><span class="sxs-lookup"><span data-stu-id="d385b-116">Monitoring Performance Counters with the Script Task</span></span>](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 <span data-ttu-id="d385b-117">使用 System.Diagnostics 命名空間中的類別，建立可用以追蹤 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件執行進度的自訂效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d385b-117">Creates a custom performance counter that can be used to track the execution progress of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, by using classes in the System.Diagnostics namespace.</span></span>  
  
 [<span data-ttu-id="d385b-118">以指令碼工作處理影像</span><span class="sxs-lookup"><span data-stu-id="d385b-118">Working with Images with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 <span data-ttu-id="d385b-119">透過使用 System.Drawing 命名空間中的類別，將影像壓縮成 JPEG 格式，並從其中建立縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="d385b-119">Compresses images into the JPEG format and creates thumbnail images from them, by using classes in the System.Drawing namespace.</span></span>  
  
 [<span data-ttu-id="d385b-120">以指令碼工作尋找安裝的印表機</span><span class="sxs-lookup"><span data-stu-id="d385b-120">Finding Installed Printers with the Script Task</span></span>](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 <span data-ttu-id="d385b-121">透過使用 System.Drawing.Printing 命名空間中的類別，尋找支援特定紙張大小的已安裝印表機。</span><span class="sxs-lookup"><span data-stu-id="d385b-121">Locates installed printers that support a specific paper size, by using classes in the System.Drawing.Printing namespace.</span></span>  
  
 [<span data-ttu-id="d385b-122">以指令碼工作傳送 HTML 郵件訊息</span><span class="sxs-lookup"><span data-stu-id="d385b-122">Sending an HTML Mail Message with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 <span data-ttu-id="d385b-123">以 HTML 格式，而不是純文字格式傳送郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="d385b-123">Sends a mail message in HTML format instead of plain text format.</span></span>  
  
 [<span data-ttu-id="d385b-124">以指令碼工作處理 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="d385b-124">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 <span data-ttu-id="d385b-125">列出 Excel 檔案中的工作表，並檢查特定工作表是否存在。</span><span class="sxs-lookup"><span data-stu-id="d385b-125">Lists the worksheets in an Excel file and checks for the existence of a specific worksheet.</span></span>  
  
 [<span data-ttu-id="d385b-126">以指令碼工作傳送至遠端私用訊息佇列</span><span class="sxs-lookup"><span data-stu-id="d385b-126">Sending to a Remote Private Message Queue with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 <span data-ttu-id="d385b-127">將訊息傳送至遠端私用訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="d385b-127">Sends a message to a remote private message queue.</span></span>  
  
### <a name="other-examples"></a><span data-ttu-id="d385b-128">其他範例</span><span class="sxs-lookup"><span data-stu-id="d385b-128">Other Examples</span></span>  
 <span data-ttu-id="d385b-129">下列主題也包含與指令碼工作搭配使用的程式碼範例：</span><span class="sxs-lookup"><span data-stu-id="d385b-129">The following topics also contain code examples for use with the Script task:</span></span>  
  
 [<span data-ttu-id="d385b-130">在指令碼工作中使用變數</span><span class="sxs-lookup"><span data-stu-id="d385b-130">Using Variables in the Script Task</span></span>](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 <span data-ttu-id="d385b-131">根據可能超過另一個變數中所指定之上限的封裝變數值，詢問使用者是否確定封裝應該繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d385b-131">Asks the user for confirmation of whether the package should continue to run, based on the value of a package variable that may exceed the limit specified in another variable.</span></span>  
  
 [<span data-ttu-id="d385b-132">在指令碼工作中連線至資料來源</span><span class="sxs-lookup"><span data-stu-id="d385b-132">Connecting to Data Sources in the Script Task</span></span>](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="d385b-133">從定義在封裝中的連接管理員，擷取連接或是連接資訊。</span><span class="sxs-lookup"><span data-stu-id="d385b-133">Retrieves a connection or connection information from connection managers defined in the package.</span></span>  
  
 [<span data-ttu-id="d385b-134">在指令碼工作中引發事件</span><span class="sxs-lookup"><span data-stu-id="d385b-134">Raising Events in the Script Task</span></span>](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 <span data-ttu-id="d385b-135">根據伺服器上的網際網路連接狀態，引發錯誤、警告或是參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="d385b-135">Raises an error, a warning, or an informational message based on the status of the Internet connection on the server.</span></span>  
  
 [<span data-ttu-id="d385b-136">在指令碼工作中記錄</span><span class="sxs-lookup"><span data-stu-id="d385b-136">Logging in the Script Task</span></span>](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 <span data-ttu-id="d385b-137">將工作所處理的項目數目記錄到啟用的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="d385b-137">Logs the number of items processed by the task to enabled log providers.</span></span>  
  
<span data-ttu-id="d385b-138">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="d385b-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d385b-139">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="d385b-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d385b-140">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="d385b-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d385b-141">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d385b-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
