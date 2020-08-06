---
title: 以程式設計方式加入工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], packages
- adding package tasks
ms.assetid: 5d4652d5-228c-4238-905c-346dd8503fdf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa61eb2fb87f45fe5b534b96280b8b4e2c21788d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594652"
---
# <a name="adding-tasks-programmatically"></a><span data-ttu-id="c83e2-102">以程式設計方式加入工作</span><span class="sxs-lookup"><span data-stu-id="c83e2-102">Adding Tasks Programmatically</span></span>
  <span data-ttu-id="c83e2-103">在執行階段引擎中可以將工作加入下列類型的物件：</span><span class="sxs-lookup"><span data-stu-id="c83e2-103">Tasks can be added to the following types of objects in the run-time engine:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Package>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.Sequence>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>  
  
 <span data-ttu-id="c83e2-104">這些類別都視為容器，而且它們全部都繼承 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c83e2-104">These classes are considered containers, and they all inherit the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSequence.Executables%2A> property.</span></span> <span data-ttu-id="c83e2-105">容器可以包含工作集合，這些工作是容器執行期間執行階段所處理的可執行物件。</span><span class="sxs-lookup"><span data-stu-id="c83e2-105">Containers can contain a collection of tasks, which are executable objects processed by the runtime during execution of the container.</span></span> <span data-ttu-id="c83e2-106">在集合中的物件執行順序是由容器中每個工作上所設定的任何 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 來決定。</span><span class="sxs-lookup"><span data-stu-id="c83e2-106">The order of execution of the objects in the collection is determined any <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> set on each task in the containers.</span></span> <span data-ttu-id="c83e2-107">優先順序條件約束允許根據集合中的 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 之成功、失敗或是完成來執行分支。</span><span class="sxs-lookup"><span data-stu-id="c83e2-107">Precedence constraints enable execution branching based on the success, failure, or completion of an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> in the collection.</span></span>  
  
 <span data-ttu-id="c83e2-108">每個容器都有 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 集合，它包含個別的 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 物件。</span><span class="sxs-lookup"><span data-stu-id="c83e2-108">Each container has an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection that contains the individual <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects.</span></span> <span data-ttu-id="c83e2-109">每個可執行的工作都會繼承和實作 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> 方法和 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c83e2-109">Each executable task inherits and implements the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> method and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> method.</span></span> <span data-ttu-id="c83e2-110">這兩種方法都是由執行階段引擎來呼叫以處理每個 <xref:Microsoft.SqlServer.Dts.Runtime.Executable>。</span><span class="sxs-lookup"><span data-stu-id="c83e2-110">These two methods are called by the run-time engine to process each <xref:Microsoft.SqlServer.Dts.Runtime.Executable>.</span></span>  
  
 <span data-ttu-id="c83e2-111">若要將工作加入封裝，您需要具有 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 現有集合的容器。</span><span class="sxs-lookup"><span data-stu-id="c83e2-111">To add a task to a package, you need a container with an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> existing collection.</span></span> <span data-ttu-id="c83e2-112">大部分的情況下，您將加入集合的工作是封裝。</span><span class="sxs-lookup"><span data-stu-id="c83e2-112">Most of the time, the task that you will add to the collection is a package.</span></span> <span data-ttu-id="c83e2-113">若要將新工作可執行檔加入容器的集合，可呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c83e2-113">To add the new task executable into the collection for that container, you call the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method .</span></span> <span data-ttu-id="c83e2-114">該方法有單一參數和一個字串，包含 CLSID、PROGID、STOCK Moniker 或是您正在加入的工作之 <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A>。</span><span class="sxs-lookup"><span data-stu-id="c83e2-114">The method has a single parameter, a string, that contains the CLSID, PROGID, STOCK moniker, or <xref:Microsoft.SqlServer.Dts.Runtime.TaskInfo.CreationName%2A> of the task you are adding.</span></span>  
  
## <a name="task-names"></a><span data-ttu-id="c83e2-115">工作名稱</span><span class="sxs-lookup"><span data-stu-id="c83e2-115">Task Names</span></span>  
 <span data-ttu-id="c83e2-116">雖然您可以依名稱或是識別碼指定工作，`STOCK` Moniker 是在 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法中最常使用的參數。</span><span class="sxs-lookup"><span data-stu-id="c83e2-116">Although you can specify a task by name or by ID, the `STOCK` moniker is the parameter used most often in the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method.</span></span> <span data-ttu-id="c83e2-117">若要將工作加入 `STOCK` Moniker 識別的可執行檔，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="c83e2-117">To add a task to an executable identified by the `STOCK` moniker, use the following syntax:</span></span>  
  
```csharp  
Executable exec = package.Executables.Add("STOCK:BulkInsertTask");  
  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add("STOCK:BulkInsertTask")  
  
```  
  
 <span data-ttu-id="c83e2-118">下列清單顯示在 `STOCK` Moniker 後面所使用的每個工作名稱。</span><span class="sxs-lookup"><span data-stu-id="c83e2-118">The following list shows the names for each task that are used after the `STOCK` moniker.</span></span>  
  
-   <span data-ttu-id="c83e2-119">ActiveXScriptTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-119">ActiveXScriptTask</span></span>  
  
-   <span data-ttu-id="c83e2-120">BulkInsertTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-120">BulkInsertTask</span></span>  
  
-   <span data-ttu-id="c83e2-121">ExecuteProcessTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-121">ExecuteProcessTask</span></span>  
  
-   <span data-ttu-id="c83e2-122">ExecutePackageTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-122">ExecutePackageTask</span></span>  
  
-   <span data-ttu-id="c83e2-123">Exec80PackageTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-123">Exec80PackageTask</span></span>  
  
-   <span data-ttu-id="c83e2-124">FileSystemTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-124">FileSystemTask</span></span>  
  
-   <span data-ttu-id="c83e2-125">FTPTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-125">FTPTask</span></span>  
  
-   <span data-ttu-id="c83e2-126">MSMQTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-126">MSMQTask</span></span>  
  
-   <span data-ttu-id="c83e2-127">PipelineTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-127">PipelineTask</span></span>  
  
-   <span data-ttu-id="c83e2-128">ScriptTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-128">ScriptTask</span></span>  
  
-   <span data-ttu-id="c83e2-129">SendMailTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-129">SendMailTask</span></span>  
  
-   <span data-ttu-id="c83e2-130">SQLTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-130">SQLTask</span></span>  
  
-   <span data-ttu-id="c83e2-131">TransferStoredProceduresTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-131">TransferStoredProceduresTask</span></span>  
  
-   <span data-ttu-id="c83e2-132">TransferLoginsTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-132">TransferLoginsTask</span></span>  
  
-   <span data-ttu-id="c83e2-133">TransferErrorMessagesTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-133">TransferErrorMessagesTask</span></span>  
  
-   <span data-ttu-id="c83e2-134">TransferJobsTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-134">TransferJobsTask</span></span>  
  
-   <span data-ttu-id="c83e2-135">TransferObjectsTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-135">TransferObjectsTask</span></span>  
  
-   <span data-ttu-id="c83e2-136">TransferDatabaseTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-136">TransferDatabaseTask</span></span>  
  
-   <span data-ttu-id="c83e2-137">WebServiceTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-137">WebServiceTask</span></span>  
  
-   <span data-ttu-id="c83e2-138">WmiDataReaderTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-138">WmiDataReaderTask</span></span>  
  
-   <span data-ttu-id="c83e2-139">WmiEventWatcherTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-139">WmiEventWatcherTask</span></span>  
  
-   <span data-ttu-id="c83e2-140">XMLTask</span><span class="sxs-lookup"><span data-stu-id="c83e2-140">XMLTask</span></span>  
  
 <span data-ttu-id="c83e2-141">如果您喜歡較明確的語法，或是如果您想要加入的工作沒有 STOCK Moniker，可以使用其完整名稱將工作加入可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c83e2-141">If you prefer a more explicit syntax, or if the task that you want to add does not have a STOCK moniker, you can add the task to the executable using its long name.</span></span> <span data-ttu-id="c83e2-142">這個語法需要您也指定工作的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c83e2-142">This syntax requires that you also specify the version number of the task.</span></span>  
  
```csharp  
Executable exec = package.Executables.Add(  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " +  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " +  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91");  
```  
  
```vb  
Dim exec As Executable = package.Executables.Add( _  
  "Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask, " & _  
  "Microsoft.SqlServer.ScriptTask, Version=10.0.000.0, " & _  
  "Culture=neutral, PublicKeyToken=89845dcd8080cc91")  
```  
  
 <span data-ttu-id="c83e2-143">您可以用程式設計的方式取得工作的完整名稱，而不需指定工作版本，方法是使用類別的 **AssemblyQualifiedName** 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c83e2-143">You can obtain the long name for the task programmatically, without having to specify the task version, by using the **AssemblyQualifiedName** property of the class, as shown in the following example.</span></span> <span data-ttu-id="c83e2-144">這個範例需要 Microsoft.SqlServer.SQLTask 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c83e2-144">This example requires a reference to the Microsoft.SqlServer.SQLTask assembly.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask;  
...  
      Executable exec = package.Executables.Add(  
        typeof(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName);  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask  
...  
    Dim exec As Executable = package.Executables.Add( _  
      GetType(Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask).AssemblyQualifiedName)  
```  
  
 <span data-ttu-id="c83e2-145">下列程式碼範例顯示如何從新封裝建立 <xref:Microsoft.SqlServer.Dts.Runtime.Executables> 集合，然後使用工作的 `STOCK` Moniker，將檔案系統工作和大量插入工作加入集合。</span><span class="sxs-lookup"><span data-stu-id="c83e2-145">The following code example shows how to create an <xref:Microsoft.SqlServer.Dts.Runtime.Executables> collection from a new package, and then add a File System task and a Bulk Insert task to the collection, by using their `STOCK` monikers.</span></span> <span data-ttu-id="c83e2-146">這個範例需要 Microsoft.SqlServer.FileSystemTask 與 Microsoft.SqlServer.BulkInsertTask 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c83e2-146">This example requires a reference to the Microsoft.SqlServer.FileSystemTask and Microsoft.SqlServer.BulkInsertTask assemblies.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thBulkInsertTask = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        Console.WriteLine("Type {0}", taskHost.InnerObject.ToString());  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thBulkInsertTask As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      Console.WriteLine("Type {0}", taskHost.InnerObject.ToString())  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="c83e2-147">**範例輸出：**</span><span class="sxs-lookup"><span data-stu-id="c83e2-147">**Sample Output:**</span></span>  
  
 `Type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
## <a name="taskhost-container"></a><span data-ttu-id="c83e2-148">TaskHost 容器</span><span class="sxs-lookup"><span data-stu-id="c83e2-148">TaskHost Container</span></span>  
 <span data-ttu-id="c83e2-149"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 類別是不會出現在圖形化使用者介面的容器，但是對於程式設計非常重要。</span><span class="sxs-lookup"><span data-stu-id="c83e2-149">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class is a container that does not appear in the graphical user interface, but is very important in programming.</span></span> <span data-ttu-id="c83e2-150">這個類別是每項工作的包裝函數。</span><span class="sxs-lookup"><span data-stu-id="c83e2-150">This class is a wrapper for every task.</span></span> <span data-ttu-id="c83e2-151">透過使用 <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 方法做為 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 物件加入封裝的工作，可以轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 物件。</span><span class="sxs-lookup"><span data-stu-id="c83e2-151">Tasks that are added to the package by using the <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> method as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object can be cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object.</span></span> <span data-ttu-id="c83e2-152">當工作轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 時，可以在工作上使用其他屬性與方法。</span><span class="sxs-lookup"><span data-stu-id="c83e2-152">When a task is cast as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, you can use additional properties and methods on the task.</span></span> <span data-ttu-id="c83e2-153">另外，工作本身可以透過 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="c83e2-153">Also, the task itself can be accessed through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="c83e2-154">視您的需求而定，可以決定將工作保留為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 物件，如此便可透過 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 集合使用工作的屬性。</span><span class="sxs-lookup"><span data-stu-id="c83e2-154">Depending on your needs, you may decide to keep the task as a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object so that you can use the properties of the task through the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection.</span></span> <span data-ttu-id="c83e2-155">使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 的優點是您可以撰寫更一般的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c83e2-155">The advantage of using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> is that you can write more generic code.</span></span> <span data-ttu-id="c83e2-156">如果您對於工作需要非常特定的程式碼，則應該將工作轉換為其適當的物件。</span><span class="sxs-lookup"><span data-stu-id="c83e2-156">If you need very specific code for a task, then you should cast the task to its appropriate object.</span></span>  
  
 <span data-ttu-id="c83e2-157">下列程式碼範例顯示如何將 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 和 thBulkInsertTask (包含 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>) 轉換為 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> 物件。</span><span class="sxs-lookup"><span data-stu-id="c83e2-157">The following code example shows how to cast a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, thBulkInsertTask, that contains a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>, to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> object.</span></span>  
  
```csharp  
BulkInsertTask myTask = thBulkInsertTask.InnerObject as BulkInsertTask;  
```  
  
```vb  
Dim myTask As BulkInsertTask = CType(thBulkInsertTask.InnerObject, BulkInsertTask)  
```  
  
 <span data-ttu-id="c83e2-158">下列程式碼範例顯示如何將可執行檔轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，然後使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 屬性以決定主機包含哪些類型的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c83e2-158">The following code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> property to determine which type of executable is contained by the host.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Tasks.FileSystemTask;  
using Microsoft.SqlServer.Dts.Tasks.BulkInsertTask;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
      // Add a File System task to the package.  
      Executable exec1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileSystemTask1 = exec1 as TaskHost;  
      // Add a Bulk Insert task to the package.  
      Executable exec2 = p.Executables.Add("STOCK:BulkInsertTask");  
      TaskHost thFileSystemTask2 = exec2 as TaskHost;  
  
      // Iterate through the package Executables collection.  
      Executables pExecs = p.Executables;  
      foreach (Executable pExec in pExecs)  
      {  
        TaskHost taskHost = (TaskHost)pExec;  
        if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
        {  
          // Do work with FileSystemTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        else if (taskHost.InnerObject is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask)  
        {  
          // Do work with BulkInsertTask here.  
          Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString());  
        }  
        // Add additional statements to check InnerObject, if desired.  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Tasks.FileSystemTask  
Imports Microsoft.SqlServer.Dts.Tasks.BulkInsertTask  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task to the package.  
    Dim exec1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileSystemTask1 As TaskHost = CType(exec1, TaskHost)  
    ' Add a Bulk Insert task to the package.  
    Dim exec2 As Executable = p.Executables.Add("STOCK:BulkInsertTask")  
    Dim thFileSystemTask2 As TaskHost = CType(exec2, TaskHost)  
  
    ' Iterate through the package Executables collection.  
    Dim pExecs As Executables = p.Executables  
    Dim pExec As Executable  
    For Each pExec In pExecs  
      Dim taskHost As TaskHost = CType(pExec, TaskHost)  
      If TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask Then  
        ' Do work with FileSystemTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      ElseIf TypeOf taskHost.InnerObject Is Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask Then  
        ' Do work with BulkInsertTask here.  
        Console.WriteLine("Found task of type {0}", taskHost.InnerObject.ToString())  
      End If  
      ' Add additional statements to check InnerObject, if desired.  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="c83e2-159">**範例輸出：**</span><span class="sxs-lookup"><span data-stu-id="c83e2-159">**Sample Output:**</span></span>  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask`  
  
 `Found task of type Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask`  
  
 <span data-ttu-id="c83e2-160"><xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> 陳述式會傳回從新建立的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 物件轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 物件的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c83e2-160">The <xref:Microsoft.SqlServer.Dts.Runtime.Executables.Add%2A> statement returns an executable that is cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object from the newly created <xref:Microsoft.SqlServer.Dts.Runtime.Executable> object.</span></span>  
  
 <span data-ttu-id="c83e2-161">若要在新物件上設定屬性或是呼叫方法，您有兩個選項：</span><span class="sxs-lookup"><span data-stu-id="c83e2-161">To set properties or to call methods on the new object, you have two options:</span></span>  
  
1.  <span data-ttu-id="c83e2-162">使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 集合。</span><span class="sxs-lookup"><span data-stu-id="c83e2-162">Use the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="c83e2-163">例如，若要從物件取得屬性，請使用 `th.Properties["propertyname"].GetValue(th))`。</span><span class="sxs-lookup"><span data-stu-id="c83e2-163">For example, to obtain a property from the object, use `th.Properties["propertyname"].GetValue(th))`.</span></span> <span data-ttu-id="c83e2-164">若要設定屬性，請使用 `th.Properties["propertyname"].SetValue(th, <value>);`。</span><span class="sxs-lookup"><span data-stu-id="c83e2-164">To set a property, use `th.Properties["propertyname"].SetValue(th, <value>);`.</span></span>  
  
2.  <span data-ttu-id="c83e2-165">將 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 轉換為工作類別。</span><span class="sxs-lookup"><span data-stu-id="c83e2-165">Cast the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.InnerObject%2A> of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task class.</span></span> <span data-ttu-id="c83e2-166">例如，若要在將大量插入工作加入封裝以做為 <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> 以及接著轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 之後，將該工作轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，請使用 `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`。</span><span class="sxs-lookup"><span data-stu-id="c83e2-166">For example, to cast the Bulk Insert task to a <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask> after it has been added to a package as an <xref:Microsoft.SqlServer.Dts.Runtime.Executable> and subsequently cast to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, use `BulkInsertTask myTask = th.InnerObject as BulkInsertTask;`.</span></span>  
  
 <span data-ttu-id="c83e2-167">在程式碼中使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 類別，而不是轉換為工作特定的類別具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="c83e2-167">Using the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> class in code, instead of casting to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="c83e2-168"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 提供者並不需要程式碼中組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c83e2-168">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> provider does not require a reference to the assembly in the code.</span></span>  
  
-   <span data-ttu-id="c83e2-169">您可以撰寫可用於任何工作的一般常式，因為在編譯時期並不需要知道工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="c83e2-169">You can code generic routines that work for any task, because you do not have to know the name of the task at compile time.</span></span> <span data-ttu-id="c83e2-170">這樣的一般常式包括您傳遞工作名稱給該方法的一些方法，而且該方法的程式碼適用於所有工作。</span><span class="sxs-lookup"><span data-stu-id="c83e2-170">Such generic routines include methods where you pass in the name of the task to the method, and the method code works for all tasks.</span></span> <span data-ttu-id="c83e2-171">這是撰寫測試程式碼的好方法。</span><span class="sxs-lookup"><span data-stu-id="c83e2-171">This is a good method for writing test code.</span></span>  
  
 <span data-ttu-id="c83e2-172">從 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 轉換為工作特定的類別，具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="c83e2-172">Casting from the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> to the task-specific class has the following advantages:</span></span>  
  
-   <span data-ttu-id="c83e2-173">Visual Studio 專案提供您陳述式完成 (IntelliSense)。</span><span class="sxs-lookup"><span data-stu-id="c83e2-173">The Visual Studio project gives you statement completion (IntelliSense).</span></span>  
  
-   <span data-ttu-id="c83e2-174">程式碼的執行速度可能更快。</span><span class="sxs-lookup"><span data-stu-id="c83e2-174">The code may run faster.</span></span>  
  
-   <span data-ttu-id="c83e2-175">工作特定物件允許早期繫結與結果最佳化。</span><span class="sxs-lookup"><span data-stu-id="c83e2-175">Task-specific objects enable early binding and the resulting optimizations.</span></span> <span data-ttu-id="c83e2-176">如需有關早期和晚期繫結的詳細資訊，請參閱＜Visual Basic 語言概念＞中的＜早期和晚期繫結＞主題。</span><span class="sxs-lookup"><span data-stu-id="c83e2-176">For more information about early and late binding, see the topic "Early and Late Binding" in Visual Basic Language Concepts.</span></span>  
  
 <span data-ttu-id="c83e2-177">下列程式碼範例擴充了重複使用工作程式碼的概念。</span><span class="sxs-lookup"><span data-stu-id="c83e2-177">The following code example expands on the concept of reusing task code.</span></span> <span data-ttu-id="c83e2-178">程式碼範例並不是將工作轉換為其特定的類別對等項目，而是將可執行檔轉換為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>，然後使用 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> 以針對所有的工作撰寫一般程式碼。</span><span class="sxs-lookup"><span data-stu-id="c83e2-178">Instead of casting tasks to their specific class equivalents, the code example shows how to cast the executable to a <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, and then uses the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.Properties%2A> to write generic code against all the tasks.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package = new Package();  
  
      string[] tasks = { "STOCK:SQLTask", "STOCK:ScriptTask",   
        "STOCK:ExecuteProcessTask", "STOCK:PipelineTask",   
        "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask" };  
  
      foreach (string s in tasks)  
      {  
        TaskHost taskhost = package.Executables.Add(s) as TaskHost;  
        DtsProperties props = taskhost.Properties;  
        Console.WriteLine("Enumerating properties on " + taskhost.Name);  
        Console.WriteLine(" TaskHost.InnerObject is " + taskhost.InnerObject.ToString());  
        Console.WriteLine();  
  
        foreach (DtsProperty prop in props)  
        {  
          Console.WriteLine("Properties for " + prop.Name);  
          Console.WriteLine("Name : " + prop.Name);  
          Console.WriteLine("Type : " + prop.Type.ToString());  
          Console.WriteLine("Readable : " + prop.Get.ToString());  
          Console.WriteLine("Writable : " + prop.Set.ToString());  
          Console.WriteLine();  
        }  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package = New Package()  
  
    Dim tasks() As String = New String() {"STOCK:SQLTask", "STOCK:ScriptTask", _  
              "STOCK:ExecuteProcessTask", "STOCK:PipelineTask", _  
              "STOCK:FTPTask", "STOCK:SendMailTask", "STOCK:MSMQTask"}  
  
    For Each s As String In tasks  
  
      Dim taskhost As TaskHost = CType(package.Executables.Add(s), TaskHost)  
      Dim props As DtsProperties = taskhost.Properties  
      Console.WriteLine("Enumerating properties on " & taskhost.Name)  
      Console.WriteLine(" TaskHost.InnerObject is " & taskhost.InnerObject.ToString())  
      Console.WriteLine()  
  
      For Each prop As DtsProperty In props  
        Console.WriteLine("Properties for " + prop.Name)  
        Console.WriteLine(" Name : " + prop.Name)  
        Console.WriteLine(" Type : " + prop.Type.ToString())  
        Console.WriteLine(" Readable : " + prop.Get.ToString())  
        Console.WriteLine(" Writable : " + prop.Set.ToString())  
        Console.WriteLine()  
      Next  
  
    Next  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="c83e2-179">外部資源</span><span class="sxs-lookup"><span data-stu-id="c83e2-179">External Resources</span></span>  
 <span data-ttu-id="c83e2-180">blogs.msdn.com 上的部落格文章：[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) (EzAPI - 針對 SQL Server 2012 更新)。</span><span class="sxs-lookup"><span data-stu-id="c83e2-180">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="c83e2-181">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="c83e2-181">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c83e2-182">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="c83e2-182">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c83e2-183">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="c83e2-183">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c83e2-184">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="c83e2-184">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83e2-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c83e2-185">See Also</span></span>  
 [<span data-ttu-id="c83e2-186">以程式設計方式連接工作</span><span class="sxs-lookup"><span data-stu-id="c83e2-186">Connecting Tasks Programmatically</span></span>](../building-packages-programmatically/connecting-tasks-programmatically.md)  
  
  
