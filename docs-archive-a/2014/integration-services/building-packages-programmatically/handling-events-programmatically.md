---
title: 以程式設計方式處理事件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services packages, events
- SQL Server Integration Services packages, events
- SSIS events, programmatically handling
- packages [Integration Services], events
- DtsEventHandler object
- SSIS packages, events
- SSIS events
- events [Integration Services], programmatically
- tasks [Integration Services], events
- IDTSEvents interface
ms.assetid: 0f00bd66-efd5-4f12-9e1c-36195f739332
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c70d2d8909df65f775fc3a3034931bb599597068
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594144"
---
# <a name="handling-events-programmatically"></a><span data-ttu-id="852e2-102">以程式設計方式處理事件</span><span class="sxs-lookup"><span data-stu-id="852e2-102">Handling Events Programmatically</span></span>
  <span data-ttu-id="852e2-103">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 執行階段會提供在驗證和執行封裝之前、期間和之後所發生的事件集合。</span><span class="sxs-lookup"><span data-stu-id="852e2-103">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] runtime provides a collection of events that occur before, during, and after the validation and execution of a package.</span></span> <span data-ttu-id="852e2-104">這些事件可使用兩種方式來擷取。</span><span class="sxs-lookup"><span data-stu-id="852e2-104">These events can be captured in two ways.</span></span> <span data-ttu-id="852e2-105">第一個方法是在類別中實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面，並將此類別當做參數提供給封裝的 `Execute` 和 `Validate` 方法。</span><span class="sxs-lookup"><span data-stu-id="852e2-105">The first method is by implementing the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface in a class, and supplying the class as a parameter to the `Execute` and `Validate` methods of the package.</span></span> <span data-ttu-id="852e2-106">第二個方法是建立 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件，其中可包含當 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 內發生事件時所執行的其他 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 物件 (如工作和迴圈)。</span><span class="sxs-lookup"><span data-stu-id="852e2-106">The second method is by creating <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects, which can contain other [!INCLUDE[ssIS](../../includes/ssis-md.md)] objects, such as tasks and loops, that are executed when an event in <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> occurs.</span></span> <span data-ttu-id="852e2-107">本章節描述這兩個方法，並提供示範其使用方式的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="852e2-107">This section describes these two methods and provides code examples to demonstrate their use.</span></span>  
  
## <a name="receiving-idtsevents-callbacks"></a><span data-ttu-id="852e2-108">接收 IDTSEvents 回撥</span><span class="sxs-lookup"><span data-stu-id="852e2-108">Receiving IDTSEvents Callbacks</span></span>  
 <span data-ttu-id="852e2-109">以程式設計方式建立及執行封裝的開發人員，可以在驗證和執行程序期間使用 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面來接收事件通知。</span><span class="sxs-lookup"><span data-stu-id="852e2-109">Developers who build and execute packages programmatically can receive event notifications during the validation and execution process using the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface.</span></span> <span data-ttu-id="852e2-110">其處理方式是建立一個類別來實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面，並將這個類別當做參數提供給封裝的 `Validate` 和 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="852e2-110">This is done by creating a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface and providing this class as a parameter to the `Validate` and `Execute` methods of a package.</span></span> <span data-ttu-id="852e2-111">然後當事件發生時，執行階段引擎會呼叫此類別的方法。</span><span class="sxs-lookup"><span data-stu-id="852e2-111">The methods of the class are then called by the run-time engine when the events occur.</span></span>  
  
 <span data-ttu-id="852e2-112"><xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別是一個已經實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面的類別；因此，直接實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 的另一個方法是衍生自 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>，並覆寫您想要回應的特定事件。</span><span class="sxs-lookup"><span data-stu-id="852e2-112">The <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class is a class that already implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface; therefore, another alternative to implementing <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> directly is to derive from <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> and override the specific events that you want to respond to.</span></span> <span data-ttu-id="852e2-113">然後您可以將您的類別當做參數提供給 <xref:Microsoft.SqlServer.Dts.Runtime.Package> 的 `Validate` 和 `Execute` 方法，以接收事件回撥。</span><span class="sxs-lookup"><span data-stu-id="852e2-113">You then provide your class as a parameter to the `Validate` and `Execute` methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Package> to receive event callbacks.</span></span>  
  
 <span data-ttu-id="852e2-114">下列程式碼範例會示範衍生自 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 的類別，並覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="852e2-114">The following code sample demonstrates a class that derives from <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents>, and overrides the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnPreExecute%2A> method.</span></span> <span data-ttu-id="852e2-115">然後，類別會當做 aparameter 提供給 `Validate` 封裝的和 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="852e2-115">The class is then provided as aparameter to the `Validate` and `Execute` methods of the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      MyEventsClass eventsClass = new MyEventsClass();  
  
      p.Validate(null, null, eventsClass, null);  
      p.Execute(null, null, eventsClass, null, null);  
  
      Console.Read();  
    }  
  }  
  class MyEventsClass : DefaultEvents  
  {  
    public override void OnPreExecute(Executable exec, ref bool fireAgain)  
    {  
      // TODO: Add custom code to handle the event.  
      Console.WriteLine("The PreExecute event of the " +  
        exec.ToString() + " has been raised.");  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    Dim eventsClass As MyEventsClass = New MyEventsClass()  
  
    p.Validate(Nothing, Nothing, eventsClass, Nothing)  
    p.Execute(Nothing, Nothing, eventsClass, Nothing, Nothing)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
Class MyEventsClass  
  Inherits DefaultEvents  
  
  Public Overrides Sub OnPreExecute(ByVal exec As Executable, ByRef fireAgain As Boolean)  
  
    ' TODO: Add custom code to handle the event.  
    Console.WriteLine("The PreExecute event of the " & _  
      exec.ToString() & " has been raised.")  
  
  End Sub  
  
End Class  
```  
  
## <a name="creating-dtseventhandler-objects"></a><span data-ttu-id="852e2-116">建立 DtsEventHandler 物件</span><span class="sxs-lookup"><span data-stu-id="852e2-116">Creating DtsEventHandler Objects</span></span>  
 <span data-ttu-id="852e2-117">執行階段引擎會透過 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件提供功能強大且彈性高的事件處理和通知系統。</span><span class="sxs-lookup"><span data-stu-id="852e2-117">The run-time engine provides a robust, highly flexible event handling and notification system through the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object.</span></span> <span data-ttu-id="852e2-118">這些物件可讓您在事件處理常式內設計完整工作流程，只有當此事件處理常式所屬的事件發生時，才會執行這些工作流程。</span><span class="sxs-lookup"><span data-stu-id="852e2-118">These objects let you design whole workflows within the event handler, which execute only when the event that the event handler belongs to occurs.</span></span> <span data-ttu-id="852e2-119"><xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件是一個容器，當引發其父物件上的對應事件時會執行此物件。</span><span class="sxs-lookup"><span data-stu-id="852e2-119">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object is a container that is executed when the corresponding event on its parent object fires.</span></span> <span data-ttu-id="852e2-120">此架構可讓您建立隔離的工作流程，執行這些工作流程是為了回應容器上所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="852e2-120">This architecture lets you create isolated workflows that are executed in response to events that occur on a container.</span></span> <span data-ttu-id="852e2-121">因為 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件是同步的，所以要等到附加至此事件的事件處理常式傳回之後，才會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="852e2-121">Because <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects are synchronous, execution does not resume until the event handlers that are attached to the event have returned.</span></span>  
  
 <span data-ttu-id="852e2-122">下列程式碼示範如何建立 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件。</span><span class="sxs-lookup"><span data-stu-id="852e2-122">The following code demonstrates how to create a <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object.</span></span> <span data-ttu-id="852e2-123">此程式碼會將 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 加入至此封裝的 <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> 集合，然後為此工作的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 事件建立 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="852e2-123">The code adds a <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Executables%2A> collection of the package, and then creates a <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> object for the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> event of the task.</span></span> <span data-ttu-id="852e2-124"><xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 會加入至事件處理常式中，當第一個 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> 發生 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 事件時就會執行此事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="852e2-124">A <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> is added to the event handler, which is executed when the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnError%2A> event occurs for the first <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>.</span></span> <span data-ttu-id="852e2-125">這個範例假設您有一個名為 C:\Windows\Temp\DemoFile.txt 的檔案以供測試。</span><span class="sxs-lookup"><span data-stu-id="852e2-125">This example assumes that you have a file that is named C:\Windows\Temp\DemoFile.txt for testing.</span></span> <span data-ttu-id="852e2-126">第一次執行此範例時，表示順利複製此檔案而且未呼叫此事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="852e2-126">The first time that you run the sample, if copies the file successfully and the event handler is not called.</span></span> <span data-ttu-id="852e2-127">當您第二次執行此範例時，表示第一個 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 複製檔案失敗 (因為 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A> 的值是 `false`)、已呼叫此事件處理常式、第二個 <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> 偵測到來源檔案，而且因為發生錯誤而導致封裝報表失敗。</span><span class="sxs-lookup"><span data-stu-id="852e2-127">The second time you run the sample, the first <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> fails to copy the file (because the value of <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask.OverwriteDestinationFile%2A> is `false`), the event handler is called, the second <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask> deletes the source file, and the package reports failure because of the error that occurred.</span></span>  
  
## <a name="example"></a><span data-ttu-id="852e2-128">範例</span><span class="sxs-lookup"><span data-stu-id="852e2-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string f = "DemoFile.txt";  
      Executable e;  
      TaskHost th;  
      FileSystemTask fst;  
  
      Package p = new Package();  
  
      p.Variables.Add("sourceFile", true, String.Empty,  
        @"C:\Windows\Temp\" + f);  
      p.Variables.Add("destinationFile", true, String.Empty,  
        Path.Combine(Directory.GetCurrentDirectory(), f));  
  
      // Create a first File System task and add it to the package.  
      // This task tries to copy a file from one folder to another.  
      e = p.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask1";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.CopyFile;  
      fst.OverwriteDestinationFile = false;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
      fst.Destination = "destinationFile";  
      fst.IsDestinationPathVariable = true;  
  
      // Add an event handler for the FileSystemTask's OnError event.  
      DtsEventHandler ehOnError = (DtsEventHandler)th.EventHandlers.Add("OnError");  
  
      // Create a second File System task and add it to the event handler.  
      // This task deletes the source file if the event handler is called.  
      e = ehOnError.Executables.Add("STOCK:FileSystemTask");  
      th = e as TaskHost;  
      th.Name = "FileSystemTask2";  
      fst = th.InnerObject as FileSystemTask;  
  
      fst.Operation = DTSFileSystemOperation.DeleteFile;  
      fst.Source = "sourceFile";  
      fst.IsSourcePathVariable = true;  
  
      DTSExecResult vr = p.Validate(null, null, null, null);  
      Console.WriteLine("ValidationResult = " + vr.ToString());  
      if (vr == DTSExecResult.Success)  
      {  
        DTSExecResult er = p.Execute(null, null, null, null, null);  
        Console.WriteLine("ExecutionResult = " + er.ToString());  
        if (er == DTSExecResult.Failure)  
          if (!File.Exists(@"C:\Windows\Temp\" + f))  
            Console.WriteLine("Source file has been deleted by the event handler.");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports System.IO  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim f As String = "DemoFile.txt"  
    Dim e As Executable  
    Dim th As TaskHost  
    Dim fst As FileSystemTask  
  
    Dim p As Package = New Package()  
  
    p.Variables.Add("sourceFile", True, String.Empty, _  
      "C:\Windows\Temp\" & f)  
    p.Variables.Add("destinationFile", True, String.Empty, _  
      Path.Combine(Directory.GetCurrentDirectory(), f))  
  
    ' Create a first File System task and add it to the package.  
    ' This task tries to copy a file from one folder to another.  
    e = p.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.CopyFile  
    fst.OverwriteDestinationFile = False  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
    fst.Destination = "destinationFile"  
    fst.IsDestinationPathVariable = True  
  
    ' Add an event handler for the FileSystemTask's OnError event.  
    Dim ehOnError As DtsEventHandler = CType(th.EventHandlers.Add("OnError"), DtsEventHandler)  
  
    ' Create a second File System task and add it to the event handler.  
    ' This task deletes the source file if the event handler is called.  
    e = ehOnError.Executables.Add("STOCK:FileSystemTask")  
    th = CType(e, TaskHost)  
    th.Name = "FileSystemTask1"  
    fst = CType(th.InnerObject, FileSystemTask)  
  
    fst.Operation = DTSFileSystemOperation.DeleteFile  
    fst.Source = "sourceFile"  
    fst.IsSourcePathVariable = True  
  
    Dim vr As DTSExecResult = p.Validate(Nothing, Nothing, Nothing, Nothing)  
    Console.WriteLine("ValidationResult = " + vr.ToString())  
    If vr = DTSExecResult.Success Then  
      Dim er As DTSExecResult = p.Execute(Nothing, Nothing, Nothing, Nothing, Nothing)  
      Console.WriteLine("ExecutionResult = " + er.ToString())  
      If er = DTSExecResult.Failure Then  
        If Not File.Exists("C:\Windows\Temp\" + f) Then  
          Console.WriteLine("Source file has been deleted by the event handler.")  
        End If  
      End If  
    End If  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="852e2-129">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="852e2-129">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="852e2-130">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="852e2-130">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="852e2-131">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="852e2-131">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="852e2-132">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="852e2-132">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852e2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="852e2-133">See Also</span></span>  
 <span data-ttu-id="852e2-134">[Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="852e2-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="852e2-135">將事件處理常式新增至套件</span><span class="sxs-lookup"><span data-stu-id="852e2-135">Add an Event Handler to a Package</span></span>](../add-an-event-handler-to-a-package.md)  
  
  
