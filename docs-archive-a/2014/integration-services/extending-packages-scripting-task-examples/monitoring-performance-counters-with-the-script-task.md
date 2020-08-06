---
title: 以指令碼工作監視效能計數器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- performance counters [Integration Services]
- SSIS Script task, performance counters
- custom performance counters [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], performance counters
- counters [Integration Services]
ms.assetid: 86609bf1-cae6-435e-a58d-41bdfc521e94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 143e11ff966eb11961aa15073a503522c4b9c86b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705290"
---
# <a name="monitoring-performance-counters-with-the-script-task"></a><span data-ttu-id="a33df-102">以指令碼工作監視效能計數器</span><span class="sxs-lookup"><span data-stu-id="a33df-102">Monitoring Performance Counters with the Script Task</span></span>
  <span data-ttu-id="a33df-103">系統管理員可能需要監視 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝在大量資料執行複雜轉換時的效能。</span><span class="sxs-lookup"><span data-stu-id="a33df-103">Administrators may need to monitor the performance of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that perform complex transformations on large amounts of data.</span></span> <span data-ttu-id="a33df-104">  的 [!INCLUDE[msCoName](../../includes/msconame-md.md)]System.Diagnostics[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間提供可讓您使用現有效能計數器或建立自訂效能計數器的類別。</span><span class="sxs-lookup"><span data-stu-id="a33df-104">The **System.Diagnostics** namespace of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for using existing performance counters and for creating your own performance counters.</span></span>  
  
 <span data-ttu-id="a33df-105">效能計數器會儲存應用程式效能資訊，可用以分析某段時間的軟體效能。</span><span class="sxs-lookup"><span data-stu-id="a33df-105">Performance counters store application performance information that you can use to analyze the performance of software over time.</span></span> <span data-ttu-id="a33df-106">透過使用 [效能監視器]  工具，就可以在本機或是遠端監視效能計數器。</span><span class="sxs-lookup"><span data-stu-id="a33df-106">Performance counters can be monitored locally or remotely by using the **Performance Monitor** tool.</span></span> <span data-ttu-id="a33df-107">您可以將效能計數器值儲存在變數中，以供之後在封裝中的控制流程分支使用。</span><span class="sxs-lookup"><span data-stu-id="a33df-107">You can store the values of performance counters in variables for later control flow branching in the package.</span></span>  
  
 <span data-ttu-id="a33df-108">若不使用效能計數器，您也可以透過 `Dts` 物件的 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 屬性，引發 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 事件。</span><span class="sxs-lookup"><span data-stu-id="a33df-108">As an alternative to using performance counters, you can raise the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property of the `Dts` object.</span></span> <span data-ttu-id="a33df-109"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> 事件會將增加的進度與百分比完成資訊傳回 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行階段。</span><span class="sxs-lookup"><span data-stu-id="a33df-109">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireProgress%2A> event returns both incremental progress and percentage complete information to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a33df-110">如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。</span><span class="sxs-lookup"><span data-stu-id="a33df-110">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="a33df-111">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a33df-111">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="a33df-112">描述</span><span class="sxs-lookup"><span data-stu-id="a33df-112">Description</span></span>  
 <span data-ttu-id="a33df-113">下列範例會建立自訂效能計數器並遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="a33df-113">The following example creates a custom performance counter and increments the counter.</span></span> <span data-ttu-id="a33df-114">首先，範例會判斷效能計數器是否已經存在。</span><span class="sxs-lookup"><span data-stu-id="a33df-114">First, the example determines whether the performance counter already exists.</span></span> <span data-ttu-id="a33df-115">如果尚未建立效能計數器，指令碼會呼叫 `Create` 物件的 `PerformanceCounterCategory` 方法。</span><span class="sxs-lookup"><span data-stu-id="a33df-115">If the performance counter has not been created, the script calls the `Create` method of the `PerformanceCounterCategory` object to create it.</span></span> <span data-ttu-id="a33df-116">在建立效能計數器之後，指令碼會遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="a33df-116">After the performance counter has been created, the script increments the counter.</span></span> <span data-ttu-id="a33df-117">最後，下面將提供範例說明當不再需要效能計數器時，呼叫效能計數器上的 `Close` 方法之最佳作法。</span><span class="sxs-lookup"><span data-stu-id="a33df-117">Finally, the example follows the best practice of calling the `Close` method on the performance counter when it is no longer needed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a33df-118">建立新的效能計數器類別以及效能計數器需要系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="a33df-118">Creating a new performance counter category and performance counter requires administrative rights.</span></span> <span data-ttu-id="a33df-119">另外，在建立新的類別與計數器之後，會保存在電腦上。</span><span class="sxs-lookup"><span data-stu-id="a33df-119">Also, the new category and counter persist on the computer after creation.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="a33df-120">設定此指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="a33df-120">To configure this Script Task example</span></span>  
  
-   <span data-ttu-id="a33df-121">`Imports`在您的程式碼中使用語句來**System.Diagnostics**匯入 system.servicemodel 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a33df-121">Use an `Imports` statement in your code to import the **System.Diagnostics** namespace.</span></span>  
  
### <a name="example-code"></a><span data-ttu-id="a33df-122">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="a33df-122">Example Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myCounter As PerformanceCounter  
  
    Try  
        'Create the performance counter if it does not already exist.  
        If Not _  
        PerformanceCounterCategory.Exists("TaskExample") Then  
            PerformanceCounterCategory.Create("TaskExample", _  
                "Task Performance Counter Example", "Iterations", _  
                "Number of times this task has been called.")  
        End If  
  
        'Initialize the performance counter.  
        myCounter = New PerformanceCounter("TaskExample", _  
            "Iterations", String.Empty, False)  
  
        'Increment the performance counter.  
        myCounter.Increment()  
  
         myCounter.Close()  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Task Performance Counter Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
  
public class ScriptMain  
{  
  
public void Main()  
        {  
  
            PerformanceCounter myCounter;  
  
            try  
            {  
                //Create the performance counter if it does not already exist.  
                if (!PerformanceCounterCategory.Exists("TaskExample"))  
                {  
                    PerformanceCounterCategory.Create("TaskExample", "Task Performance Counter Example", "Iterations", "Number of times this task has been called.");  
                }  
  
                //Initialize the performance counter.  
                myCounter = new PerformanceCounter("TaskExample", "Iterations", String.Empty, false);  
  
                //Increment the performance counter.  
                myCounter.Increment();  
  
                myCounter.Close();  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Task Performance Counter Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
```  
  
<span data-ttu-id="a33df-123">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a33df-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a33df-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a33df-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a33df-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a33df-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a33df-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a33df-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
