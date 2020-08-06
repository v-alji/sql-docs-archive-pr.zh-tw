---
title: 在資料流程元件中引發和定義事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], events
- events [Integration Services], custom
- custom events [Integration Services]
- custom data flow components [Integration Services], events
- events [Integration Services], raising
- predefined events [Integration Services]
ms.assetid: 1d8c5358-9384-47a8-b7cb-7b0650384119
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 25f4572f8a8af829145da4e4d685f5dddad4a29a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688045"
---
# <a name="raising-and-defining-events-in-a-data-flow-component"></a><span data-ttu-id="b833d-102">在資料流程元件中引發和定義事件</span><span class="sxs-lookup"><span data-stu-id="b833d-102">Raising and Defining Events in a Data Flow Component</span></span>
  <span data-ttu-id="b833d-103">元件開發人員可以引發 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> 介面中定義的事件子集，其方式是呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 屬性上所公開的方法。</span><span class="sxs-lookup"><span data-stu-id="b833d-103">Component developers can raise a subset of the events defined in the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> interface by calling the methods exposed on the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="b833d-104">您也可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 集合來定義自訂事件，然後在執行期間使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法來引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-104">You can also define custom events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection, and raise them during execution by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span> <span data-ttu-id="b833d-105">本章節描述如何建立及引發事件，並提供有關您在設計階段的何時應該引發事件的指引。</span><span class="sxs-lookup"><span data-stu-id="b833d-105">This section describes how to create and raise an event, and provides guidelines on when you should raise events at design time.</span></span>

## <a name="raising-events"></a><span data-ttu-id="b833d-106">引發事件</span><span class="sxs-lookup"><span data-stu-id="b833d-106">Raising Events</span></span>
 <span data-ttu-id="b833d-107">元件會使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面的 **Fire\<X>** 方法來引發事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-107">Components raise events by using the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span> <span data-ttu-id="b833d-108">您可以在元件的設計和執行期間引發事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-108">You can raise events during component design and execution.</span></span> <span data-ttu-id="b833d-109">一般在元件設計期間，<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> 方法會在驗證期間呼叫。</span><span class="sxs-lookup"><span data-stu-id="b833d-109">Typically, during component design, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A> methods are called during validation.</span></span> <span data-ttu-id="b833d-110">這些事件會在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的 [錯誤清單] 窗格內顯示訊息，並在元件設定不正確時提供意見給元件的使用者。</span><span class="sxs-lookup"><span data-stu-id="b833d-110">These events display messages in the **Error List** pane of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] and provide feedback to users of the component when a component is incorrectly configured.</span></span>

 <span data-ttu-id="b833d-111">元件也可以在執行期間的任何時間點引發事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-111">Components can also raise events at any point during execution.</span></span> <span data-ttu-id="b833d-112">事件可讓元件開發人員在執行元件時，提供意見給此元件的使用者。</span><span class="sxs-lookup"><span data-stu-id="b833d-112">Events allow component developers to provide feedback to users of the component as it executes.</span></span> <span data-ttu-id="b833d-113">在執行期間呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> 方法很可能會讓封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="b833d-113">Calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A> method during execution is likely to fail the package.</span></span>

## <a name="defining-and-raising-custom-events"></a><span data-ttu-id="b833d-114">定義及引發自訂事件</span><span class="sxs-lookup"><span data-stu-id="b833d-114">Defining and Raising Custom Events</span></span>

### <a name="defining-a-custom-event"></a><span data-ttu-id="b833d-115">定義自訂事件</span><span class="sxs-lookup"><span data-stu-id="b833d-115">Defining a Custom Event</span></span>
 <span data-ttu-id="b833d-116">自訂事件的建立是藉由呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b833d-116">Custom events are created by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.EventInfos%2A> collection.</span></span> <span data-ttu-id="b833d-117">這個集合是由資料流程工作所設定，並透過 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基底類別當做屬性提供給元件開發人員。</span><span class="sxs-lookup"><span data-stu-id="b833d-117">This collection is set by the data flow task and provided as a property to the component developer through the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class.</span></span> <span data-ttu-id="b833d-118">這個類別包含資料流程工作所定義的自訂事件，以及此元件在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法期間所定義的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-118">This class contains custom events defined by the data flow task and custom events defined by the component during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method.</span></span>

 <span data-ttu-id="b833d-119">元件的自訂事件不會保存在封裝 XML 中。</span><span class="sxs-lookup"><span data-stu-id="b833d-119">The custom events of a component are not persisted in the package XML.</span></span> <span data-ttu-id="b833d-120">因此，設計和執行期間會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法，好讓此元件定義它所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-120">Therefore, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method is called during both design and execution to allow the component to define the events it raises.</span></span>

 <span data-ttu-id="b833d-121"><xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> 方法的 *allowEventHandlers* 參數會指定此元件是否允許針對此事件建立 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件。</span><span class="sxs-lookup"><span data-stu-id="b833d-121">The *allowEventHandlers* parameter of the <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSEventInfos100.Add%2A> method specifies whether the component allows <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects to be created for the event.</span></span> <span data-ttu-id="b833d-122">請注意，<xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> 是同步的。</span><span class="sxs-lookup"><span data-stu-id="b833d-122">Note that <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> are synchronous.</span></span> <span data-ttu-id="b833d-123">因此，要等到附加至自訂事件的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 已經完成執行以後，此元件才會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b833d-123">Therefore the component does not resume execution until an <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> attached to the custom event has finished executing.</span></span> <span data-ttu-id="b833d-124">如果*allowEventHandlers*參數為 `true` ，事件的每個參數都會透過執行時間自動建立和擴展的變數，自動提供給任何 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> 物件使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b833d-124">If the *allowEventHandlers* parameter is `true`, each parameter of the event is automatically made available to any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> objects through variables that are created and populated automatically by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

### <a name="raising-a-custom-event"></a><span data-ttu-id="b833d-125">引發自訂事件</span><span class="sxs-lookup"><span data-stu-id="b833d-125">Raising a Custom Event</span></span>
 <span data-ttu-id="b833d-126">元件引發自訂事件的方式，是藉由呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法及提供此事件的名稱、文字和參數。</span><span class="sxs-lookup"><span data-stu-id="b833d-126">Components raise custom events by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method, and providing the name, text, and parameters of the event.</span></span> <span data-ttu-id="b833d-127">如果*allowEventHandlers*參數為 `true` ，則 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> 針對自訂事件所建立的任何都會由 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 執行時間引擎執行。</span><span class="sxs-lookup"><span data-stu-id="b833d-127">If the *allowEventHandlers* parameter is `true`, any <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandlers> that are created for the custom event are executed by the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] run-time engine.</span></span>

### <a name="custom-event-sample"></a><span data-ttu-id="b833d-128">自訂事件範例</span><span class="sxs-lookup"><span data-stu-id="b833d-128">Custom Event Sample</span></span>
 <span data-ttu-id="b833d-129">下列程式碼範例示範一個元件，此元件會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> 方法期間定義自訂事件，然後在執行階段藉由呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> 方法來引發此事件。</span><span class="sxs-lookup"><span data-stu-id="b833d-129">The following code example shows a component that defines a custom event during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.RegisterEvents%2A> method, and then raises the event at run time by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A> method.</span></span>

```csharp
public override void RegisterEvents()
{
    string [] parameterNames = new string[2]{"RowCount", "StartTime"};
    ushort [] parameterTypes = new ushort[2]{ DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)};
    string [] parameterDescriptions = new string[2]{"The number of rows to sort.", "The start time of the Sort operation."};
    EventInfos.Add("StartingSort","Fires when the component begins sorting the rows.",false,ref parameterNames, ref parameterTypes, ref parameterDescriptions);
}
public override void ProcessInput(int inputID, PipelineBuffer buffer)
{
    while (buffer.NextRow())
    {
       // Process buffer rows.
    }

    IDTSEventInfo100 eventInfo = EventInfos["StartingSort"];
    object []arguments = new object[2]{buffer.RowCount, DateTime.Now };
    ComponentMetaData.FireCustomEvent("StartingSort", "Beginning sort operation.", ref arguments, ComponentMetaData.Name, ref FireSortEventAgain);
}
```

```vb
Public  Overrides Sub RegisterEvents() 
  Dim parameterNames As String() = New String(2) {"RowCount", "StartTime"} 
  Dim parameterTypes As System.UInt16() = New System.UInt16(2) {DtsConvert.VarTypeFromTypeCode(TypeCode.Int32), DtsConvert.VarTypeFromTypeCode(TypeCode.DateTime)} 
  Dim parameterDescriptions As String() = New String(2) {"The number of rows to sort.", "The start time of the Sort operation."} 
  EventInfos.Add("StartingSort", "Fires when the component begins sorting the rows.", False, parameterNames, parameterTypes, parameterDescriptions) 
End Sub 

Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer) 
  While buffer.NextRow 
  End While 
  Dim eventInfo As IDTSEventInfo100 = EventInfos("StartingSort") 
  Dim arguments As Object() = New Object(2) {buffer.RowCount, DateTime.Now} 
  ComponentMetaData.FireCustomEvent("StartingSort", _
    "Beginning sort operation.", arguments, _
    ComponentMetaData.Name, FireSortEventAgain) 
End Sub
```

<span data-ttu-id="b833d-130">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b833d-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b833d-131">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b833d-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b833d-132">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b833d-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b833d-133">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b833d-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b833d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b833d-134">See Also</span></span>
 <span data-ttu-id="b833d-135">[Integration Services &#40;SSIS&#41; 事件處理](../../integration-services-ssis-event-handlers.md)程式[將事件處理常式新增至封裝](../../add-an-event-handler-to-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="b833d-135">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) [Add an Event Handler to a Package](../../add-an-event-handler-to-a-package.md)</span></span>


