---
title: 執行處理工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.f1
helpviewer_keywords:
- Execute Process task [Integration Services]
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c0db683d7c900e2554b3b856cbf68f7cfb1ca087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595222"
---
# <a name="execute-process-task"></a><span data-ttu-id="abfb3-102">執行處理工作</span><span class="sxs-lookup"><span data-stu-id="abfb3-102">Execute Process Task</span></span>
  <span data-ttu-id="abfb3-103">「執行處理」工作會隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件工作流程來執行應用程式或批次檔。</span><span class="sxs-lookup"><span data-stu-id="abfb3-103">The Execute Process task runs an application or batch file as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="abfb3-104">雖然可以使用「執行處理」工作來開啟任何標準應用程式，例如 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 或 [!INCLUDE[ofprword](../../includes/ofprword-md.md)]，但通常您會使用它來執行處理資料來源的商業應用程式或批次檔。</span><span class="sxs-lookup"><span data-stu-id="abfb3-104">Although you can use the Execute Process task to open any standard application, such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or [!INCLUDE[ofprword](../../includes/ofprword-md.md)], you typically use it to run business applications or batch files that work against a data source.</span></span> <span data-ttu-id="abfb3-105">例如，您可以使用「執行處理」工作展開壓縮的文字檔。</span><span class="sxs-lookup"><span data-stu-id="abfb3-105">For example, you can use the Execute Process task to expand a compressed text file.</span></span> <span data-ttu-id="abfb3-106">然後封裝就可以使用文字檔做為封裝中資料流程的資料來源。</span><span class="sxs-lookup"><span data-stu-id="abfb3-106">Then the package can use the text file as a data source for the data flow in the package.</span></span> <span data-ttu-id="abfb3-107">另一項範例為：您可以使用「執行處理」工作來執行產生每日銷售報表的自訂 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="abfb3-107">As another example, you can use the Execute Process task to run a custom [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] application that generates a daily sales report.</span></span> <span data-ttu-id="abfb3-108">接著，您就可將報告附加至「傳送郵件」工作，並將報告轉寄到通訊群組清單。</span><span class="sxs-lookup"><span data-stu-id="abfb3-108">Then you can attach the report to a Send Mail task and forward the report to a distribution list.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="abfb3-109">包含執行工作流程作業的其他工作，例如執行封裝。</span><span class="sxs-lookup"><span data-stu-id="abfb3-109">includes other tasks that perform workflow operations such as executing packages.</span></span> <span data-ttu-id="abfb3-110">如需詳細資訊，請參閱 [執行封裝工作](execute-package-task.md)</span><span class="sxs-lookup"><span data-stu-id="abfb3-110">For more information, see [Execute Package Task](execute-package-task.md)</span></span>  
  
## <a name="custom-log-entries-available-on-the-execute-process-task"></a><span data-ttu-id="abfb3-111">執行處理工作上可用的自訂記錄項目</span><span class="sxs-lookup"><span data-stu-id="abfb3-111">Custom Log Entries Available on the Execute Process Task</span></span>  
 <span data-ttu-id="abfb3-112">下表列出「執行處理」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="abfb3-112">The following table lists the custom log entries for the Execute Process task.</span></span> <span data-ttu-id="abfb3-113">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="abfb3-113">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="abfb3-114">記錄項目</span><span class="sxs-lookup"><span data-stu-id="abfb3-114">Log entry</span></span>|<span data-ttu-id="abfb3-115">描述</span><span class="sxs-lookup"><span data-stu-id="abfb3-115">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|<span data-ttu-id="abfb3-116">提供將工作設定為執行之相關的程序資訊。</span><span class="sxs-lookup"><span data-stu-id="abfb3-116">Provides information about the process that the task is configured to run.</span></span><br /><br /> <span data-ttu-id="abfb3-117">將會寫入兩個記錄項目。</span><span class="sxs-lookup"><span data-stu-id="abfb3-117">Two log entries are written.</span></span> <span data-ttu-id="abfb3-118">其中一個包含工作所執行之可執行檔的名稱和位置的相關資訊，另一個項目則記錄可執行檔的結束。</span><span class="sxs-lookup"><span data-stu-id="abfb3-118">One contains information about the name and location of the executable that the task runs, and the other entry records the exit from the executable.</span></span>|  
|`ExecuteProcessVariableRouting`|<span data-ttu-id="abfb3-119">提供有關哪些變數會傳到可執行檔之輸入和輸出的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="abfb3-119">Provides information about which variables are routed to the input and outputs of the executable.</span></span> <span data-ttu-id="abfb3-120">將會寫入 stdin (輸入)、stdout (輸出) 和 stderr (錯誤輸出) 的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="abfb3-120">Log entries are written for stdin (the input), stdout (the output), and stderr (the error output).</span></span>|  
  
## <a name="configuration-of-the-execute-process-task"></a><span data-ttu-id="abfb3-121">執行處理工作的組態</span><span class="sxs-lookup"><span data-stu-id="abfb3-121">Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="abfb3-122">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="abfb3-122">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="abfb3-123">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="abfb3-123">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="abfb3-124">執行處理工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="abfb3-124">Execute Process Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="abfb3-125">執行處理工作編輯器 &#40;處理頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="abfb3-125">Execute Process Task Editor &#40;Process Page&#41;</span></span>](../execute-process-task-editor-process-page.md)  
  
 <span data-ttu-id="abfb3-126">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="abfb3-126">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="abfb3-127">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="abfb3-127">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="property-settings"></a><span data-ttu-id="abfb3-128">屬性設定</span><span class="sxs-lookup"><span data-stu-id="abfb3-128">Property Settings</span></span>  
 <span data-ttu-id="abfb3-129">當「執行處理」工作執行自訂應用程式時，此工作會透過下列一個或兩個方法提供輸入給應用程式：</span><span class="sxs-lookup"><span data-stu-id="abfb3-129">When the Execute Process task runs a custom application, the task provides input to the application through one or both of the following methods:</span></span>  
  
-   <span data-ttu-id="abfb3-130">您在 [StandardInputVariable]  屬性設定中指定的變數。</span><span class="sxs-lookup"><span data-stu-id="abfb3-130">A variable that you specify in the **StandardInputVariable** property setting.</span></span> <span data-ttu-id="abfb3-131">如需變數的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="abfb3-131">For more information about variables, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
-   <span data-ttu-id="abfb3-132">您在 **Arguments** 屬性設定中指定的引數。</span><span class="sxs-lookup"><span data-stu-id="abfb3-132">An argument that you specify in the **Arguments** property setting.</span></span> <span data-ttu-id="abfb3-133">(例如，如果工作使用 Word 開啟文件，則引數可能命名為 .doc 檔)。</span><span class="sxs-lookup"><span data-stu-id="abfb3-133">(For example, if the task opens a document in Word, the argument can name the .doc file.)</span></span>  
  
 <span data-ttu-id="abfb3-134">若要在一個「執行處理」工作中將多個引數傳遞到自訂應用程式，請使用空格來分隔引數。</span><span class="sxs-lookup"><span data-stu-id="abfb3-134">To pass multiple arguments to a custom application in one Execute Process task, use spaces to delimit the arguments.</span></span> <span data-ttu-id="abfb3-135">引數不得包含空格，否則此工作將無法執行。</span><span class="sxs-lookup"><span data-stu-id="abfb3-135">An argument cannot include a space; otherwise, the task will not run.</span></span> <span data-ttu-id="abfb3-136">您可以使用運算式以引數的方式傳遞變數值。</span><span class="sxs-lookup"><span data-stu-id="abfb3-136">You can use an expression to pass a variable value as the argument.</span></span> <span data-ttu-id="abfb3-137">在下列範例中，運算式會以引數的方式傳遞兩個變數值，並使用空格來分隔引數：</span><span class="sxs-lookup"><span data-stu-id="abfb3-137">In the following example, the expression passes two variable values as arguments, and uses a space to delimit the arguments:</span></span>  
  
 `@variable1 + " " + @variable2`  
  
 <span data-ttu-id="abfb3-138">您可以使用運算式來設定各種「執行處理」工作屬性。</span><span class="sxs-lookup"><span data-stu-id="abfb3-138">You can use an expression to set various Execute Process task properties.</span></span>  
  
 <span data-ttu-id="abfb3-139">當您使用**StandardInputVariable**屬性設定「執行處理」工作來提供輸入時，請 `Console.ReadLine` 從應用程式呼叫方法來讀取輸入。</span><span class="sxs-lookup"><span data-stu-id="abfb3-139">When you use the **StandardInputVariable** property to configure the Execute Process task to provide input, call the `Console.ReadLine` method from the application to read the input.</span></span> <span data-ttu-id="abfb3-140">如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別庫中的 [Console.ReadLine 方法](https://go.microsoft.com/fwlink/?LinkId=129201)主題。</span><span class="sxs-lookup"><span data-stu-id="abfb3-140">For more information, see [Console.ReadLine Method](https://go.microsoft.com/fwlink/?LinkId=129201)the topic, , in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Class Library.</span></span>  
  
 <span data-ttu-id="abfb3-141">當您使用 **Arguments** 屬性設定「執行處理」工作來提供輸入時，請執行下列其中一個步驟來取得引數：</span><span class="sxs-lookup"><span data-stu-id="abfb3-141">When you use the **Arguments** property to configure the Execute Process task to provide input, do one of the following steps to obtain the arguments:</span></span>  
  
-   <span data-ttu-id="abfb3-142">如果您使用 Microsoft Visual Basic 撰寫應用程式，請設定 `My.Application.CommandLineArgs` 屬性。</span><span class="sxs-lookup"><span data-stu-id="abfb3-142">If you use Microsoft Visual Basic to write the application, set the `My.Application.CommandLineArgs` property.</span></span> <span data-ttu-id="abfb3-143">下列範例設定 `My.Application.CommandLineArgs` 屬性來擷取兩個引數：</span><span class="sxs-lookup"><span data-stu-id="abfb3-143">The following example sets the `My.Application.CommandLineArgs` property is to retrieve two arguments:</span></span>  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     <span data-ttu-id="abfb3-144">如需詳細資訊，請參閱 [參考中的](https://go.microsoft.com/fwlink/?LinkId=129200)My.Application.CommandLineArgs 屬性 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 主題。</span><span class="sxs-lookup"><span data-stu-id="abfb3-144">For more information, see the topic, [My.Application.CommandLineArgs Property](https://go.microsoft.com/fwlink/?LinkId=129200), in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] reference.</span></span>  
  
-   <span data-ttu-id="abfb3-145">如果您使用 Microsoft Visual C# 撰寫應用程式，請使用 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="abfb3-145">If you use Microsoft Visual C# to write the applicate, use the `Main` method.</span></span>  
  
     <span data-ttu-id="abfb3-146">如需詳細資訊，請參閱《C# 程式設計手冊》中的 [命令列引數 (C# 程式設計手冊)](https://go.microsoft.com/fwlink/?LinkId=129406)主題。</span><span class="sxs-lookup"><span data-stu-id="abfb3-146">For more information, see the topic, [Command-Line Arguments (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=129406), in the C# Programming Guide.</span></span>  
  
 <span data-ttu-id="abfb3-147">「執行處理」工作也包含 **StandardOutputVariable** 和 **StandardErrorVariable** 屬性，分別用來指定使用應用程式的標準輸出和錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="abfb3-147">The Execute Process task also includes the **StandardOutputVariable** and **StandardErrorVariable** properties for specifying the variables that consume the standard output and error output of the application, respectively.</span></span>  
  
 <span data-ttu-id="abfb3-148">此外，您可以設定讓「執行處理」工作指定工作目錄、逾時期限，或表示可執行檔成功執行的值。</span><span class="sxs-lookup"><span data-stu-id="abfb3-148">Additionally, you can configure the Execute Process task to specify a working directory, a time-out period, or a value to indicate that the executable ran successfully.</span></span> <span data-ttu-id="abfb3-149">如果可執行檔的傳回碼與表示成功的值不符，或在指定的位置找不到可執行檔，亦可將此工作設定為失敗。</span><span class="sxs-lookup"><span data-stu-id="abfb3-149">The task can also be configured to fail if the return code of the executable does not match the value that indicates success, or if the executable is not found at the specified location.</span></span>  
  
## <a name="programmatic-configuration-of-the-execute-process-task"></a><span data-ttu-id="abfb3-150">執行處理工作的程式設計組態</span><span class="sxs-lookup"><span data-stu-id="abfb3-150">Programmatic Configuration of the Execute Process Task</span></span>  
 <span data-ttu-id="abfb3-151">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="abfb3-151">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess>  
  
## <a name="see-also"></a><span data-ttu-id="abfb3-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abfb3-152">See Also</span></span>  
 <span data-ttu-id="abfb3-153">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="abfb3-153">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="abfb3-154">控制流程</span><span class="sxs-lookup"><span data-stu-id="abfb3-154">Control Flow</span></span>](control-flow.md)  
  
  
