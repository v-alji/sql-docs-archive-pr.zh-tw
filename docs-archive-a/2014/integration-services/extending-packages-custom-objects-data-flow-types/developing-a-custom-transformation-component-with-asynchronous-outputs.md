---
title: 開發具有非同步輸出的自訂轉換元件 | Microsoft Docs
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
- custom data flow components [Integration Services], transformation components
- asynchronous outputs [Integration Services]
- ProcessInput method
- cache [Integration Services]
- buffer allocations [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], transformation components
ms.assetid: 1c3e92c7-a4fa-4fdd-b9ca-ac3069536274
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41e2ecdf9f90765e75ff2b8c9c0681a25366e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705317"
---
# <a name="developing-a-custom-transformation-component-with-asynchronous-outputs"></a><span data-ttu-id="ad6e8-102">開發具有非同步輸出的自訂轉換元件</span><span class="sxs-lookup"><span data-stu-id="ad6e8-102">Developing a Custom Transformation Component with Asynchronous Outputs</span></span>
  <span data-ttu-id="ad6e8-103">當轉換在元件收到它的所有輸入資料列以前無法輸出資料料時，或是當轉換無法針對每一個收到的輸入資料列剛好產生一個輸出資料列時，您會使用非同步輸出。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-103">You use a component with asynchronous outputs when a transform cannot output rows until the component has received all its input rows, or when the transformation does not produce exactly one output row for each row received as input.</span></span> <span data-ttu-id="ad6e8-104">例如，彙總轉換要等到讀取所有資料列以後，才能計算資料列的總和。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-104">The Aggregate transformation, for example, cannot calculate a sum across rows until it has read all the rows.</span></span> <span data-ttu-id="ad6e8-105">相反地，每當您在資料通過時修改每一個資料列時，都可以搭配同步輸出來使用元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-105">In contrast, you can use a component with synchronous outputs any time when you modify each row of data as it passes through.</span></span> <span data-ttu-id="ad6e8-106">您可以就地修改每一個資料列的資料，或是建立一或多個其他新的資料行，每一個資料行對於每一個輸入資料列都有一個值。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-106">You can modify the data for each row in place, or you can create one or more new columns, each of which has a value for every one of the input rows.</span></span> <span data-ttu-id="ad6e8-107">如需同步與非同步元件之間差異的詳細資訊，請參閱[了解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-107">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="ad6e8-108">具有非同步輸出的轉換元件是唯一的，因為它們會同時當做目的地和來源元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-108">Transformation components with asynchronous outputs are unique because they act as both destination and source components.</span></span> <span data-ttu-id="ad6e8-109">這種元件會從上游元件收到資料列，並加入下游元件所耗用的資料列。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-109">This kind of component receives rows from upstream components, and adds rows that are consumed by downstream components.</span></span> <span data-ttu-id="ad6e8-110">沒有其他資料流程元件會執行這兩種作業。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-110">No other data flow component performs both of these operations.</span></span>

 <span data-ttu-id="ad6e8-111">可供具有同步輸出之元件使用之上游元件中的資料行會自動提供給此元件的下游元件使用。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-111">The columns from upstream components that are available to a component with synchronous outputs are automatically available to components downstream from the component.</span></span> <span data-ttu-id="ad6e8-112">因此，具有同步輸出的元件不必定義任何輸出資料行，也可提供資料行和資料列給下一個元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-112">Therefore, a component with synchronous outputs does not have to define any output columns to provide columns and rows to the next component.</span></span> <span data-ttu-id="ad6e8-113">就另一方面而言，具有非同步輸出的元件必須定義輸出資料行，並提供資料列給下游元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-113">Components with asynchronous outputs, on the other hand, must define output columns and provide rows to downstream components.</span></span> <span data-ttu-id="ad6e8-114">因此，具有非同步輸出的元件在設計和執行階段會有更多的工作要執行，而且元件開發人員會有更多的程式碼要實作。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-114">Therefore a component with asynchronous outputs has more tasks to perform during both design and execution time, and the component developer has more code to implement.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ad6e8-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含數個具有非同步輸出的轉換。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains several transformations with asynchronous outputs.</span></span> <span data-ttu-id="ad6e8-116">例如，排序轉換會先要求它的所有資料列，然後才能加以排序，並使用非同步輸出達成這個結果。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-116">For example, the Sort transformation requires all its rows before it can sort them, and achieves this by using asynchronous outputs.</span></span> <span data-ttu-id="ad6e8-117">當它收到所有資料列以後，它會加以排序並將其加入到輸出中。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-117">After it has received all its rows, it sorts them and adds them to its output.</span></span>

 <span data-ttu-id="ad6e8-118">本章節將詳細說明如何開發具有非同步輸出的轉換。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-118">This section explains in detail how to develop transformations with asynchronous outputs.</span></span> <span data-ttu-id="ad6e8-119">如需來源元件開發的詳細資訊，請參閱[開發自訂來源元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-119">For more information about source component development, see [Developing a Custom Source Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="ad6e8-120">設計階段</span><span class="sxs-lookup"><span data-stu-id="ad6e8-120">Design Time</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="ad6e8-121">建立元件</span><span class="sxs-lookup"><span data-stu-id="ad6e8-121">Creating the Component</span></span>
 <span data-ttu-id="ad6e8-122"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 物件上的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 屬性會識別輸出為同步或非同步。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property on the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object identifies whether an output is synchronous or asynchronous.</span></span> <span data-ttu-id="ad6e8-123">若要建立非同步輸出，請將輸出加入到元件中，並將 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 設定為零。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-123">To create an asynchronous output, add the output to the component and set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> to zero.</span></span> <span data-ttu-id="ad6e8-124">設定這個屬性也會決定資料流程工作是否會同時針對元件的輸入和輸出來配置 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 物件，或者是否會配置單一緩衝區並在兩個物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-124">Setting this property also determines whether the data flow task allocates <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects for both the input and output of the component, or whether a single buffer is allocated and shared between the two objects.</span></span>

 <span data-ttu-id="ad6e8-125">下列範例程式碼顯示一個元件，此元件會在它的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 實作中建立非同步輸出。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-125">The following sample code shows a component that creates an asynchronous output in its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> implementation.</span></span>

```csharp
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "AsyncComponent",ComponentType = ComponentType.Transform)]
    public class AsyncComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Call the base class, which adds a synchronous input
            // and output.
            base.ProvideComponentProperties();

            // Make the output asynchronous.
            IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
            output.SynchronousInputID = 0;
        }
    }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime

<DtsPipelineComponent(DisplayName:="AsyncComponent", ComponentType:=ComponentType.Transform)> _
Public Class AsyncComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Call the base class, which adds a synchronous input
        ' and output.
        Me.ProvideComponentProperties()

        ' Make the output asynchronous.
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
        output.SynchronousInputID = 0

    End Sub

End Class
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="ad6e8-126">建立和設定輸出資料行</span><span class="sxs-lookup"><span data-stu-id="ad6e8-126">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="ad6e8-127">如同之前所述，非同步元件會將資料行加入它的輸出資料行集合中，以提供資料行給下游元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-127">As mentioned earlier, an asynchronous component adds columns to its output column collection to provide columns to downstream components.</span></span> <span data-ttu-id="ad6e8-128">根據元件的需求而定，有幾種設計階段方法可供選擇。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-128">There are several design-time methods to choose from, depending on the needs of the component.</span></span> <span data-ttu-id="ad6e8-129">例如，如果您想要將上游元件中的所有資料行傳遞給下游元件，您會覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> 方法來加入資料行，因為這是可供此元件使用之輸入資料行中的第一個方法。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-129">For example, if you want to pass all the columns from the upstream components to the downstream components, you would override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.OnInputPathAttached%2A> method to add the columns, because this is the first method in which the input columns are available to the component.</span></span>

 <span data-ttu-id="ad6e8-130">如果此元件根據為其輸入選取的資料行來建立輸出資料行，請覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> 方法來選取輸出資料行，並指示將要如何使用這些資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-130">If the component creates output columns based on the columns selected for its input, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetUsageType%2A> method to select the output columns and to indicate how they will be used.</span></span>

 <span data-ttu-id="ad6e8-131">如果具有非同步輸出的元件根據上游元件中的資料行建立輸出資料行，而且可用的上游資料行變更了，則此元件應該更新它的輸出資料行集合。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-131">If a component with asynchronous outputs creates output columns based on the columns from upstream components, and the available upstream columns change, the component should update its output column collection.</span></span> <span data-ttu-id="ad6e8-132">此元件應該會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 期間偵測到這些變更，並在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 期間加以修正。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-132">These changes should be detected by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and fixed during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.</span></span>

> [!NOTE]
>  <span data-ttu-id="ad6e8-133">當從輸出資料行集合中移除輸出資料行時，資料流程中參考此資料行的下游元件會受到負面的影響。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-133">When an output column is removed from the output column collection, downstream components in the data flow that reference the column are adversely affected.</span></span> <span data-ttu-id="ad6e8-134">必須修復輸出資料行，而不能移除及重新建立此資料行，以免破壞下游元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-134">The output column must be repaired without removing and recreating the column to prevent breaking the downstream components.</span></span> <span data-ttu-id="ad6e8-135">例如，如果此資料行的資料類型已經變更，您必須更新資料類型。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-135">For example, if the data type of the column has changed, you must update the data type.</span></span>

 <span data-ttu-id="ad6e8-136">下列程式碼範例示範一個元件，此元件會針對上游元件中可用的每一個資料行將輸出資料行加入它的輸出資料行集合中。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-136">The following code example shows a component that adds an output column to its output column collection for each column available from the upstream component.</span></span>

```csharp
public override void OnInputPathAttached(int inputID)
{
   IDTSInput100 input = ComponentMetaData.InputCollection.GetObjectByID(inputID);
   IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
   IDTSVirtualInput100 vInput = input.GetVirtualInput();

   foreach (IDTSVirtualInputColumn100 vCol in vInput.VirtualInputColumnCollection)
   {
      IDTSOutputColumn100 outCol = output.OutputColumnCollection.New();
      outCol.Name = vCol.Name;
      outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage);
   }
}
```

```vb
Public Overrides Sub OnInputPathAttached(ByVal inputID As Integer)

    Dim input As IDTSInput100 = ComponentMetaData.InputCollection.GetObjectByID(inputID)
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput()

    For Each vCol As IDTSVirtualInputColumn100 In vInput.VirtualInputColumnCollection

        Dim outCol As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        outCol.Name = vCol.Name
        outCol.SetDataTypeProperties(vCol.DataType, vCol.Length, vCol.Precision, vCol.Scale, vCol.CodePage)

    Next
End Sub
```

## <a name="run-time"></a><span data-ttu-id="ad6e8-137">執行階段</span><span class="sxs-lookup"><span data-stu-id="ad6e8-137">Run Time</span></span>
 <span data-ttu-id="ad6e8-138">具有非同步輸出的元件也會在執行階段執行一連串與其他元件類型不同的方法。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-138">Components with asynchronous outputs also execute a different sequence of methods at run time than other types of components.</span></span> <span data-ttu-id="ad6e8-139">首先，它們是同時收到 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法呼叫的僅有元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-139">First, they are the only components that receive a call to both the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> methods.</span></span> <span data-ttu-id="ad6e8-140">具有非同步輸出的元件也會先要求所有內送資料列的存取權，然後才可以開始處理；因此，在已經讀取所有資料列以前，它們必須在內部快取輸入資料列。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-140">Components with asynchronous outputs also require access to all the incoming rows before they can start processing; therefore, they must cache the input rows internally until all rows have been read.</span></span> <span data-ttu-id="ad6e8-141">最後，具有非同步輸出的元件會同時收到輸入緩衝區和輸出緩衝區，與其他元件不同。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-141">Finally, unlike other components, components with asynchronous outputs receive both an input buffer and an output buffer.</span></span>

### <a name="understanding-the-buffers"></a><span data-ttu-id="ad6e8-142">了解緩衝區</span><span class="sxs-lookup"><span data-stu-id="ad6e8-142">Understanding the Buffers</span></span>
 <span data-ttu-id="ad6e8-143">此元件會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 期間收到輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-143">The input buffer is received by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span> <span data-ttu-id="ad6e8-144">此緩衝區包含了由上游元件加入到緩衝區的資料列。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-144">This buffer contains the rows added to the buffer by upstream components.</span></span> <span data-ttu-id="ad6e8-145">此緩衝區也包含元件輸入的資料行，同時還有之前在上游元件的輸出內所提供，但是未加入到非同步元件輸入集合中的資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-145">The buffer also contains the columns of the component's input, in addition to the columns that were provided in the output of an upstream component but were not added to the asynchronous component's input collection.</span></span>

 <span data-ttu-id="ad6e8-146">提供給 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 內之元件的輸出緩衝區一開始不包含資料列。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-146">The output buffer, which is provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, does not initially contain rows.</span></span> <span data-ttu-id="ad6e8-147">此元件會將資料列加入到這個緩衝區內，並在緩衝區已滿時將它提供給下游元件。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-147">The component adds rows to this buffer and provides the buffer to downstream components when it is full.</span></span> <span data-ttu-id="ad6e8-148">輸出緩衝區包含此元件的輸出資料行集合內所定義的資料行，同時還有其他下游元件已加入到其輸出內的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-148">The output buffer contains the columns defined in the component's output column collection, in addition to any columns that other downstream components have added to their outputs.</span></span>

 <span data-ttu-id="ad6e8-149">這個行為與具有同步輸出的元件不同，該元件會收到單一共用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-149">This is different behavior from that of components with synchronous outputs, which receive a single shared buffer.</span></span> <span data-ttu-id="ad6e8-150">具有同步輸出之元件的共用緩衝區包含了此元件的輸入和輸出資料行，同時還有加入到上游和下游元件之輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-150">The shared buffer of a component with synchronous outputs contains both the input and output columns of the component, in addition to columns added to the outputs of upstream and downstream components.</span></span>

### <a name="processing-rows"></a><span data-ttu-id="ad6e8-151">處理資料列</span><span class="sxs-lookup"><span data-stu-id="ad6e8-151">Processing Rows</span></span>

#### <a name="caching-input-rows"></a><span data-ttu-id="ad6e8-152">快取輸入資料列</span><span class="sxs-lookup"><span data-stu-id="ad6e8-152">Caching Input Rows</span></span>
 <span data-ttu-id="ad6e8-153">當您撰寫具有非同步輸出的元件時，您有三個選項可將資料列加入到輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-153">When you write a component with asynchronous outputs, you have three options for adding rows to the output buffer.</span></span> <span data-ttu-id="ad6e8-154">您可以將它們當做收到的輸入資料列來加入，也可以快取它們，直到此元件收到上游元件中的所有資料列為止，或者可以在適合此元件的時機加入它們。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-154">You can add them as input rows are received, you can cache them until the component has received all the rows from the upstream component, or you can add them when it is appropriate to do so for the component.</span></span> <span data-ttu-id="ad6e8-155">您所選擇的方法取決於此元件的需求。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-155">The method that you choose depends on the requirements of the component.</span></span> <span data-ttu-id="ad6e8-156">例如，排序元件需要收到所有的上游資料列，然後才可加以排序。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-156">For example, the Sort component requires that all the upstream rows be received before they can be sorted.</span></span> <span data-ttu-id="ad6e8-157">因此，將資料列加入到輸出緩衝區以前，它會等候所有的資料列都已讀取。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-157">Therefore, it waits until all rows have been read before adding rows to the output buffer.</span></span>

 <span data-ttu-id="ad6e8-158">此元件必須在內部快取輸入緩衝區內收到的資料列，直到準備處理這些資料列為止。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-158">The rows that are received in the input buffer must be cached internally by the component until it is ready to process them.</span></span> <span data-ttu-id="ad6e8-159">內送緩衝區資料列可以在資料表、多維度陣列或其他任何內部結構中快取。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-159">The incoming buffer rows can be cached in a data table, a multidimensional array, or any other internal structure.</span></span>

#### <a name="adding-output-rows"></a><span data-ttu-id="ad6e8-160">加入輸出資料列</span><span class="sxs-lookup"><span data-stu-id="ad6e8-160">Adding Output Rows</span></span>
 <span data-ttu-id="ad6e8-161">不論您在收到資料列時還是在收到所有資料列以後，將資料列加入到輸出緩衝區，您都可以在輸出緩衝區上呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> 方法來這樣做。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-161">Whether you add rows to the output buffer as they are received or after receiving all of the rows, you do so by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method on the output buffer.</span></span> <span data-ttu-id="ad6e8-162">當您加入此資料列以後，您會在新的資料列中設定每一個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-162">After you have added the row, you set the values of each column in the new row.</span></span>

 <span data-ttu-id="ad6e8-163">因為輸出緩衝區中的資料行有時會多於此元件之輸出資料行集合中的資料行，所以您必須先找出緩衝區內適當資料行的索引，然後才可以設定它的值。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-163">Because there are sometimes more columns in the output buffer than in the output column collection of the component, you must locate the index of the appropriate column in the buffer before you can set its value.</span></span> <span data-ttu-id="ad6e8-164"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 屬性的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法會傳回緩衝區資料列中具有指定之歷程識別碼的資料行索引，然後會用它來將此值指派給緩衝區資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-164">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property returns the index of the column in the buffer row with the specified lineage ID, which is then used to assign the value to the buffer column.</span></span>

 <span data-ttu-id="ad6e8-165">在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 方法或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法以前所呼叫的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法是 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 屬性可用時的第一個方法，以及在輸入和輸出緩衝區內尋找資料行之索引的第一個機會。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-165">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, which is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method or the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method, is the first method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property is available, and the first opportunity to locate the indexes of the columns in the input and output buffers.</span></span>

## <a name="sample"></a><span data-ttu-id="ad6e8-166">範例</span><span class="sxs-lookup"><span data-stu-id="ad6e8-166">Sample</span></span>
 <span data-ttu-id="ad6e8-167">下列範例顯示具有非同步輸出的簡單轉換元件，該元件會將收到的資料列加入到輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-167">The following sample shows a simple transformation component with asynchronous outputs that adds rows to the output buffer as they are received.</span></span> <span data-ttu-id="ad6e8-168">這個範例並未示範本主題中討論的所有方法與功能。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-168">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="ad6e8-169">而是示範每個具有非同步輸出的自訂轉換元件必須覆寫的重要方法，但是並不包含設計階段驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-169">It demonstrates the important methods that every custom transformation component with asynchronous outputs must override, but does not contain code for design-time validation.</span></span> <span data-ttu-id="ad6e8-170">此外，<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 中的程式碼會假設輸出資料行集合針對輸入資料行集合中的每一個資料行都有一個資料行。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-170">Also, the code in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> assumes that the output column collection has one column for each column in the input column collection.</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
   [DtsPipelineComponent(DisplayName = "AsynchronousOutput")]
   public class AsynchronousOutput : PipelineComponent
   {
      PipelineBuffer outputBuffer;
      int[] inputColumnBufferIndexes;
      int[] outputColumnBufferIndexes;

      public override void ProvideComponentProperties()
      {
         // Let the base class add the input and output objects.
         base.ProvideComponentProperties();

         // Name the input and output, and make the
         // output asynchronous.
         ComponentMetaData.InputCollection[0].Name = "Input";
         ComponentMetaData.OutputCollection[0].Name = "AsyncOutput";
         ComponentMetaData.OutputCollection[0].SynchronousInputID = 0;
      }
      public override void PreExecute()
      {
         IDTSInput100 input = ComponentMetaData.InputCollection[0];
         IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

         inputColumnBufferIndexes = new int[input.InputColumnCollection.Count];
         outputColumnBufferIndexes = new int[output.OutputColumnCollection.Count];

         for (int col = 0; col < input.InputColumnCollection.Count; col++)
            inputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection[col].LineageID);

         for (int col = 0; col < output.OutputColumnCollection.Count; col++)
            outputColumnBufferIndexes[col] = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[col].LineageID);

      }

      public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
      {
         if (buffers.Length != 0)
            outputBuffer = buffers[0];
      }
      public override void ProcessInput(int inputID, PipelineBuffer buffer)
      {
            // Advance the buffer to the next row.
            while (buffer.NextRow())
            {
               // Add a row to the output buffer.
               outputBuffer.AddRow();
               for (int x = 0; x < inputColumnBufferIndexes.Length; x++)
               {
                  // Copy the data from the input buffer column to the output buffer column.
                  outputBuffer[outputColumnBufferIndexes[x]] = buffer[inputColumnBufferIndexes[x]];
               }
            }
         if (buffer.EndOfRowset)
         {
            // EndOfRowset on the input buffer is true.
            // Set EndOfRowset on the output buffer.
            outputBuffer.SetEndOfRowset();
         }
      }
   }
}
```

```vb
Imports System
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

Namespace Microsoft.Samples.SqlServer.Dts

    <DtsPipelineComponent(DisplayName:="AsynchronousOutput")> _
    Public Class AsynchronousOutput

        Inherits PipelineComponent

        Private outputBuffer As PipelineBuffer
        Private inputColumnBufferIndexes As Integer()
        Private outputColumnBufferIndexes As Integer()

        Public Overrides Sub ProvideComponentProperties()

            ' Let the base class add the input and output objects.
            Me.ProvideComponentProperties()

            ' Name the input and output, and make the
            ' output asynchronous.
            ComponentMetaData.InputCollection(0).Name = "Input"
            ComponentMetaData.OutputCollection(0).Name = "AsyncOutput"
            ComponentMetaData.OutputCollection(0).SynchronousInputID = 0
        End Sub

        Public Overrides Sub PreExecute()

            Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)
            Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

            ReDim inputColumnBufferIndexes(input.InputColumnCollection.Count)
            ReDim outputColumnBufferIndexes(output.OutputColumnCollection.Count)

            For col As Integer = 0 To input.InputColumnCollection.Count
                inputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(input.Buffer, input.InputColumnCollection(col).LineageID)
            Next

            For col As Integer = 0 To output.OutputColumnCollection.Count
                outputColumnBufferIndexes(col) = BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(col).LineageID)
            Next

        End Sub
        Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

            If buffers.Length <> 0 Then
                outputBuffer = buffers(0)
            End If

        End Sub

        Public Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)

                ' Advance the buffer to the next row.
                While (buffer.NextRow())

                    ' Add a row to the output buffer.
                    outputBuffer.AddRow()
                    For x As Integer = 0 To inputColumnBufferIndexes.Length

                        ' Copy the data from the input buffer column to the output buffer column.
                        outputBuffer(outputColumnBufferIndexes(x)) = buffer(inputColumnBufferIndexes(x))

                    Next
                End While

            If buffer.EndOfRowset = True Then
                ' EndOfRowset on the input buffer is true.
                ' Set the end of row set on the output buffer.
                outputBuffer.SetEndOfRowset()
            End If
        End Sub
    End Class
End Namespace
```

<span data-ttu-id="ad6e8-171">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ad6e8-171">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ad6e8-172">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ad6e8-172">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ad6e8-173">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ad6e8-173">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ad6e8-174">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ad6e8-174">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad6e8-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad6e8-175">See Also</span></span>
 <span data-ttu-id="ad6e8-176">[開發具有同步輸出的自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)[瞭解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)[使用腳本元件建立異步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span><span class="sxs-lookup"><span data-stu-id="ad6e8-176">[Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)</span></span>


