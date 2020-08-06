---
title: 開發具有同步輸出的自訂轉換元件 | Microsoft Docs
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
- ProcessInput method
- buffer allocations [Integration Services]
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- output columns [Integration Services]
- data flow components [Integration Services], transformation components
ms.assetid: b694d21f-9919-402d-9192-666c6449b0b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 94d78872570103d3df7e1cb96aecb144fafe4257
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705318"
---
# <a name="developing-a-custom-transformation-component-with-synchronous-outputs"></a><span data-ttu-id="b10cc-102">開發具有同步輸出的自訂轉換元件</span><span class="sxs-lookup"><span data-stu-id="b10cc-102">Developing a Custom Transformation Component with Synchronous Outputs</span></span>
  <span data-ttu-id="b10cc-103">具有同步輸出的轉換元件會從上游元件接收資料列，並在傳遞資料列給下游元件時，讀取或是修改這些資料列之資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="b10cc-103">Transformation components with synchronous outputs receive rows from upstream components, and read or modify the values in the columns of these rows as they pass the rows to downstream components.</span></span> <span data-ttu-id="b10cc-104">它們也必須定義從上游元件提供的資料行所衍生之其他輸出資料行，但是它們不需要將資料列加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="b10cc-104">They may also define additional output columns that are derived from the columns provided by upstream components, but they do not add rows to the data flow.</span></span> <span data-ttu-id="b10cc-105">如需同步與非同步元件之間差異的詳細資訊，請參閱[了解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="b10cc-105">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>  
  
 <span data-ttu-id="b10cc-106">這種元件適用於將資料提供給元件時以內嵌方式修改資料的工作，以及元件不必看到所有的資料列就能處理它們的工作。</span><span class="sxs-lookup"><span data-stu-id="b10cc-106">This kind of component is suited for tasks where the data is modified inline as it is provided to the component and where the component does not have to see all the rows before processing them.</span></span> <span data-ttu-id="b10cc-107">它是最容易開發的元件，因為具有同步輸出的轉換通常不會連接至外部資料來源、管理外部中繼資料行，或是將資料列加入輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b10cc-107">It is the easiest component to develop because transformations with synchronous outputs typically do not connect to external data sources, manage external metadata columns, or add rows to output buffers.</span></span>  
  
 <span data-ttu-id="b10cc-108">建立具有同步輸出的轉換元件需要加入含有為元件選取的上游資料行之 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>，以及可能包含由元件建立的衍生資料行之 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 物件。</span><span class="sxs-lookup"><span data-stu-id="b10cc-108">Creating a transformation component with synchronous outputs involves adding an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> that will contain the upstream columns selected for the component, and a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> object that may contain derived columns created by the component.</span></span> <span data-ttu-id="b10cc-109">建立的過程也包括實作設計階段方法，並提供執行期間在內送緩衝區資料列中讀取或修改資料行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b10cc-109">It also includes implementing the design-time methods, and providing code that reads or modifies the columns in the incoming buffer rows during execution.</span></span>  
  
 <span data-ttu-id="b10cc-110">本節提供實作自訂轉換元件所需的資訊，並提供程式碼範例以協助您更加了解概念。</span><span class="sxs-lookup"><span data-stu-id="b10cc-110">This section provides the information that is required to implement a custom transformation component, and provides code examples to help you better understand the concepts.</span></span>  
  
## <a name="design-time"></a><span data-ttu-id="b10cc-111">設計階段</span><span class="sxs-lookup"><span data-stu-id="b10cc-111">Design Time</span></span>  
 <span data-ttu-id="b10cc-112">這個元件的設計階段程式碼需要建立輸入和輸出，加入元件產生的任何其他輸出資料行，並驗證元件的組態。</span><span class="sxs-lookup"><span data-stu-id="b10cc-112">The design-time code for this component involves creating the inputs and outputs, adding any additional output columns that the component generates, and validating the configuration of the component.</span></span>  
  
### <a name="creating-the-component"></a><span data-ttu-id="b10cc-113">建立元件</span><span class="sxs-lookup"><span data-stu-id="b10cc-113">Creating the Component</span></span>  
 <span data-ttu-id="b10cc-114">元件的輸入、輸出和自訂屬性通常會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法期間建立。</span><span class="sxs-lookup"><span data-stu-id="b10cc-114">The inputs, outputs, and custom properties of the component are typically created during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="b10cc-115">有兩種方法可以加入具有同步輸出的轉換元件之輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="b10cc-115">There are two ways that you can add the input and the output of a transformation component with synchronous outputs.</span></span> <span data-ttu-id="b10cc-116">您可以使用該方法的基底類別實作，然後修改它建立的預設輸入和輸出，或者可以自己明確地加入輸入與輸出。</span><span class="sxs-lookup"><span data-stu-id="b10cc-116">You can use the base class implementation of the method and then modify the default input and output that it creates, or you can explicitly add the input and output yourself.</span></span>  
  
 <span data-ttu-id="b10cc-117">下列程式碼範例顯示 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 的實作，以明確地加入輸入和輸出物件。</span><span class="sxs-lookup"><span data-stu-id="b10cc-117">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that explicitly adds the input and output objects.</span></span> <span data-ttu-id="b10cc-118">註解中包含的對基底類別的呼叫也可以完成同一件事情。</span><span class="sxs-lookup"><span data-stu-id="b10cc-118">The call to the base class that would accomplish the same thing is included in a comment.</span></span>  
  
```csharp  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SynchronousComponent", ComponentType = ComponentType.Transform)]  
    public class SyncComponent : PipelineComponent  
    {  
  
        public override void ProvideComponentProperties()  
        {  
            // Add the input.  
            IDTSInput100 input = ComponentMetaData.InputCollection.New();  
            input.Name = "Input";  
  
            // Add the output.  
            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();  
            output.Name = "Output";  
            output.SynchronousInputID = input.ID;  
  
            // Alternatively, you can let the base class add the input and output  
            // and set the SynchronousInputID of the output to the ID of the input.  
            // base.ProvideComponentProperties();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsPipelineComponent(DisplayName:="SynchronousComponent", ComponentType:=ComponentType.Transform)> _  
Public Class SyncComponent  
    Inherits PipelineComponent  
  
    Public Overrides Sub ProvideComponentProperties()  
  
        ' Add the input.  
        Dim input As IDTSInput100 = ComponentMetaData.InputCollection.New()  
        input.Name = "Input"  
  
        ' Add the output.  
        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()  
        output.Name = "Output"  
        output.SynchronousInputID = Input.ID  
  
        ' Alternatively, you can let the base class add the input and output  
        ' and set the SynchronousInputID of the output to the ID of the input.  
        ' base.ProvideComponentProperties();  
  
    End Sub  
  
End Class  
```  
  
### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="b10cc-119">建立和設定輸出資料行</span><span class="sxs-lookup"><span data-stu-id="b10cc-119">Creating and Configuring Output Columns</span></span>  
 <span data-ttu-id="b10cc-120">雖然具有同步輸出的轉換元件不會將資料列加入緩衝區，但是它們可能會將額外的輸出資料行加入其輸出。</span><span class="sxs-lookup"><span data-stu-id="b10cc-120">Although transformation components with synchronous outputs do not add rows to buffers, they may add extra output columns to their output.</span></span> <span data-ttu-id="b10cc-121">一般而言，當元件加入輸出資料行時，會在執行階段從上游元件提供給該元件之一或多個資料行所含的資料中，衍生新輸出資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b10cc-121">Typically, when a component adds an output column, the values for the new output column are derived at run time from the data that is contained in one or more of the columns provided to the component by an upstream component.</span></span>  
  
 <span data-ttu-id="b10cc-122">在建立輸出資料行之後，必須設定其資料類型屬性。</span><span class="sxs-lookup"><span data-stu-id="b10cc-122">After an output column has been created, its data type properties must be set.</span></span> <span data-ttu-id="b10cc-123">設定輸出資料行的資料類型屬性需要特殊的處理，而且是透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> 方法來執行。</span><span class="sxs-lookup"><span data-stu-id="b10cc-123">Setting the data type properties of an output column requires special handling and is performed by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="b10cc-124">這個方法是必要的，因為 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> 屬性每個都是唯讀的，而且每個屬性都與另一個屬性的設定相依。</span><span class="sxs-lookup"><span data-stu-id="b10cc-124">This method is required because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are individually read-only, because each depends on the settings of the other.</span></span> <span data-ttu-id="b10cc-125">這個方法保證以一致的方式設定屬性值，而且資料流程工作會驗證它們是否已正確設定。</span><span class="sxs-lookup"><span data-stu-id="b10cc-125">This method guarantees that the values of the properties are set consistently, and the data flow task validates that they are set correctly.</span></span>  
  
 <span data-ttu-id="b10cc-126">資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 會決定為其他屬性設定的值。</span><span class="sxs-lookup"><span data-stu-id="b10cc-126">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="b10cc-127">下表顯示每個 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 的相依屬性之需求。</span><span class="sxs-lookup"><span data-stu-id="b10cc-127">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="b10cc-128">未列出的資料類型會將其相依屬性設定為零。</span><span class="sxs-lookup"><span data-stu-id="b10cc-128">The data types not listed have their dependent properties set to zero.</span></span>  
  
|<span data-ttu-id="b10cc-129">DataType</span><span class="sxs-lookup"><span data-stu-id="b10cc-129">DataType</span></span>|<span data-ttu-id="b10cc-130">長度</span><span class="sxs-lookup"><span data-stu-id="b10cc-130">Length</span></span>|<span data-ttu-id="b10cc-131">調整</span><span class="sxs-lookup"><span data-stu-id="b10cc-131">Scale</span></span>|<span data-ttu-id="b10cc-132">Precision</span><span class="sxs-lookup"><span data-stu-id="b10cc-132">Precision</span></span>|<span data-ttu-id="b10cc-133">CodePage</span><span class="sxs-lookup"><span data-stu-id="b10cc-133">CodePage</span></span>|  
|--------------|------------|-----------|---------------|--------------|  
|<span data-ttu-id="b10cc-134">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="b10cc-134">DT_DECIMAL</span></span>|<span data-ttu-id="b10cc-135">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-135">0</span></span>|<span data-ttu-id="b10cc-136">大於 0，且小於或等於 28。</span><span class="sxs-lookup"><span data-stu-id="b10cc-136">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="b10cc-137">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-137">0</span></span>|<span data-ttu-id="b10cc-138">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-138">0</span></span>|  
|<span data-ttu-id="b10cc-139">DT_CY</span><span class="sxs-lookup"><span data-stu-id="b10cc-139">DT_CY</span></span>|<span data-ttu-id="b10cc-140">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-140">0</span></span>|<span data-ttu-id="b10cc-141">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-141">0</span></span>|<span data-ttu-id="b10cc-142">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-142">0</span></span>|<span data-ttu-id="b10cc-143">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-143">0</span></span>|  
|<span data-ttu-id="b10cc-144">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="b10cc-144">DT_NUMERIC</span></span>|<span data-ttu-id="b10cc-145">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-145">0</span></span>|<span data-ttu-id="b10cc-146">大於 0、小於或等於 28，且小於有效位數 (Precision)。</span><span class="sxs-lookup"><span data-stu-id="b10cc-146">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="b10cc-147">大於或等於 1，且小於或等於 38。</span><span class="sxs-lookup"><span data-stu-id="b10cc-147">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="b10cc-148">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-148">0</span></span>|  
|<span data-ttu-id="b10cc-149">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="b10cc-149">DT_BYTES</span></span>|<span data-ttu-id="b10cc-150">大於 0。</span><span class="sxs-lookup"><span data-stu-id="b10cc-150">Greater than 0.</span></span>|<span data-ttu-id="b10cc-151">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-151">0</span></span>|<span data-ttu-id="b10cc-152">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-152">0</span></span>|<span data-ttu-id="b10cc-153">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-153">0</span></span>|  
|<span data-ttu-id="b10cc-154">DT_STR</span><span class="sxs-lookup"><span data-stu-id="b10cc-154">DT_STR</span></span>|<span data-ttu-id="b10cc-155">大於 0 且小於 8000。</span><span class="sxs-lookup"><span data-stu-id="b10cc-155">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="b10cc-156">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-156">0</span></span>|<span data-ttu-id="b10cc-157">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-157">0</span></span>|<span data-ttu-id="b10cc-158">非 0，並為有效的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="b10cc-158">Not 0, and a valid code page.</span></span>|  
|<span data-ttu-id="b10cc-159">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="b10cc-159">DT_WSTR</span></span>|<span data-ttu-id="b10cc-160">大於 0，且小於 4000。</span><span class="sxs-lookup"><span data-stu-id="b10cc-160">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="b10cc-161">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-161">0</span></span>|<span data-ttu-id="b10cc-162">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-162">0</span></span>|<span data-ttu-id="b10cc-163">0</span><span class="sxs-lookup"><span data-stu-id="b10cc-163">0</span></span>|  
  
 <span data-ttu-id="b10cc-164">由於資料類型屬性的限制會以輸出資料行的資料類型為準，因此在使用 Managed 類型時，必須選擇正確的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b10cc-164">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="b10cc-165">基底類別提供三種 Helper 方法：<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>，可協助 Managed 元件開發人員在有提供 Managed 類型時，選取 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b10cc-165">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A> that assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="b10cc-166">這些方法會將 Managed 資料類型轉換為 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="b10cc-166">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="b10cc-167">執行階段</span><span class="sxs-lookup"><span data-stu-id="b10cc-167">Run Time</span></span>  
 <span data-ttu-id="b10cc-168">一般而言，元件之執行階段部分的實作可分成兩項工作：在緩衝區中尋找元件的輸入與輸出資料行，以及在內送緩衝區資料列中讀取或寫入這些資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b10cc-168">Generally, the implementation of the run-time part of the component is categorized into two tasks-locating the input and output columns of the component in the buffer, and reading or writing the values of these columns in the incoming buffer rows.</span></span>  
  
### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="b10cc-169">找出緩衝區中的資料行</span><span class="sxs-lookup"><span data-stu-id="b10cc-169">Locating Columns in the Buffer</span></span>  
 <span data-ttu-id="b10cc-170">在執行期間提供給元件的緩衝區中之資料行數目，有可能超過元件之輸入或輸出集合中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="b10cc-170">The number of columns in the buffers that are provided to a component during execution will likely exceed the number of columns in the input or output collections of the component.</span></span> <span data-ttu-id="b10cc-171">這是因為每個緩衝區都包含資料流程的元件中定義的所有輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="b10cc-171">This is because each buffer contains all the output columns defined in the components in a data flow.</span></span> <span data-ttu-id="b10cc-172">為了確保緩衝區資料行正確地符合輸入或輸出的資料行，元件開發人員必須使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b10cc-172">To ensure that the buffer columns are correctly matched to the columns of the input or output, component developers must use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="b10cc-173">這個方法會使用資料行的歷程識別碼來尋找指定緩衝區中的資料行。</span><span class="sxs-lookup"><span data-stu-id="b10cc-173">This method locates a column in the specified buffer by its lineage ID.</span></span> <span data-ttu-id="b10cc-174">一般而言，會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期間找到資料行，因為這是 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 屬性變成可用的第一個執行階段方法。</span><span class="sxs-lookup"><span data-stu-id="b10cc-174">Typically columns are located during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> because this is the first run-time method where the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> property becomes available.</span></span>  
  
 <span data-ttu-id="b10cc-175">下列程式碼範例示範在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期間，於其輸入與輸出資料行集合中找到資料行索引的元件。</span><span class="sxs-lookup"><span data-stu-id="b10cc-175">The following code example shows a component that locates indexes of the columns in its input and output column collection during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>.</span></span> <span data-ttu-id="b10cc-176">資料行索引是儲存在整數陣列中，而且在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 期間可以讓元件存取。</span><span class="sxs-lookup"><span data-stu-id="b10cc-176">The column indexes are stored in an integer array, and can be accessed by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>.</span></span>  
  
```csharp  
int []inputColumns;  
int []outputColumns;  
  
public override void PreExecute()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];  
  
    inputColumns = new int[input.InputColumnCollection.Count];  
    outputColumns = new int[output.OutputColumnCollection.Count];  
  
    for(int col=0; col < input.InputColumnCollection.Count; col++)  
    {  
        IDTSInputColumn100 inputColumn = input.InputColumnCollection[col];  
        inputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID);  
    }  
  
    for(int col=0; col < output.OutputColumnCollection.Count; col++)  
    {  
        IDTSOutputColumn100 outputColumn = output.OutputColumnCollection[col];  
        outputColumns[col] = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID);  
    }  
  
}  
```  
  
```vb  
Public Overrides Sub PreExecute()  
  
    Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)  
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)  
  
    ReDim inputColumns(input.InputColumnCollection.Count)  
    ReDim outputColumns(output.OutputColumnCollection.Count)  
  
    For col As Integer = 0 To input.InputColumnCollection.Count  
  
        Dim inputColumn As IDTSInputColumn100 = input.InputColumnCollection(col)  
        inputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, inputColumn.LineageID)  
    Next  
  
    For col As Integer = 0 To output.OutputColumnCollection.Count  
  
        Dim outputColumn As IDTSOutputColumn100 = output.OutputColumnCollection(col)  
        outputColumns(col) = BufferManager.FindColumnByLineageID(input.Buffer, outputColumn.LineageID)  
    Next  
  
End Sub  
```  
  
### <a name="processing-rows"></a><span data-ttu-id="b10cc-177">處理資料列</span><span class="sxs-lookup"><span data-stu-id="b10cc-177">Processing Rows</span></span>  
 <span data-ttu-id="b10cc-178">元件會接收 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 方法中包含資料列與資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 物件。</span><span class="sxs-lookup"><span data-stu-id="b10cc-178">Components receive <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> objects that contain rows and columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method.</span></span> <span data-ttu-id="b10cc-179">在這個方法期間會反覆運算緩衝區中的資料列，而且會在讀取和修改 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 期間識別資料行。</span><span class="sxs-lookup"><span data-stu-id="b10cc-179">During this method the rows in the buffer are iterated, and the columns identified during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> are read and modified.</span></span> <span data-ttu-id="b10cc-180">資料流程工作會重複呼叫該方法，直到不再從上游元件提供其他資料列為止。</span><span class="sxs-lookup"><span data-stu-id="b10cc-180">The method is called repeatedly by the data flow task until no more rows are provided from the upstream component.</span></span>  
  
 <span data-ttu-id="b10cc-181">透過使用陣列索引子存取方法，或是透過使用其中一個 `Get` 或 `Set` 方法，會讀取或寫入緩衝區中的個別資料行。</span><span class="sxs-lookup"><span data-stu-id="b10cc-181">An individual column in the buffer is read or written by using the array indexer access method, or by using one of the `Get` or `Set` methods.</span></span> <span data-ttu-id="b10cc-182">在已知緩衝區內資料行的資料類型時，應該使用較有效率的 `Get` 和 `Set` 方法。</span><span class="sxs-lookup"><span data-stu-id="b10cc-182">The `Get` and `Set` methods are more efficient and should be used when the data type of the column in the buffer is known.</span></span>  
  
 <span data-ttu-id="b10cc-183">下列程式碼範例顯示處理內送資料列的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> 方法之實作。</span><span class="sxs-lookup"><span data-stu-id="b10cc-183">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> method that processes incoming rows.</span></span>  
  
```csharp  
public override void ProcessInput( int InputID, PipelineBuffer buffer)  
{  
       while( buffer.NextRow())  
       {  
            for(int x=0; x < inputColumns.Length;x++)  
            {  
                if(!buffer.IsNull(inputColumns[x]))  
                {  
                    object columnData = buffer[inputColumns[x]];  
                    // TODO: Modify the column data.  
                    buffer[inputColumns[x]] = columnData;  
                }  
            }  
  
      }  
}  
```  
  
```vb  
Public Overrides Sub ProcessInput(ByVal InputID As Integer, ByVal buffer As PipelineBuffer)  
  
        While (buffer.NextRow())  
  
            For x As Integer = 0 To inputColumns.Length  
  
                if buffer.IsNull(inputColumns(x)) = false then  
  
                    Dim columnData As Object = buffer(inputColumns(x))  
                    ' TODO: Modify the column data.  
                    buffer(inputColumns(x)) = columnData  
  
                End If  
            Next  
  
        End While  
End Sub  
```  
  
## <a name="sample"></a><span data-ttu-id="b10cc-184">範例</span><span class="sxs-lookup"><span data-stu-id="b10cc-184">Sample</span></span>  
 <span data-ttu-id="b10cc-185">下列範例顯示具有同步輸出的簡單轉換元件，可將所有字串資料行值轉換為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="b10cc-185">The following sample shows a simple transformation component with synchronous outputs that converts the values of all string columns to uppercase.</span></span> <span data-ttu-id="b10cc-186">這個範例並未示範本主題中討論的所有方法與功能。</span><span class="sxs-lookup"><span data-stu-id="b10cc-186">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="b10cc-187">它示範每個具有同步輸出的自訂轉換元件必須覆寫的重要方法，但是並不包含設計階段驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b10cc-187">It demonstrates the important methods that every custom transformation component with synchronous outputs must override, but does not contain code for design-time validation.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
namespace Uppercase  
{  
  [DtsPipelineComponent(DisplayName = "Uppercase")]  
  public class Uppercase : PipelineComponent  
  {  
    ArrayList m_ColumnIndexList = new ArrayList();  
  
    public override void ProvideComponentProperties()  
    {  
      base.ProvideComponentProperties();  
      ComponentMetaData.InputCollection[0].Name = "Uppercase Input";  
      ComponentMetaData.OutputCollection[0].Name = "Uppercase Output";  
    }  
  
    public override void PreExecute()  
    {  
      IDTSInput100 input = ComponentMetaData.InputCollection[0];  
      IDTSInputColumnCollection100 inputColumns = input.InputColumnCollection;  
  
      foreach (IDTSInputColumn100 column in inputColumns)  
      {  
        if (column.DataType == DataType.DT_STR || column.DataType == DataType.DT_WSTR)  
        {  
          m_ColumnIndexList.Add((int)BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID));  
        }  
      }  
    }  
  
    public override void ProcessInput(int inputID, PipelineBuffer buffer)  
    {  
      while (buffer.NextRow())  
      {  
        foreach (int columnIndex in m_ColumnIndexList)  
        {  
          string str = buffer.GetString(columnIndex);  
          buffer.SetString(columnIndex, str.ToUpper());  
        }  
      }  
    }  
  }  
}  
```  
  
```vb  
Imports System   
Imports System.Collections   
Imports Microsoft.SqlServer.Dts.Pipeline   
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper   
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper   
Namespace Uppercase   
  
 <DtsPipelineComponent(DisplayName="Uppercase")> _   
 Public Class Uppercase   
 Inherits PipelineComponent   
   Private m_ColumnIndexList As ArrayList = New ArrayList   
  
   Public  Overrides Sub ProvideComponentProperties()   
     MyBase.ProvideComponentProperties   
     ComponentMetaData.InputCollection(0).Name = "Uppercase Input"   
     ComponentMetaData.OutputCollection(0).Name = "Uppercase Output"   
   End Sub   
  
   Public  Overrides Sub PreExecute()   
     Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
     Dim inputColumns As IDTSInputColumnCollection100 = input.InputColumnCollection   
     For Each column As IDTSInputColumn100 In inputColumns   
       If column.DataType = DataType.DT_STR OrElse column.DataType = DataType.DT_WSTR Then   
         m_ColumnIndexList.Add(CType(BufferManager.FindColumnByLineageID(input.Buffer, column.LineageID), Integer))   
       End If   
     Next   
   End Sub   
  
   Public  Overrides Sub ProcessInput(ByVal inputID As Integer, ByVal buffer As PipelineBuffer)   
     While buffer.NextRow   
       For Each columnIndex As Integer In m_ColumnIndexList   
         Dim str As String = buffer.GetString(columnIndex)   
         buffer.SetString(columnIndex, str.ToUpper)   
       Next   
     End While   
   End Sub   
 End Class   
End Namespace  
```  
  
<span data-ttu-id="b10cc-188">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="b10cc-188">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b10cc-189">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="b10cc-189">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b10cc-190">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="b10cc-190">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b10cc-191">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="b10cc-191">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10cc-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b10cc-192">See Also</span></span>  
 <span data-ttu-id="b10cc-193">[開發具有非同步輸出的自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span><span class="sxs-lookup"><span data-stu-id="b10cc-193">[Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md) </span></span>  
 <span data-ttu-id="b10cc-194">[瞭解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="b10cc-194">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) </span></span>  
 [<span data-ttu-id="b10cc-195">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="b10cc-195">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
