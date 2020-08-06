---
title: 以指令碼工作來擴充套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5f1a265b01a898cdc87bdf9df6cb67399879061b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700054"
---
# <a name="extending-the-package-with-the-script-task"></a><span data-ttu-id="bbee5-102">以指令碼工作擴充封裝</span><span class="sxs-lookup"><span data-stu-id="bbee5-102">Extending the Package with the Script Task</span></span>
  <span data-ttu-id="bbee5-103">指令碼工作會以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Visual C# 所撰寫且在套件執行階段編譯並執行的自訂程式碼，以擴充 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 套件的執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="bbee5-103">The Script task extends the run-time capabilities of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages with custom code written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# that is compiled and executed at package run time.</span></span> <span data-ttu-id="bbee5-104">當 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 所含的工作未完全滿足您的需求時，指令碼工作可簡化自訂執行階段工作的開發。</span><span class="sxs-lookup"><span data-stu-id="bbee5-104">The Script task simplifies the development of a custom run-time task when the tasks included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] do not fully satisfy your requirements.</span></span> <span data-ttu-id="bbee5-105">指令碼工作會為您撰寫所有必要的基礎結構程式碼，讓您專門著重在自訂處理所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbee5-105">The Script task writes all the required infrastructure code for you, letting you focus exclusively on the code that is required for your custom processing.</span></span>  
  
 <span data-ttu-id="bbee5-106">指令碼工作透過全域 `Dts` 物件與容器封裝互動，這個物件是公開在指令碼編寫環境中的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 類別之執行個體。</span><span class="sxs-lookup"><span data-stu-id="bbee5-106">A Script task interacts with the containing package through the global `Dts` object, an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class that is exposed in the scripting environment.</span></span> <span data-ttu-id="bbee5-107">您可以在指令碼工作中撰寫程式碼，以修改儲存在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 變數的值；之後，封裝可以使用這些更新的值來決定其工作流程的路徑。</span><span class="sxs-lookup"><span data-stu-id="bbee5-107">You can write code in a Script task that modifies the values stored in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] variables; later, the package can use those updated values to determine the path of its workflow.</span></span> <span data-ttu-id="bbee5-108">指令碼工作也可以使用 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 命名空間和 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別庫以及自訂組件，來實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="bbee5-108">The Script task can also use the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] namespace and the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library, as well as custom assemblies, to implement custom functionality.</span></span>  
  
 <span data-ttu-id="bbee5-109">指令碼工作以及它為您產生的基礎結構程式碼，可大幅簡化開發自訂工作的程序。</span><span class="sxs-lookup"><span data-stu-id="bbee5-109">The Script task and the infrastructure code that it generates for you simplify significantly the process of developing a custom task.</span></span> <span data-ttu-id="bbee5-110">不過，若要了解指令碼工作如何運作，閱讀[開發自訂工作](../../extending-packages-custom-objects/task/developing-a-custom-task.md)一節，以了解開發自訂工作所需的步驟，可能會非常有用。</span><span class="sxs-lookup"><span data-stu-id="bbee5-110">However, to understand how the Script task works, you may find it useful to read the section [Developing a Custom Task](../../extending-packages-custom-objects/task/developing-a-custom-task.md) to understand the steps that are involved in developing a custom task.</span></span>  
  
 <span data-ttu-id="bbee5-111">如果您建立一個計劃在多個封裝中重複使用的工作，應該考慮開發自訂工作，而不要使用指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="bbee5-111">If you are creating a task that you plan to reuse in multiple packages, you should consider developing a custom task instead of using the Script task.</span></span> <span data-ttu-id="bbee5-112">如需詳細資訊，請參閱[比較指令碼解決方案和自訂物件](../comparing-scripting-solutions-and-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="bbee5-112">For more information, see [Comparing Scripting Solutions and Custom Objects](../comparing-scripting-solutions-and-custom-objects.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbee5-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="bbee5-113">In This Section</span></span>  
 <span data-ttu-id="bbee5-114">下列主題提供有關指令碼工作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bbee5-114">The following topics provide more information about the Script task.</span></span>  
  
 [<span data-ttu-id="bbee5-115">在指令碼工作編輯器設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="bbee5-115">Configuring the Script Task in the Script Task Editor</span></span>](configuring-the-script-task-in-the-script-task-editor.md)  
 <span data-ttu-id="bbee5-116">說明在**指令碼工作編輯器**中設定的屬性如何影響指令碼工作中程式碼的功能與效能。</span><span class="sxs-lookup"><span data-stu-id="bbee5-116">Explains how the properties that you configure in the **Script Task Editor** affect the capabilities and the performance of the code in the Script task.</span></span>  
  
 [<span data-ttu-id="bbee5-117">編碼和偵錯指令碼工作</span><span class="sxs-lookup"><span data-stu-id="bbee5-117">Coding and Debugging the Script Task</span></span>](../../control-flow/script-task.md)  
 <span data-ttu-id="bbee5-118">說明如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 來開發包含在指令碼工作中的指令碼。</span><span class="sxs-lookup"><span data-stu-id="bbee5-118">Explains how to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) to develop the scripts that are contained in the Script task.</span></span>  
  
 [<span data-ttu-id="bbee5-119">在指令碼工作中使用變數</span><span class="sxs-lookup"><span data-stu-id="bbee5-119">Using Variables in the Script Task</span></span>](using-variables-in-the-script-task.md)  
 <span data-ttu-id="bbee5-120">說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性使用變數。</span><span class="sxs-lookup"><span data-stu-id="bbee5-120">Explains how to use variables through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>  
  
 [<span data-ttu-id="bbee5-121">在指令碼工作中連線至資料來源</span><span class="sxs-lookup"><span data-stu-id="bbee5-121">Connecting to Data Sources in the Script Task</span></span>](connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="bbee5-122">說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 屬性使用連接。</span><span class="sxs-lookup"><span data-stu-id="bbee5-122">Explains how to use connections through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property.</span></span>  
  
 [<span data-ttu-id="bbee5-123">在指令碼工作中引發事件</span><span class="sxs-lookup"><span data-stu-id="bbee5-123">Raising Events in the Script Task</span></span>](raising-events-in-the-script-task.md)  
 <span data-ttu-id="bbee5-124">說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> 屬性引發事件。</span><span class="sxs-lookup"><span data-stu-id="bbee5-124">Explains how to raise events through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> property.</span></span>  
  
 [<span data-ttu-id="bbee5-125">在指令碼工作中記錄</span><span class="sxs-lookup"><span data-stu-id="bbee5-125">Logging in the Script Task</span></span>](logging-in-the-script-task.md)  
 <span data-ttu-id="bbee5-126">說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> 方法記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="bbee5-126">Explains how to log information through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method.</span></span>  
  
 [<span data-ttu-id="bbee5-127">從指令碼工作傳回結果</span><span class="sxs-lookup"><span data-stu-id="bbee5-127">Returning Results from the Script Task</span></span>](returning-results-from-the-script-task.md)  
 <span data-ttu-id="bbee5-128">說明如何透過 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> 屬性與 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> 屬性傳回結果。</span><span class="sxs-lookup"><span data-stu-id="bbee5-128">Explains how to return results through the property <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> and the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> property.</span></span>  
  
 [<span data-ttu-id="bbee5-129">指令碼工作範例</span><span class="sxs-lookup"><span data-stu-id="bbee5-129">Script Task Examples</span></span>](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 <span data-ttu-id="bbee5-130">提供簡單的範例，以示範指令碼工作的幾個可能用途。</span><span class="sxs-lookup"><span data-stu-id="bbee5-130">Provides simple examples that demonstrate several possible uses for a Script task.</span></span>  
  
<span data-ttu-id="bbee5-131">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="bbee5-131">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bbee5-132">若要取得 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的最新下載、文件、範例和影片以及社群中的選定方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="bbee5-132">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bbee5-133">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="bbee5-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bbee5-134">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="bbee5-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbee5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbee5-135">See Also</span></span>  
 <span data-ttu-id="bbee5-136">[腳本工作](../../control-flow/script-task.md) </span><span class="sxs-lookup"><span data-stu-id="bbee5-136">[Script Task](../../control-flow/script-task.md) </span></span>  
 [<span data-ttu-id="bbee5-137">比較指令碼工作和指令碼元件</span><span class="sxs-lookup"><span data-stu-id="bbee5-137">Comparing the Script Task and the Script Component</span></span>](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
