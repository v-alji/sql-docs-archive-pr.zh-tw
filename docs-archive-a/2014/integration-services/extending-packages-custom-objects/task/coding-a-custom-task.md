---
title: 撰寫自訂工作的程式碼 | Microsoft Docs
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
- Validate method
- custom tasks [Integration Services], validating
- validation [Integration Services], design-time tasks
- SSIS custom tasks, validating
ms.assetid: dc224f4f-b339-4eb6-a008-1b4fe0ea4fd2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c369f4a7e8352be7ddde9e2e3938b47b0bcc1349
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597226"
---
# <a name="coding-a-custom-task"></a><span data-ttu-id="441d0-102">撰寫自訂工作的程式碼</span><span class="sxs-lookup"><span data-stu-id="441d0-102">Coding a Custom Task</span></span>
  <span data-ttu-id="441d0-103">建立繼承自 [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基底類別的類別，並將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性 (Attribute) 套用到類別之後，必須覆寫基底類別的屬性 (Properties) 與方法的實作，才可提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="441d0-103">After you have created a class that inherits from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>

## <a name="configuring-the-task"></a><span data-ttu-id="441d0-104">設定工作</span><span class="sxs-lookup"><span data-stu-id="441d0-104">Configuring the Task</span></span>

### <a name="validating-the-task"></a><span data-ttu-id="441d0-105">驗證工作</span><span class="sxs-lookup"><span data-stu-id="441d0-105">Validating the Task</span></span>
 <span data-ttu-id="441d0-106">當您在設計 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 封裝時，可以使用驗證來確認每個工作上的設定，這樣您就可以盡早在設定時擷取到不正確或不當的設定值，而不是只能夠在執行階段尋找所有的錯誤。</span><span class="sxs-lookup"><span data-stu-id="441d0-106">When you are designing an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package, you can use validation to verify settings on each task, so that you can catch incorrect or inappropriate settings as soon as they are set, instead of finding all errors at run-time only.</span></span> <span data-ttu-id="441d0-107">驗證的目的就是要判斷工作是否包含使其無法成功執行的無效設定或是連接。</span><span class="sxs-lookup"><span data-stu-id="441d0-107">The purpose of validation is to determine whether the task contains invalid settings or connections that will prevent it from running successfully.</span></span> <span data-ttu-id="441d0-108">這可確保封裝所包含的工作在第一次執行時，就可以順利地執行。</span><span class="sxs-lookup"><span data-stu-id="441d0-108">This makes sure that the package contains tasks that have a good chance of running on their first run.</span></span>

 <span data-ttu-id="441d0-109">您可以在自訂程式碼中使用 `Validate` 方法來實作驗證。</span><span class="sxs-lookup"><span data-stu-id="441d0-109">You can implement validation by using the `Validate` method in custom code.</span></span> <span data-ttu-id="441d0-110">執行階段引擎會透過呼叫在工作上的 `Validate` 方法來驗證工作。</span><span class="sxs-lookup"><span data-stu-id="441d0-110">The run-time engine validates a task by calling the `Validate` method on the task.</span></span> <span data-ttu-id="441d0-111">工作開發人員的責任就是要定義可判斷工作成功或失敗的驗證準則，並通知執行階段引擎此驗證的結果。</span><span class="sxs-lookup"><span data-stu-id="441d0-111">It is the responsibility of the task developer to define the criteria that give you a successful or failed task validation, and to notify the run-time engine of the result of this evaluation.</span></span>

#### <a name="task-abstract-base-class"></a><span data-ttu-id="441d0-112">工作抽象基底類別</span><span class="sxs-lookup"><span data-stu-id="441d0-112">Task Abstract Base Class</span></span>
 <span data-ttu-id="441d0-113">[ [] 抽象基類提供了](/dotnet/api/microsoft.sqlserver.dts.runtime.task) `Validate` 方法，每個工作都會覆寫以定義其驗證準則。</span><span class="sxs-lookup"><span data-stu-id="441d0-113">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) abstract base class provides the `Validate` method that each task overrides to define its validation criteria.</span></span> <span data-ttu-id="441d0-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會自動在封裝設計期間呼叫 `Validate` 方法多次，並在警告或錯誤發生時，提供視覺提示給使用者，以協助識別工作組態中的問題。</span><span class="sxs-lookup"><span data-stu-id="441d0-114">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically calls the `Validate` method multiple times during package design, and provides visual cues to the user when warnings or errors occur to help identify problems with the configuration of the task.</span></span> <span data-ttu-id="441d0-115">工作透過從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列舉傳回值，以及透過引發警告和錯誤事件，來提供驗證結果。</span><span class="sxs-lookup"><span data-stu-id="441d0-115">Tasks provide validation results by returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and by raising warning and error events.</span></span> <span data-ttu-id="441d0-116">這些事件包含對 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中的使用者顯示的資訊。</span><span class="sxs-lookup"><span data-stu-id="441d0-116">These events contain information that is displayed to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="441d0-117">以下是一些驗證範例：</span><span class="sxs-lookup"><span data-stu-id="441d0-117">Some examples for validation follow:</span></span>

-   <span data-ttu-id="441d0-118">連接管理員會驗證特定的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="441d0-118">A connection manager validates the specific file name.</span></span>

-   <span data-ttu-id="441d0-119">連接管理員會驗證輸入的類型是否為預期的類型，例如 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="441d0-119">A connection manager validates that the type of input is the expected type, such as an XML file.</span></span>

-   <span data-ttu-id="441d0-120">需要資料庫輸入的工作會確認它無法從非資料庫連接接收資料。</span><span class="sxs-lookup"><span data-stu-id="441d0-120">A task that expects database input verifies that it cannot receive data from a non-database connection.</span></span>

-   <span data-ttu-id="441d0-121">工作會保證其所有屬性都不會與相同工作上設定的其他屬性衝突。</span><span class="sxs-lookup"><span data-stu-id="441d0-121">A task guarantees that none of its properties contradicts other properties set on the same task.</span></span>

-   <span data-ttu-id="441d0-122">工作會保證其在執行時需要使用的全部資源都可以使用。</span><span class="sxs-lookup"><span data-stu-id="441d0-122">A task guarantees that all required resources used by the task at execution time are available.</span></span>

 <span data-ttu-id="441d0-123">在判斷要驗證的項目時，需要考量的另一個層面是效能。</span><span class="sxs-lookup"><span data-stu-id="441d0-123">Performance is something to consider in determining what is validated and what is not.</span></span> <span data-ttu-id="441d0-124">例如，工作的輸入可能是透過低頻寬網路或高流量網路的連接。</span><span class="sxs-lookup"><span data-stu-id="441d0-124">For example, the input to a task might be a connection over a network that has low bandwidth or heavy traffic.</span></span> <span data-ttu-id="441d0-125">如果您決定驗證該資源是否可用，驗證可能需要花費數秒的處理時間。</span><span class="sxs-lookup"><span data-stu-id="441d0-125">The validation may take several seconds to process if you decide to validate that the resource is available.</span></span> <span data-ttu-id="441d0-126">另一項驗證可能會造成需要大量地往返於伺服器之間，而且驗證常式可能會變慢。</span><span class="sxs-lookup"><span data-stu-id="441d0-126">Another validation may cause a round-trip to a server that is in high demand, and the validation routine might be slow.</span></span> <span data-ttu-id="441d0-127">雖然有許多屬性和設定都可加以驗證，但這不表示您該驗證所有項目。</span><span class="sxs-lookup"><span data-stu-id="441d0-127">Although there are many properties and settings that can be validated, not everything should be validated.</span></span>

-   <span data-ttu-id="441d0-128">在執行工作之前，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 也會呼叫 `Validate` 方法中的程式碼，而且如果驗證失敗，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 會取消執行。</span><span class="sxs-lookup"><span data-stu-id="441d0-128">The code in the `Validate` method is also called by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> before the task is run, and the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> cancels execution if validation fails.</span></span>

#### <a name="user-interface-considerations-during-validation"></a><span data-ttu-id="441d0-129">在驗證期間的使用者介面考量</span><span class="sxs-lookup"><span data-stu-id="441d0-129">User Interface Considerations during Validation</span></span>
 <span data-ttu-id="441d0-130">此工作[會將](/dotnet/api/microsoft.sqlserver.dts.runtime.task)介面當做 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 參數包含在 `Validate` 方法中。</span><span class="sxs-lookup"><span data-stu-id="441d0-130">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) includes an <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface as a parameter to the `Validate` method.</span></span> <span data-ttu-id="441d0-131"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 介面包含工作向執行階段引擎引發事件所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-131">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the methods that are called by the task in order to raise events to the run-time engine.</span></span> <span data-ttu-id="441d0-132">當警告或是錯誤狀況在驗證期間發生時，會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-132">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods are called when a warning or error condition occurs during validation.</span></span> <span data-ttu-id="441d0-133">這兩個警告方法都需要相同的參數，包含錯誤碼、來源元件、描述、說明檔以及說明內容資訊。</span><span class="sxs-lookup"><span data-stu-id="441d0-133">Both warning methods require the same parameters, which include an error code, source component, description, Help file, and Help context information.</span></span> <span data-ttu-id="441d0-134">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師使用此資訊在設計介面上顯示視覺提示。</span><span class="sxs-lookup"><span data-stu-id="441d0-134">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses this information to display visual cues on the design surface.</span></span> <span data-ttu-id="441d0-135">設計師提供的視覺提示包括出現在設計師介面上工作旁邊的驚嘆號圖示。</span><span class="sxs-lookup"><span data-stu-id="441d0-135">The visual cues that are provided by the designer include an exclamation icon that appears next to the task on the designer surface.</span></span> <span data-ttu-id="441d0-136">此視覺提示提醒使用者工作需要其他組態，執行才可以繼續。</span><span class="sxs-lookup"><span data-stu-id="441d0-136">This visual cue signals to the user that the task requires additional configuration before execution can continue.</span></span>

 <span data-ttu-id="441d0-137">驚嘆號圖示也會顯示包含錯誤訊息的工具提示。</span><span class="sxs-lookup"><span data-stu-id="441d0-137">The exclamation icon also displays a ToolTip that contains an error message.</span></span> <span data-ttu-id="441d0-138">工作會在事件的描述參數中提供錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="441d0-138">The error message is provided by the task in the description parameter of the event.</span></span> <span data-ttu-id="441d0-139">錯誤訊息也會顯示在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的 [工作清單] 窗格中，這個窗格為使用者提供檢視所有驗證錯誤的集中位置。</span><span class="sxs-lookup"><span data-stu-id="441d0-139">Error messages are also displayed in the **Task List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], providing the user with a central location for viewing all validation errors.</span></span>

#### <a name="validation-example"></a><span data-ttu-id="441d0-140">驗證範例</span><span class="sxs-lookup"><span data-stu-id="441d0-140">Validation Example</span></span>
 <span data-ttu-id="441d0-141">下列程式碼範例顯示使用 `UserName` 屬性的工作。</span><span class="sxs-lookup"><span data-stu-id="441d0-141">The following code example shows a task with a `UserName` property.</span></span> <span data-ttu-id="441d0-142">已指定此屬性為成功驗證所需。</span><span class="sxs-lookup"><span data-stu-id="441d0-142">This property has been specified as required for validation to succeed.</span></span> <span data-ttu-id="441d0-143">如果未設定此屬性，工作會公佈錯誤，並從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> 列舉傳回 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult>。</span><span class="sxs-lookup"><span data-stu-id="441d0-143">If the property is not set, the task posts an error, and returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Failure> from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span> <span data-ttu-id="441d0-144">`Validate` 方法會包裝在 Try/Catch 區塊中，而且會在發生例外狀況時失敗。</span><span class="sxs-lookup"><span data-stu-id="441d0-144">The `Validate` method is wrapped in a try/catch block, and fails validation if an exception occurs.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string userName = "";

  public override DTSExecResult Validate(Connections connections,
     VariableDispenser variableDispenser, IDTSComponentEvents events,
     IDTSLogging log)
  {
    try
    {
      if (this.userName == "")
      {
        //   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0);
        //   Fail validation.
        return DTSExecResult.Failure;
      }
      //   Return success.
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string UserName
  {
    get
    {
      return this.userName;
    }
    set
    {
      this.userName = value;
    }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _userName As String = ""

  Public Overrides Function Validate(ByVal connections As Connections, _
     ByVal variableDispenser As VariableDispenser, _
     ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging) As DTSExecResult

    Try
      If Me._userName = "" Then
        '   Raise an OnError event.
        events.FireError(0, "SampleTask", "The UserName property must be configured.", "", 0)
        '   Fail validation.
        Return DTSExecResult.Failure
      End If
      '   Return success.
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture exceptions, post an error, and fail validation.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property UserName() As String
    Get
      Return Me._userName
    End Get
    Set(ByVal Value As String)
      Me._userName = Value
    End Set
  End Property

End Class
```

### <a name="persisting-the-task"></a><span data-ttu-id="441d0-145">保存工作</span><span class="sxs-lookup"><span data-stu-id="441d0-145">Persisting the Task</span></span>
 <span data-ttu-id="441d0-146">一般而言，您不必實作工作的自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="441d0-146">Ordinarily you do not have to implement custom persistence for a task.</span></span> <span data-ttu-id="441d0-147">只有在物件的屬性使用複雜的資料類型時，才需要自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="441d0-147">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="441d0-148">如需詳細資訊，請參閱[開發 Integration Services 的自訂物件](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="441d0-148">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>

## <a name="executing-the-task"></a><span data-ttu-id="441d0-149">執行工作</span><span class="sxs-lookup"><span data-stu-id="441d0-149">Executing the Task</span></span>
 <span data-ttu-id="441d0-150">本節描述如何使用工作繼承和覆寫的 `Execute` 方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-150">This section describes how to use the `Execute` method that is inherited and overridden by tasks.</span></span> <span data-ttu-id="441d0-151">本節也會說明提供工作執行結果相關資訊的各種方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-151">This section also explains various ways of providing information about the results of task execution.</span></span>

### <a name="execute-method"></a><span data-ttu-id="441d0-152">Execute 方法</span><span class="sxs-lookup"><span data-stu-id="441d0-152">Execute Method</span></span>
 <span data-ttu-id="441d0-153">包含在封裝中的工作會在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段呼叫其 `Execute` 方法時執行。</span><span class="sxs-lookup"><span data-stu-id="441d0-153">Tasks that are contained in a package run when the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls their `Execute` method.</span></span> <span data-ttu-id="441d0-154">工作會在此方法中執行其核心商務邏輯和功能，並藉由張貼訊息、從列舉傳回值 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> ，以及覆寫屬性的屬性，來提供執行結果 `get` `ExecutionValue` 。</span><span class="sxs-lookup"><span data-stu-id="441d0-154">Tasks implement their core business logic and functionality in this method, and provide the results of execution by posting messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration, and overriding the property `get` of the `ExecutionValue` property.</span></span>

 <span data-ttu-id="441d0-155">[Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基底類別會提供 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法的預設實作。</span><span class="sxs-lookup"><span data-stu-id="441d0-155">The [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class provides a default implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="441d0-156">自訂工作會覆寫此方法以定義其執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="441d0-156">The custom tasks override this method to define their run-time functionality.</span></span> <span data-ttu-id="441d0-157"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 物件會包裝工作，將工作與執行階段引擎和封裝中的其他物件隔離。</span><span class="sxs-lookup"><span data-stu-id="441d0-157">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> object wraps the task, isolating it from the run-time engine and the other objects in the package.</span></span> <span data-ttu-id="441d0-158">因為此隔離，工作不會知道它在封裝中與執行順序有關的位置，而且只會在執行階段呼叫工作時才執行。</span><span class="sxs-lookup"><span data-stu-id="441d0-158">Because of this isolation, the task is unaware of its location in the package with regard to its execution order, and runs only when it is called by the runtime.</span></span> <span data-ttu-id="441d0-159">這個架構可預防工作在執行期間修改封裝時可能發生的問題。</span><span class="sxs-lookup"><span data-stu-id="441d0-159">This architecture prevents problems that can occur when tasks modify the package during execution.</span></span> <span data-ttu-id="441d0-160">只有透過將封裝中的其他物件當做 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法中的參數提供給工作，該工作才能夠存取這些物件。</span><span class="sxs-lookup"><span data-stu-id="441d0-160">The task is provided access to the other objects in the package only through the objects supplied to it as parameters in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span> <span data-ttu-id="441d0-161">這些參數可以讓工作引發事件、將項目寫入事件記錄檔、存取變數集合以及將連接編列到交易中的資料來源，同時仍保有可保障封裝的穩定性和可靠性所需的隔離。</span><span class="sxs-lookup"><span data-stu-id="441d0-161">These parameters let tasks raise events, write entries to the event log, access the variables collection, and enlist connections to data sources in transactions, while still maintaining the isolation that is necessary to guarantee the stability and reliability of the package.</span></span>

 <span data-ttu-id="441d0-162">下表列出 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法中提供給工作的參數。</span><span class="sxs-lookup"><span data-stu-id="441d0-162">The following table lists the parameters provided to the task in the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> method.</span></span>

|<span data-ttu-id="441d0-163">參數</span><span class="sxs-lookup"><span data-stu-id="441d0-163">Parameter</span></span>|<span data-ttu-id="441d0-164">描述</span><span class="sxs-lookup"><span data-stu-id="441d0-164">Description</span></span>|
|---------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Runtime.Connections>|<span data-ttu-id="441d0-165">包含可供工作使用的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="441d0-165">Contains a collection of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects available to the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.VariableDispenser>|<span data-ttu-id="441d0-166">包含工作可用的變數。</span><span class="sxs-lookup"><span data-stu-id="441d0-166">Contains the variables available to the task.</span></span> <span data-ttu-id="441d0-167">工作會透過 VariableDispenser 來使用變數，不會直接使用變數。</span><span class="sxs-lookup"><span data-stu-id="441d0-167">The tasks use variables through the VariableDispenser; the tasks do not use variables directly.</span></span> <span data-ttu-id="441d0-168">變數分配程式會鎖定和解除鎖定變數，並防止死結或是覆寫。</span><span class="sxs-lookup"><span data-stu-id="441d0-168">The variable dispenser locks and unlocks variables, and prevents deadlocks or overwrites.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents>|<span data-ttu-id="441d0-169">包含工作向執行階段引擎引發事件所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-169">Contains the methods called by the task to raise events to the run-time engine.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.IDTSLogging>|<span data-ttu-id="441d0-170">包含工作將項目寫入事件記錄檔所使用的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="441d0-170">Contains methods and properties used by the task to write entries to the event log.</span></span>|
|<span data-ttu-id="441d0-171">Object</span><span class="sxs-lookup"><span data-stu-id="441d0-171">Object</span></span>|<span data-ttu-id="441d0-172">包含容器所屬的交易物件 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="441d0-172">Contains the transaction object that the container is a part of, if any.</span></span> <span data-ttu-id="441d0-173">這個值會當做參數傳遞至 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 物件的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 方法。</span><span class="sxs-lookup"><span data-stu-id="441d0-173">This value is passed as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object.</span></span>|

### <a name="providing-execution-feedback"></a><span data-ttu-id="441d0-174">提供執行回饋</span><span class="sxs-lookup"><span data-stu-id="441d0-174">Providing Execution Feedback</span></span>
 <span data-ttu-id="441d0-175">工作會在 `try/catch` 區塊中包裝其程式碼，以防止對執行階段引擎引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="441d0-175">Tasks wrap their code in `try/catch` blocks to prevent exceptions from being raised to the run-time engine.</span></span> <span data-ttu-id="441d0-176">這可確保封裝完成執行並且不會意外停止。</span><span class="sxs-lookup"><span data-stu-id="441d0-176">This ensures that the package finishes execution and does not stop unexpectedly.</span></span> <span data-ttu-id="441d0-177">不過，執行階段引擎有提供其他機制，以處理可能在工作執行期間發生的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="441d0-177">However, the run-time engine provides other mechanisms for handling error conditions that can occur during the execution of a task.</span></span> <span data-ttu-id="441d0-178">這些機制包括公佈錯誤與警告訊息、從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 結構傳回值、公佈訊息、傳回 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 值，以及透過 <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> 屬性揭露工作執行結果的資訊。</span><span class="sxs-lookup"><span data-stu-id="441d0-178">These include posting error and warning messages, returning a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> structure, posting messages, returning the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value, and disclosing information about the results of task execution through the <xref:Microsoft.SqlServer.Dts.Runtime.Task.ExecutionValue%2A> property.</span></span>

 <span data-ttu-id="441d0-179"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 介面包含 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 方法，工作可以呼叫這些方法以便將錯誤與警告訊息公佈到執行階段引擎。</span><span class="sxs-lookup"><span data-stu-id="441d0-179">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface contains the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods, which can be called by the task to post error and warning messages to the run-time engine.</span></span> <span data-ttu-id="441d0-180">這兩個方法都需要錯誤碼、來源元件、描述、說明檔以及說明內容資訊等參數。</span><span class="sxs-lookup"><span data-stu-id="441d0-180">Both methods require parameters such as the error code, source component, description, Help file, and help context information.</span></span> <span data-ttu-id="441d0-181">視工作的組態而定，執行階段會藉由引發事件和中斷點或是將資訊寫入事件記錄檔中，以回應這些訊息。</span><span class="sxs-lookup"><span data-stu-id="441d0-181">Depending on the configuration of the task, the runtime responds to these messages by raising events and breakpoints, or by writing information to the event log.</span></span>

 <span data-ttu-id="441d0-182"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 也提供 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 屬性，可用以提供有關執行結果的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="441d0-182">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> also provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property that can be used to provide additional information about the results of execution.</span></span> <span data-ttu-id="441d0-183">例如，如果工作從資料表刪除資料列，做為其 `Execute` 方法的一部分，它可能會傳回刪除的資料列數，以做為 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="441d0-183">For example, if a task deletes rows from a table as part of its `Execute` method, it might return the number of rows deleted as the value of the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property.</span></span> <span data-ttu-id="441d0-184">此外，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 提供 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="441d0-184">In addition, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecValueVariable%2A> property.</span></span> <span data-ttu-id="441d0-185">此屬性可讓使用者將從工作傳回的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 對應至工作可看到的任何變數。</span><span class="sxs-lookup"><span data-stu-id="441d0-185">This property lets the user map the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> returned from the task to any variable visible to the task.</span></span> <span data-ttu-id="441d0-186">然後，指定的變數可以用來建立工作間的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="441d0-186">The specified variable can then be used to establish precedence constraints between tasks.</span></span>

### <a name="execution-example"></a><span data-ttu-id="441d0-187">執行範例</span><span class="sxs-lookup"><span data-stu-id="441d0-187">Execution Example</span></span>
 <span data-ttu-id="441d0-188">下列程式碼範例會示範 `Execute` 方法的實作，並顯示覆寫的 `ExecutionValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="441d0-188">The following code example demonstrates an implementation of the `Execute` method, and shows an overridden `ExecutionValue` property.</span></span> <span data-ttu-id="441d0-189">工作會刪除工作的 `fileName` 屬性所指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="441d0-189">The task deletes the file that is specified by the `fileName` property of the task.</span></span> <span data-ttu-id="441d0-190">如果檔案不存在，或者 `fileName` 屬性是空字串，工作會公佈警告。</span><span class="sxs-lookup"><span data-stu-id="441d0-190">The task posts a warning if the file does not exist, or if the `fileName` property is an empty string.</span></span> <span data-ttu-id="441d0-191">工作會傳回 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> 屬性中的 `Boolean` 值，以指出是否已刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="441d0-191">The task returns a `Boolean` value in the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost.ExecutionValue%2A> property to indicate whether the file was deleted.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

public class SampleTask : Task
{
  private string fileName = "";
  private bool fileDeleted = false;

  public override DTSExecResult Execute(Connections cons,
     VariableDispenser vars, IDTSComponentEvents events,
     IDTSLogging log, Object txn)
  {
    try
    {
      if (this.fileName == "")
      {
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0);
        this.fileDeleted = false;
      }
      else
      {
        if (System.IO.File.Exists(this.fileName))
        {
          System.IO.File.Delete(this.fileName);
          this.fileDeleted = true;
        }
        else
          this.fileDeleted = false;
      }
      return DTSExecResult.Success;
    }
    catch (System.Exception exception)
    {
      //   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0);
      return DTSExecResult.Failure;
    }
  }
  public string FileName
  {
    get { return this.fileName; }
    set { this.fileName = value; }
  }
  public override object ExecutionValue
  {
    get { return this.fileDeleted; }
  }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Runtime

Public Class SampleTask
  Inherits Task

  Private _fileName As String = ""
  Private _fileDeleted As Boolean = False

  Public Overrides Function Execute(ByVal cons As Connections, _
     ByVal vars As VariableDispenser, ByVal events As IDTSComponentEvents, _
     ByVal log As IDTSLogging, ByVal txn As Object) As DTSExecResult

    Try
      If Me._fileName = "" Then
        events.FireWarning(0, "SampleTask", "No file specified.", "", 0)
        Me._fileDeleted = False
      Else
        If System.IO.File.Exists(Me._fileName) Then
          System.IO.File.Delete(Me._fileName)
          Me._fileDeleted = True
        Else
          Me._fileDeleted = False
        End If
      End If
      Return DTSExecResult.Success
    Catch exception As System.Exception
      '   Capture the exception and post an error.
      events.FireError(0, "Sampletask", exception.Message, "", 0)
      Return DTSExecResult.Failure
    End Try

  End Function

  Public Property FileName() As String
    Get
      Return Me._fileName
    End Get
    Set(ByVal Value As String)
      Me._fileName = Value
    End Set
  End Property

  Public Overrides ReadOnly Property ExecutionValue() As Object
    Get
      Return Me._fileDeleted
    End Get
  End Property

End Class
```

<span data-ttu-id="441d0-192">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="441d0-192">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="441d0-193">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="441d0-193">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="441d0-194">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="441d0-194">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="441d0-195">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="441d0-195">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="441d0-196">另請參閱</span><span class="sxs-lookup"><span data-stu-id="441d0-196">See Also</span></span>
 <span data-ttu-id="441d0-197">[建立自訂](creating-a-custom-task.md)工作[編碼自](coding-a-custom-task.md)定義工作[開發自訂工作的使用者介面](developing-a-user-interface-for-a-custom-task.md)</span><span class="sxs-lookup"><span data-stu-id="441d0-197">[Creating a Custom Task](creating-a-custom-task.md) [Coding a Custom Task](coding-a-custom-task.md) [Developing a User Interface for a Custom Task](developing-a-user-interface-for-a-custom-task.md)</span></span>


