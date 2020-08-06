---
title: 資料流程元件的執行階段方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- run-time [Integration Services]
- data flow components [Integration Services], run-time methods
ms.assetid: fd9e4317-18dd-43af-bbdc-79db32183ac4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df0afe4c29044541c5a57aa3a466283ab4fe4fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703202"
---
# <a name="run-time-methods-of-a-data-flow-component"></a><span data-ttu-id="179fe-102">資料流程元件的執行階段方法</span><span class="sxs-lookup"><span data-stu-id="179fe-102">Run-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="179fe-103">在執行階段，資料流程工作會檢查元件的順序、準備執行計畫，以及管理執行工作計畫的工作者執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="179fe-103">At run time, the data flow task examines the sequence of components, prepares an execution plan, and manages a pool of worker threads that execute the work plan.</span></span> <span data-ttu-id="179fe-104">此工作會從來源載入資料列、透過轉換處理它們，然後將它們儲存到目的地。</span><span class="sxs-lookup"><span data-stu-id="179fe-104">The task loads rows of data from sources, processes them through transformations, then saves them to destinations.</span></span>  
  
## <a name="sequence-of-method-execution"></a><span data-ttu-id="179fe-105">方法執行的順序</span><span class="sxs-lookup"><span data-stu-id="179fe-105">Sequence of Method Execution</span></span>  
 <span data-ttu-id="179fe-106">在資料流程元件的執行期間，會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基底類別中的方法子集。</span><span class="sxs-lookup"><span data-stu-id="179fe-106">During the execution of a data flow component, a subset of the methods in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is called.</span></span> <span data-ttu-id="179fe-107">方法與呼叫方法的順序永遠都是相同的，但 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法例外。</span><span class="sxs-lookup"><span data-stu-id="179fe-107">The methods, and the sequence in which they are called, are always the same, with the exception of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="179fe-108">會根據元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 物件之存在與否及組態來呼叫這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="179fe-108">These two methods are called based on the existence and configuration of a component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> objects.</span></span>  
  
 <span data-ttu-id="179fe-109">下列清單按照元件執行期間呼叫方法的順序來顯示它們。</span><span class="sxs-lookup"><span data-stu-id="179fe-109">The following list shows the methods in the order in which they are called during component execution.</span></span> <span data-ttu-id="179fe-110">請注意，在呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 時，永遠會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 的前面呼叫它。</span><span class="sxs-lookup"><span data-stu-id="179fe-110">Note that <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, when called, is always called before <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrepareForExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PostExecute%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Cleanup%2A>  
  
### <a name="primeoutput-method"></a><span data-ttu-id="179fe-111">PrimeOutput 方法</span><span class="sxs-lookup"><span data-stu-id="179fe-111">PrimeOutput Method</span></span>  
 <span data-ttu-id="179fe-112">當元件至少有一個輸出透過 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> 物件附加至下游元件，而且輸出的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 屬性是零時，便會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="179fe-112">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called when a component has at least one output, attached to a downstream component through an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object, and the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property of the output is zero.</span></span> <span data-ttu-id="179fe-113"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> 方法是針對來源元件以及具有非同步輸出的轉換所呼叫。</span><span class="sxs-lookup"><span data-stu-id="179fe-113">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.PrimeOutput%2A> method is called for source components and for transformations with asynchronous outputs.</span></span> <span data-ttu-id="179fe-114">與以下所述的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法不同的是，每個需要 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法的元件都只會呼叫它一次。</span><span class="sxs-lookup"><span data-stu-id="179fe-114">Unlike the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method described below, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is only called once for each component that requires it.</span></span>  
  
### <a name="processinput-method"></a><span data-ttu-id="179fe-115">ProcessInput 方法</span><span class="sxs-lookup"><span data-stu-id="179fe-115">ProcessInput Method</span></span>  
 <span data-ttu-id="179fe-116">如果元件至少有一個輸入是由 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 物件附加至上游元件，則會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 方法。</span><span class="sxs-lookup"><span data-stu-id="179fe-116">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for components that have at least one input attached to an upstream component by an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> object.</span></span> <span data-ttu-id="179fe-117"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> 方法是針對目的地元件以及具有同步輸出的轉換所呼叫。</span><span class="sxs-lookup"><span data-stu-id="179fe-117">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100.ProcessInput%2A> method is called for destination components and for transformations with synchronous outputs.</span></span> <span data-ttu-id="179fe-118">會重複呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>，直到不再從上游元件處理資料列為止。</span><span class="sxs-lookup"><span data-stu-id="179fe-118"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> is called repeatedly until there are no more rows to process from upstream components.</span></span>  
  
## <a name="working-with-inputs-and-outputs"></a><span data-ttu-id="179fe-119">處理輸入和輸出</span><span class="sxs-lookup"><span data-stu-id="179fe-119">Working with Inputs and Outputs</span></span>  
 <span data-ttu-id="179fe-120">在執行階段，資料流程元件會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="179fe-120">At run time, data flow components perform the following tasks:</span></span>  
  
-   <span data-ttu-id="179fe-121">來源元件會加入資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-121">Source components add rows.</span></span>  
  
-   <span data-ttu-id="179fe-122">具有同步輸出的轉換元件會接收來源元件所提供的資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-122">Transformation components with synchronous outputs receive rows provided by source components.</span></span>  
  
-   <span data-ttu-id="179fe-123">具有非同步輸出的轉換元件會接收資料列並加入資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-123">Transformation components with asynchronous outputs receive rows and add rows.</span></span>  
  
-   <span data-ttu-id="179fe-124">目的地元件會接收資料列，然後將它們載入目的地中。</span><span class="sxs-lookup"><span data-stu-id="179fe-124">Destination components receive rows and then load them into a destination.</span></span>  
  
 <span data-ttu-id="179fe-125">在執行期間，資料流程工作會配置 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 物件，這些物件包含定義在元件序列之輸出資料行集合中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="179fe-125">During execution, the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain all the columns defined in the output column collections of a sequence of components.</span></span> <span data-ttu-id="179fe-126">例如，如果資料流程序列中四個元件的每一個都會將一個輸出資料行加入至其輸出資料行集合，則提供給每個元件的緩衝區都會包含四個資料行，其中每個元件的每個輸出資料行都有一個資料行。</span><span class="sxs-lookup"><span data-stu-id="179fe-126">For example, if each of four components in a data flow sequence adds one output column to its output column collection,the buffer that is provided to each component contains four columns, one for each output column per component.</span></span> <span data-ttu-id="179fe-127">因為這個行為的緣故，元件有時會接收包含未使用之資料行的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="179fe-127">Because of this behavior, a component sometimes receives buffers that contain columns it does not use.</span></span>  
  
 <span data-ttu-id="179fe-128">因為元件所接收的緩衝區可能包含此元件將不會使用的資料行，所以您必須在資料流程工作提供給此元件的緩衝區中，找到要在元件的輸入與輸出資料行集合中使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="179fe-128">Since the buffers received by your component may contain columns that the component will not use, you must locate the columns that you want to use in your component's input and output column collections in the buffer provided to the component by the data flow task.</span></span> <span data-ttu-id="179fe-129">您可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 屬性的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法來完成這項動作。</span><span class="sxs-lookup"><span data-stu-id="179fe-129">You do this by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property.</span></span> <span data-ttu-id="179fe-130">基於效能的考量，這個工作通常會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 方法期間執行，而不是在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 中執行。</span><span class="sxs-lookup"><span data-stu-id="179fe-130">For performance reasons, this task is ordinarily performed during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, rather than in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
 <span data-ttu-id="179fe-131">在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法之前，會先呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>，而且是在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 變成可供元件使用之後，元件第一次有機會執行這個工作。</span><span class="sxs-lookup"><span data-stu-id="179fe-131"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods, and is the first opportunity for a component to perform this work after the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> becomes available to the component.</span></span> <span data-ttu-id="179fe-132">在這個方法期間，元件應該在緩衝區中找到其資料行，並在內部儲存這項資訊，以便在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法中可以使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="179fe-132">During this method, the component should locate its columns in the buffers and store this information internally so the columns can be used in either the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span>  
  
 <span data-ttu-id="179fe-133">下列程式碼範例示範在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期間，具有同步輸出的轉換元件如何在緩衝區中找到其輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="179fe-133">The following code example demonstrates how a transformation component with a synchronous output locates its input columns in the buffer during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span>  
  
```csharp  
private int []bufferColumnIndex;  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    bufferColumnIndex = new int[input.InputColumnCollection.Count];  
  
    for( int x=0; x < input.InputColumnCollection.Count; x++)  
    {  
        IDTSInputColumn100 column = input.InputColumnCollection[x];  
        bufferColumnIndex[x] = BufferManager.FindColumnByLineageID( input.Buffer, column.LineageID);  
    }  
}  
```  
  
```vb  
Dim bufferColumnIndex As Integer()  
  
    Public Overrides Sub PreExecute()  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
  
        ReDim bufferColumnIndex(input.InputColumnCollection.Count)  
  
        For x As Integer = 0 To input.InputColumnCollection.Count  
  
            Dim column As IDTSInputColumn100 = input.InputColumnCollection(x)  
            bufferColumnIndex(x) = BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID)  
  
        Next  
  
    End Sub  
```  
  
### <a name="adding-rows"></a><span data-ttu-id="179fe-134">加入資料列</span><span class="sxs-lookup"><span data-stu-id="179fe-134">Adding Rows</span></span>  
 <span data-ttu-id="179fe-135">透過將資料列加入至 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 物件，元件會提供資料列給下游元件。</span><span class="sxs-lookup"><span data-stu-id="179fe-135">Components supply rows to downstream components by adding rows to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="179fe-136">資料流程工作會提供輸出緩衝區的陣列，每個連接至下游元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 物件都有一個輸出緩衝區，以做為 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法的參數。</span><span class="sxs-lookup"><span data-stu-id="179fe-136">The data flow task provides an array of output buffers - one for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that is connected to a downstream component - as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method.</span></span> <span data-ttu-id="179fe-137">具有非同步輸出的來源元件與轉換元件會將資料列加入至緩衝區，並且會在完成加入資料列時呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="179fe-137">Source components and transformation components with asynchronous outputs add rows to the buffers and call the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method when they are finished adding rows.</span></span> <span data-ttu-id="179fe-138">資料流程工作會管理提供給元件的輸出緩衝區，而當緩衝區變成完整時，便會自動將緩衝區中的資料列移到下一個元件。</span><span class="sxs-lookup"><span data-stu-id="179fe-138">The data flow task manages the output buffers that it supplies to components and, as a buffer becomes full, automatically moves the rows in the buffer to the next component.</span></span> <span data-ttu-id="179fe-139">每個元件都會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法一次，不像 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法一樣重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="179fe-139">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method is called one time per component, unlike  the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, which is called repeatedly.</span></span>  
  
 <span data-ttu-id="179fe-140">下列程式碼範例示範在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法期間，元件會如何將資料列加入至其輸出緩衝區，然後呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="179fe-140">The following code example demonstrates how a component adds rows to its output buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method, then calls the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method.</span></span>  
  
```csharp  
public override void PrimeOutput( int outputs, int []outputIDs,PipelineBuffer []buffers)  
{  
    for( int x=0; x < outputs; x++ )  
    {  
        IDTSOutput100 output = ComponentMetaData.OutputCollection.GetObjectByID( outputIDs[x]);  
        PipelineBuffer buffer = buffers[x];  
  
        // TODO: Add rows to the output buffer.  
    }  
    foreach( PipelineBuffer buffer in buffers )  
    {  
        /// Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset();  
    }  
}  
```  
  
```vb  
public overrides sub PrimeOutput( outputs as Integer , outputIDs() as Integer ,buffers() as PipelineBuffer buffers)  
  
    For x As Integer = 0 To outputs.MaxValue  
  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.GetObjectByID(outputIDs(x))  
        Dim buffer As PipelineBuffer = buffers(x)  
  
        ' TODO: Add rows to the output buffer.  
  
    Next  
  
    For Each buffer As PipelineBuffer In buffers  
  
        ' Notify the data flow task that no more rows are coming.  
        buffer.SetEndOfRowset()  
  
    Next  
  
End Sub  
```  
  
 <span data-ttu-id="179fe-141">如需開發將資料列新增至輸出緩衝區之元件的詳細資訊，請參閱[開發自訂來源元件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)和[開發具有非同步輸出的自訂轉換元件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)。</span><span class="sxs-lookup"><span data-stu-id="179fe-141">For more information about developing components that add rows to output buffers, see [Developing a Custom Source Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md) and [Developing a Custom Transformation Component with Asynchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).</span></span>  
  
### <a name="receiving-rows"></a><span data-ttu-id="179fe-142">接收資料列</span><span class="sxs-lookup"><span data-stu-id="179fe-142">Receiving Rows</span></span>  
 <span data-ttu-id="179fe-143">元件會從 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 物件中的上游元件接收資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-143">Components receive rows from upstream components in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects.</span></span> <span data-ttu-id="179fe-144">資料流程工作會提供 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 物件，該物件包含上游元件以 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法的參數形式加入至資料流程的資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-144">The data flow task provides a <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> object that contains the rows added to the data flow by upstream components as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="179fe-145">這個輸入緩衝區可用以檢查和修改緩衝區中的資料列與資料行，但是無法用以加入或是移除資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-145">This input buffer can be used to examine and modify the rows and columns in the buffer, but cannot be used to add or remove rows.</span></span> <span data-ttu-id="179fe-146"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法會重複呼叫，直到沒有其他可用的緩衝區為止。</span><span class="sxs-lookup"><span data-stu-id="179fe-146">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method is called repeatedly until there are no more available buffers.</span></span> <span data-ttu-id="179fe-147">上次呼叫它時，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 屬性是 `true`。</span><span class="sxs-lookup"><span data-stu-id="179fe-147">The last time it is called, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property is `true`.</span></span> <span data-ttu-id="179fe-148">您可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 方法，使緩衝區前進到下一個資料列，以逐一查看緩衝區中的資料列集合。</span><span class="sxs-lookup"><span data-stu-id="179fe-148">You can iterate over the collection of rows in the buffer by using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method, which advances the buffer to the next row.</span></span> <span data-ttu-id="179fe-149">當緩衝區位於集合中的最後一個資料列時，此方法會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="179fe-149">This method returns `false` when the buffer is on the last row in the collection.</span></span> <span data-ttu-id="179fe-150">除非您在已處理最後一個資料列之後還必須執行其他動作，否則不必檢查 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="179fe-150">You do not have to check the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property unless you have to perform an additional action after the last rows of data have been processed.</span></span>  
  
 <span data-ttu-id="179fe-151">下列文字將示範使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> 方法和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> 屬性的正確模式：</span><span class="sxs-lookup"><span data-stu-id="179fe-151">The following text shows the correct pattern for using the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.NextRow%2A> method and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> property:</span></span>  
  
 `while (buffer.NextRow())`  
  
 `{`  
  
 `// Do something with each row.`  
  
 `}`  
  
 `if (buffer.EndOfRowset)`  
  
 `{`  
  
 `// Optionally, do something after all rows have been processed.`  
  
 `}`  
  
 <span data-ttu-id="179fe-152">下列程式碼範例示範元件如何在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法期間，處理輸入緩衝區中的資料列。</span><span class="sxs-lookup"><span data-stu-id="179fe-152">The following code example demonstrates how a component processes the rows in input buffers during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span>  
  
```csharp  
public override void ProcessInput( int inputID, PipelineBuffer buffer )  
{  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);  
        while( buffer.NextRow())  
        {  
            // TODO: Examine the columns in the current row.  
        }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)  
  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)  
        While buffer.NextRow() = True  
  
            ' TODO: Examine the columns in the current row.  
        End While  
  
End Sub  
```  
  
 <span data-ttu-id="179fe-153">如需開發接收輸入緩衝區中資料列之元件的詳細資訊，請參閱[開發自訂目的地元件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)和[開發具有同步輸出的自訂轉換元件](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)。</span><span class="sxs-lookup"><span data-stu-id="179fe-153">For more information about developing components that receive rows in input buffers, see [Developing a Custom Destination Component](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) and [Developing a Custom Transformation Component with Synchronous Outputs](../../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>  
  
<span data-ttu-id="179fe-154">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="179fe-154">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="179fe-155">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="179fe-155">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="179fe-156">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="179fe-156">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="179fe-157">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="179fe-157">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179fe-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179fe-158">See Also</span></span>  
 [<span data-ttu-id="179fe-159">資料流程元件的設計階段方法</span><span class="sxs-lookup"><span data-stu-id="179fe-159">Design-time Methods of a Data Flow Component</span></span>](design-time-methods-of-a-data-flow-component.md)  
  
  
