---
title: 在自訂工作中引發和定義事件 | Microsoft Docs
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
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb41ee60543a05b6cf10b3acda43372e20288d13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597958"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a><span data-ttu-id="ee605-102">引發並在自訂工作中定義事件</span><span class="sxs-lookup"><span data-stu-id="ee605-102">Raising and Defining Events in a Custom Task</span></span>
  <span data-ttu-id="ee605-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段引擎提供事件的集合，可以顯示驗證與執行工作時的工作進度狀態。</span><span class="sxs-lookup"><span data-stu-id="ee605-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine provides a collection of events that provide status on the progress of a task as the task is validated and executed.</span></span> <span data-ttu-id="ee605-104"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 介面會定義這些事件，而且是以 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> 方法的參數提供給工作。</span><span class="sxs-lookup"><span data-stu-id="ee605-104">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface defines these events, and is provided to tasks as a parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="ee605-105">另一組定義在 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> 介面的事件，是由 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 代表工作而引發。</span><span class="sxs-lookup"><span data-stu-id="ee605-105">There is another set of events, which are defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents> interface, that are raised on behalf of the task by the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span> <span data-ttu-id="ee605-106"><xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 會引發在驗證和執行前後發生的事件，而工作會引發在執行和驗證期間發生的事件。</span><span class="sxs-lookup"><span data-stu-id="ee605-106">The <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> raises events that occur before and after validation and execution, whereas the task raises the events that occur during execution and validation.</span></span>  
  
## <a name="creating-custom-events"></a><span data-ttu-id="ee605-107">建立自訂事件</span><span class="sxs-lookup"><span data-stu-id="ee605-107">Creating Custom Events</span></span>  
 <span data-ttu-id="ee605-108">自訂工作開發人員可以透過在 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> 方法的覆寫實作中建立新的 <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A>，以定義新自訂事件。</span><span class="sxs-lookup"><span data-stu-id="ee605-108">Custom task developers can define new, custom events by creating a new <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> in their overridden implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A> method.</span></span> <span data-ttu-id="ee605-109">在建立 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> 之後，會使用 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> 方法，將它加入 `EventInfos` 集合。</span><span class="sxs-lookup"><span data-stu-id="ee605-109">After the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> is created, it is added to the `EventInfos` collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method.</span></span> <span data-ttu-id="ee605-110"><xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> 方法的方法簽章如下所示：</span><span class="sxs-lookup"><span data-stu-id="ee605-110">The method signature of the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> method is as follows:</span></span>  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 <span data-ttu-id="ee605-111">下列程式碼範例會示範自訂工作的 `InitializeTask` 方法，其中建立了兩個自訂事件並設定其屬性。</span><span class="sxs-lookup"><span data-stu-id="ee605-111">The following code sample shows the `InitializeTask` method of a custom task, where two custom events are created and their properties are set.</span></span> <span data-ttu-id="ee605-112">然後會將新事件加入 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> 集合。</span><span class="sxs-lookup"><span data-stu-id="ee605-112">The new events are then added to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection.</span></span>  
  
 <span data-ttu-id="ee605-113">第一個自訂事件的 *eventName* 為 "**OnBeforeIncrement**"，而 *description* 為「**更新初始值之後觸發**」。</span><span class="sxs-lookup"><span data-stu-id="ee605-113">The first custom event has an *eventName* of "**OnBeforeIncrement**" and *description* of "**Fires after the initial value is updated.**"</span></span> <span data-ttu-id="ee605-114">下一個參數 `true` 值表示此事件應允許建立事件處理常式容器以處理事件。</span><span class="sxs-lookup"><span data-stu-id="ee605-114">The next parameter, the `true` value, indicates that this event should allow an event handler container to be created to handle the event.</span></span> <span data-ttu-id="ee605-115">事件處理常式是提供封裝中結構與工作服務的容器，就像封裝、時序、ForLoop 和 ForEachLoop 等其他容器一樣。</span><span class="sxs-lookup"><span data-stu-id="ee605-115">The event handler is a container that provides structure in a package and services to tasks, like other containers such as the package, Sequence, ForLoop, and ForEachLoop.</span></span> <span data-ttu-id="ee605-116">當*allowEventHandlers*參數是時 `true` ， <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 會為事件建立物件。</span><span class="sxs-lookup"><span data-stu-id="ee605-116">When the *allowEventHandlers* parameter is `true`, <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects are created for the event.</span></span> <span data-ttu-id="ee605-117">為事件定義的任何參數現在可供 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 的變數集合中之 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 使用。</span><span class="sxs-lookup"><span data-stu-id="ee605-117">Any parameters that were defined for the event are now available to the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> in the variables collection of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.</span></span>  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a><span data-ttu-id="ee605-118">引發自訂事件</span><span class="sxs-lookup"><span data-stu-id="ee605-118">Raising Custom Events</span></span>  
 <span data-ttu-id="ee605-119">自訂事件是透過呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> 方法來引發。</span><span class="sxs-lookup"><span data-stu-id="ee605-119">Custom events are raised by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="ee605-120">下列程式碼行會引發自訂事件。</span><span class="sxs-lookup"><span data-stu-id="ee605-120">The following line of code raises a custom event.</span></span>  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a><span data-ttu-id="ee605-121">範例</span><span class="sxs-lookup"><span data-stu-id="ee605-121">Sample</span></span>  
 <span data-ttu-id="ee605-122">下列範例顯示的工作會在 `InitializeTask` 方法中定義自訂事件，將自訂事件加入 <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> 集合，然後透過呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> 方法在其 `Execute` 方法期間引發自訂事件。</span><span class="sxs-lookup"><span data-stu-id="ee605-122">The following example shows a task that defines a custom event in the `InitializeTask` method, adds the custom event to the <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos> collection, and then raises the custom event during its `Execute` method by calling the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A> method.</span></span>  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
<span data-ttu-id="ee605-123">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ee605-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ee605-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ee605-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ee605-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ee605-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ee605-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ee605-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee605-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee605-127">See Also</span></span>  
 <span data-ttu-id="ee605-128">[Integration Services &#40;SSIS&#41; 事件處理常式](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="ee605-128">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="ee605-129">將事件處理常式新增至套件</span><span class="sxs-lookup"><span data-stu-id="ee605-129">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
