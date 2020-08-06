---
title: 開發自訂來源元件 | Microsoft Docs
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
- validation [Integration Services], components
- external data sources [Integration Services]
- data flow components [Integration Services], source components
- output columns [Integration Services]
- custom data flow components [Integration Services], source components
- custom sources [Integration Services]
- source components [Integration Services]
ms.assetid: 4dc0f631-8fd6-4007-b573-ca67f58ca068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6679b28463a09efe069235a5aef9dca54a381d62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705322"
---
# <a name="developing-a-custom-source-component"></a><span data-ttu-id="5091b-102">開發自訂來源元件</span><span class="sxs-lookup"><span data-stu-id="5091b-102">Developing a Custom Source Component</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5091b-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 可讓開發人員撰寫來源元件，以便連線到自訂資料來源，並將這些來源的資料提供給資料流程工作中的其他元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] gives developers the ability to write source components that can connect to custom data sources and supply data from those sources to other components in a data flow task.</span></span> <span data-ttu-id="5091b-104">當您必須連接至無法使用其中一個現有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源存取的資料來源時，能夠建立自訂來源的能力是很重要的。</span><span class="sxs-lookup"><span data-stu-id="5091b-104">The ability to create custom sources is valuable when you must connect to data sources that cannot be accessed by using one of the existing [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sources.</span></span>

 <span data-ttu-id="5091b-105">來源元件具有一或多個輸出與零輸入。</span><span class="sxs-lookup"><span data-stu-id="5091b-105">Source components have one or more outputs and zero inputs.</span></span> <span data-ttu-id="5091b-106">在設計階段，來源元件是用以建立和設定連接、從外部資料來源讀取資料行中繼資料，以及設定以外部資料來源為基礎之來源的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-106">At design time, source components are used to create and configure connections, read column metadata from the external data source, and configure the source's output columns based on the external data source.</span></span> <span data-ttu-id="5091b-107">在執行期間，它們會連接至外部資料來源並將資料列加入輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5091b-107">During execution they connect to the external data source and add rows to an output buffer.</span></span> <span data-ttu-id="5091b-108">資料流程工作會將這個緩衝區的資料列提供給下游元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-108">The data flow task then provides this buffer of data rows to downstream components.</span></span>

 <span data-ttu-id="5091b-109">如需資料流程元件開發的一般概觀，請參閱[開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="5091b-109">For a general overview of data flow component development, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>

## <a name="design-time"></a><span data-ttu-id="5091b-110">設計階段</span><span class="sxs-lookup"><span data-stu-id="5091b-110">Design Time</span></span>
 <span data-ttu-id="5091b-111">實作來源元件的設計階段功能需要指定連至外部資料來源的連接、加入和設定反映資料來源的輸出資料行，以及驗證元件是否已就緒可執行。</span><span class="sxs-lookup"><span data-stu-id="5091b-111">Implementing the design-time functionality of a source component involves specifying a connection to an external data source, adding and configuring output columns that reflect the data source, and validating that the component is ready to execute.</span></span> <span data-ttu-id="5091b-112">依定義，來源元件具有零個輸入以及一或多個非同步輸出。</span><span class="sxs-lookup"><span data-stu-id="5091b-112">By definition, a source component has zero inputs and one or more asynchronous outputs.</span></span>

### <a name="creating-the-component"></a><span data-ttu-id="5091b-113">建立元件</span><span class="sxs-lookup"><span data-stu-id="5091b-113">Creating the Component</span></span>
 <span data-ttu-id="5091b-114">來源元件使用在封裝中定義的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件，連接至外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="5091b-114">Source components connect to external data sources by using <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects defined in a package.</span></span> <span data-ttu-id="5091b-115">它們將元素加入 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 屬性的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 集合，以指出其連接管理員需求。</span><span class="sxs-lookup"><span data-stu-id="5091b-115">They indicate their requirement for a connection manager by adding an element to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property.</span></span> <span data-ttu-id="5091b-116">這個集合有兩個目的：用以儲存元件所使用的封裝中的連接管理員參考，以及用以向設計工具通告連接管理員的需求。</span><span class="sxs-lookup"><span data-stu-id="5091b-116">This collection serves two purposes-to hold references to connection managers in the package used by the component, and to advertise the need for a connection manager to the designer.</span></span> <span data-ttu-id="5091b-117">將 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> 新增至集合時，[進階編輯器]  會顯示 [連線屬性]  索引標籤，這可讓使用者在套件中選取或是建立連線。</span><span class="sxs-lookup"><span data-stu-id="5091b-117">When an <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> has been added to the collection, the **Advanced Editor** displays the **Connection Properties** tab, which lets users select or create a connection in the package.</span></span>

 <span data-ttu-id="5091b-118">下列程式碼範例顯示 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 的實作，它加入輸出並將 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> 物件加入 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>。</span><span class="sxs-lookup"><span data-stu-id="5091b-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> that adds an output, and adds a <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100> object to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span>

```csharp
using System;
using System.Collections;
using System.Data;
using System.Data.SqlClient;
using System.Data.OleDb;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    [DtsPipelineComponent(DisplayName = "MySourceComponent",ComponentType = ComponentType.SourceAdapter)]
    public class MyComponent : PipelineComponent
    {
        public override void ProvideComponentProperties()
        {
            // Reset the component.
            base.RemoveAllInputsOutputsAndCustomProperties();
            ComponentMetaData.RuntimeConnectionCollection.RemoveAll();

            IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
            output.Name = "Output";

            IDTSRuntimeConnection100 connection = ComponentMetaData.RuntimeConnectionCollection.New();
            connection.Name = "ADO.NET";
        }
```

```vb
Imports System.Data
Imports System.Data.SqlClient
Imports Microsoft.SqlServer.Dts.Runtime
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper
Imports Microsoft.SqlServer.Dts.Pipeline
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper

<DtsPipelineComponent(DisplayName:="MySourceComponent", ComponentType:=ComponentType.SourceAdapter)> _
Public Class MySourceComponent
    Inherits PipelineComponent

    Public Overrides Sub ProvideComponentProperties()

        ' Allow for resetting the component.
        RemoveAllInputsOutputsAndCustomProperties()
        ComponentMetaData.RuntimeConnectionCollection.RemoveAll()

        Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New()
        output.Name = "Output"

        Dim connection As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection.New()
        connection.Name = "ADO.NET"

    End Sub
End Class
```

### <a name="connecting-to-an-external-data-source"></a><span data-ttu-id="5091b-119">連接到外部資料來源</span><span class="sxs-lookup"><span data-stu-id="5091b-119">Connecting to an External Data Source</span></span>
 <span data-ttu-id="5091b-120">在將連接加入 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 之後，就可覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 方法以建立連至外部資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="5091b-120">After a connection has been added to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>, you override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method to establish a connection to the external data source.</span></span> <span data-ttu-id="5091b-121">會在設計與執行階段呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="5091b-121">This method is called during both design and execution time.</span></span> <span data-ttu-id="5091b-122">元件應該建立一個連接，以連至執行階段連接所指定的連接管理員，之後再建立連至外部資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="5091b-122">The component should establish a connection to the connection manager specified by the run-time connection, and subsequently, to the external data source.</span></span>

 <span data-ttu-id="5091b-123">在建立連接之後，元件應該會在內部快取它，並在呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 方法時釋放。</span><span class="sxs-lookup"><span data-stu-id="5091b-123">After the connection is established, it should be cached internally by the component and released when the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called.</span></span> <span data-ttu-id="5091b-124">會在設計階段與執行階段呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 方法，就像呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 方法一樣。</span><span class="sxs-lookup"><span data-stu-id="5091b-124">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method is called at design and execution time, like the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method.</span></span> <span data-ttu-id="5091b-125">開發人員會覆寫這個方法，並在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 期間釋放元件建立的連接。</span><span class="sxs-lookup"><span data-stu-id="5091b-125">Developers override this method, and release the connection established by the component during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span>

 <span data-ttu-id="5091b-126">下列程式碼範例顯示連接到 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 方法中的 ADO.NET 連接，並關閉 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> 方法中的連接。</span><span class="sxs-lookup"><span data-stu-id="5091b-126">The following code example shows a component that connects to an ADO.NET connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> method and closes the connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReleaseConnections%2A> method.</span></span>

```csharp
private SqlConnection sqlConnection;

public override void AcquireConnections(object transaction)
{
    if (ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager != null)
    {
        ConnectionManager cm = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection[0].ConnectionManager);
        ConnectionManagerAdoNet cmado = cm.InnerObject as ConnectionManagerAdoNet;

        if (cmado == null)
            throw new Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.");

        sqlConnection = cmado.AcquireConnection(transaction) as SqlConnection;
        sqlConnection.Open();
    }
}

public override void ReleaseConnections()
{
    if (sqlConnection != null && sqlConnection.State != ConnectionState.Closed)
        sqlConnection.Close();
}
```

```vb
Private sqlConnection As SqlConnection

Public Overrides Sub AcquireConnections(ByVal transaction As Object)

    If Not IsNothing(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager) Then

        Dim cm As ConnectionManager = Microsoft.SqlServer.Dts.Runtime.DtsConvert.GetWrapper(ComponentMetaData.RuntimeConnectionCollection(0).ConnectionManager)
        Dim cmado As ConnectionManagerAdoNet = CType(cm.InnerObject, ConnectionManagerAdoNet)

        If IsNothing(cmado) Then
            Throw New Exception("The ConnectionManager " + cm.Name + " is not an ADO.NET connection.")
        End If

        sqlConnection = CType(cmado.AcquireConnection(transaction), SqlConnection)
        sqlConnection.Open()

    End If
End Sub

Public Overrides Sub ReleaseConnections()

    If Not IsNothing(sqlConnection) And sqlConnection.State <> ConnectionState.Closed Then
        sqlConnection.Close()
    End If

End Sub
```

### <a name="creating-and-configuring-output-columns"></a><span data-ttu-id="5091b-127">建立和設定輸出資料行</span><span class="sxs-lookup"><span data-stu-id="5091b-127">Creating and Configuring Output Columns</span></span>
 <span data-ttu-id="5091b-128">來源元件的輸出資料行會反映元件在執行期間，加入資料流程的外部資料來源之資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-128">The output columns of a source component reflect the columns from the external data source that the component adds to the data flow during execution.</span></span> <span data-ttu-id="5091b-129">在設計階段，您在設定元件以連接至外部資料來源之後，加入輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-129">At design time, you add output columns after the component has been configured to connect to an external data source.</span></span> <span data-ttu-id="5091b-130">元件將資料行加入其輸出集合的設計階段方法，有可能因元件的需求而有所不同，雖然在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 或 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A> 期間不應該加入它們。</span><span class="sxs-lookup"><span data-stu-id="5091b-130">The design-time method that a component uses to add the columns to its output collection can vary based on the needs of the component, although they should not be added during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> or <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.AcquireConnections%2A>.</span></span> <span data-ttu-id="5091b-131">例如，在控制元件資料集之自訂屬性中包含 SQL 陳述式的元件，可能會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> 方法期間加入其輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-131">For example, a component that contains a SQL statement in a custom property that controls the data set for the component may add its output columns during the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.SetComponentProperty%2A> method.</span></span> <span data-ttu-id="5091b-132">元件會檢查它是否有快取的連接，而且如果有話，就會連接到資料來源並產生其輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-132">The component checks to see whether it has a cached connection, and, if it does, connects to the data source and generates its output columns.</span></span>

 <span data-ttu-id="5091b-133">在建立輸出資料行之後，請呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> 方法設定其資料類型屬性。</span><span class="sxs-lookup"><span data-stu-id="5091b-133">After an output column has been created, set its data type properties by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.SetDataTypeProperties%2A> method.</span></span> <span data-ttu-id="5091b-134">這個方法是必要的，因為 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> 屬性是唯讀的，而且每個屬性都與另一個屬性的設定相依。</span><span class="sxs-lookup"><span data-stu-id="5091b-134">This method is necessary because the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Length%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.Precision%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.CodePage%2A> properties are read-only and each property is dependent on the settings of the other.</span></span> <span data-ttu-id="5091b-135">這個方法會強制以一致的方式設定這些值的需求，而且資料流程工作會驗證它們是否已正確設定。</span><span class="sxs-lookup"><span data-stu-id="5091b-135">This method enforces the need for these values to be set consistently, and the data flow task validates that they are set correctly.</span></span>

 <span data-ttu-id="5091b-136">資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 會決定為其他屬性設定的值。</span><span class="sxs-lookup"><span data-stu-id="5091b-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> of the column determines the values that are set for the other properties.</span></span> <span data-ttu-id="5091b-137">下表顯示每個 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A> 的相依屬性之需求。</span><span class="sxs-lookup"><span data-stu-id="5091b-137">The following table shows the requirements on the dependent properties for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.DataType%2A>.</span></span> <span data-ttu-id="5091b-138">未列出的資料類型會將其相依屬性設定為零。</span><span class="sxs-lookup"><span data-stu-id="5091b-138">The data types not listed have their dependent properties set to zero.</span></span>

|<span data-ttu-id="5091b-139">DataType</span><span class="sxs-lookup"><span data-stu-id="5091b-139">DataType</span></span>|<span data-ttu-id="5091b-140">長度</span><span class="sxs-lookup"><span data-stu-id="5091b-140">Length</span></span>|<span data-ttu-id="5091b-141">調整</span><span class="sxs-lookup"><span data-stu-id="5091b-141">Scale</span></span>|<span data-ttu-id="5091b-142">Precision</span><span class="sxs-lookup"><span data-stu-id="5091b-142">Precision</span></span>|<span data-ttu-id="5091b-143">CodePage</span><span class="sxs-lookup"><span data-stu-id="5091b-143">CodePage</span></span>|
|--------------|------------|-----------|---------------|--------------|
|<span data-ttu-id="5091b-144">DT_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="5091b-144">DT_DECIMAL</span></span>|<span data-ttu-id="5091b-145">0</span><span class="sxs-lookup"><span data-stu-id="5091b-145">0</span></span>|<span data-ttu-id="5091b-146">大於 0，且小於或等於 28。</span><span class="sxs-lookup"><span data-stu-id="5091b-146">Greater than 0 and less than or equal to 28.</span></span>|<span data-ttu-id="5091b-147">0</span><span class="sxs-lookup"><span data-stu-id="5091b-147">0</span></span>|<span data-ttu-id="5091b-148">0</span><span class="sxs-lookup"><span data-stu-id="5091b-148">0</span></span>|
|<span data-ttu-id="5091b-149">DT_CY</span><span class="sxs-lookup"><span data-stu-id="5091b-149">DT_CY</span></span>|<span data-ttu-id="5091b-150">0</span><span class="sxs-lookup"><span data-stu-id="5091b-150">0</span></span>|<span data-ttu-id="5091b-151">0</span><span class="sxs-lookup"><span data-stu-id="5091b-151">0</span></span>|<span data-ttu-id="5091b-152">0</span><span class="sxs-lookup"><span data-stu-id="5091b-152">0</span></span>|<span data-ttu-id="5091b-153">0</span><span class="sxs-lookup"><span data-stu-id="5091b-153">0</span></span>|
|<span data-ttu-id="5091b-154">DT_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="5091b-154">DT_NUMERIC</span></span>|<span data-ttu-id="5091b-155">0</span><span class="sxs-lookup"><span data-stu-id="5091b-155">0</span></span>|<span data-ttu-id="5091b-156">大於 0、小於或等於 28，且小於有效位數 (Precision)。</span><span class="sxs-lookup"><span data-stu-id="5091b-156">Greater than 0 and less than or equal to 28, and less than Precision.</span></span>|<span data-ttu-id="5091b-157">大於或等於 1，且小於或等於 38。</span><span class="sxs-lookup"><span data-stu-id="5091b-157">Greater than or equal to 1 and less than or equal to 38.</span></span>|<span data-ttu-id="5091b-158">0</span><span class="sxs-lookup"><span data-stu-id="5091b-158">0</span></span>|
|<span data-ttu-id="5091b-159">DT_BYTES</span><span class="sxs-lookup"><span data-stu-id="5091b-159">DT_BYTES</span></span>|<span data-ttu-id="5091b-160">大於 0。</span><span class="sxs-lookup"><span data-stu-id="5091b-160">Greater than 0.</span></span>|<span data-ttu-id="5091b-161">0</span><span class="sxs-lookup"><span data-stu-id="5091b-161">0</span></span>|<span data-ttu-id="5091b-162">0</span><span class="sxs-lookup"><span data-stu-id="5091b-162">0</span></span>|<span data-ttu-id="5091b-163">0</span><span class="sxs-lookup"><span data-stu-id="5091b-163">0</span></span>|
|<span data-ttu-id="5091b-164">DT_STR</span><span class="sxs-lookup"><span data-stu-id="5091b-164">DT_STR</span></span>|<span data-ttu-id="5091b-165">大於 0 且小於 8000。</span><span class="sxs-lookup"><span data-stu-id="5091b-165">Greater than 0 and less than 8000.</span></span>|<span data-ttu-id="5091b-166">0</span><span class="sxs-lookup"><span data-stu-id="5091b-166">0</span></span>|<span data-ttu-id="5091b-167">0</span><span class="sxs-lookup"><span data-stu-id="5091b-167">0</span></span>|<span data-ttu-id="5091b-168">非 0，並為有效的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="5091b-168">Not 0, and a valid code page.</span></span>|
|<span data-ttu-id="5091b-169">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="5091b-169">DT_WSTR</span></span>|<span data-ttu-id="5091b-170">大於 0，且小於 4000。</span><span class="sxs-lookup"><span data-stu-id="5091b-170">Greater than 0 and less than 4000.</span></span>|<span data-ttu-id="5091b-171">0</span><span class="sxs-lookup"><span data-stu-id="5091b-171">0</span></span>|<span data-ttu-id="5091b-172">0</span><span class="sxs-lookup"><span data-stu-id="5091b-172">0</span></span>|<span data-ttu-id="5091b-173">0</span><span class="sxs-lookup"><span data-stu-id="5091b-173">0</span></span>|

 <span data-ttu-id="5091b-174">由於資料類型屬性的限制會以輸出資料行的資料類型為準，因此在使用 Managed 類型時，必須選擇正確的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5091b-174">Because the restrictions on the data type properties are based on the data type of the output column, you must choose the correct [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type when you work with managed types.</span></span> <span data-ttu-id="5091b-175">基底類別提供三種 Helper 方法：<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>，以協助受控元件開發人員在提供受控類型時，選取 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="5091b-175">The base class provides three helper methods, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ConvertBufferDataTypeToFitManaged%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferTypeToDataRecordType%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.DataRecordTypeToBufferType%2A>, to assist managed component developers in selecting an [!INCLUDE[ssIS](../../includes/ssis-md.md)] data type given a managed type.</span></span> <span data-ttu-id="5091b-176">這些方法會將 Managed 資料類型轉換為 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 資料類型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="5091b-176">These methods convert managed data types to [!INCLUDE[ssIS](../../includes/ssis-md.md)] data types, and vice versa.</span></span>

 <span data-ttu-id="5091b-177">下列程式碼範例顯示元件的輸出資料行集合如何根據表格的結構描述擴展。</span><span class="sxs-lookup"><span data-stu-id="5091b-177">The following code example shows how the output column collection of a component is populated based on the schema of a table.</span></span> <span data-ttu-id="5091b-178">基底類別的 Helper 方法是用以設定資料行的資料類型，而相依的屬性則會根據資料類型來設定。</span><span class="sxs-lookup"><span data-stu-id="5091b-178">The helper methods of the base class are used to set the data type of the column, and the dependent properties are set based on the data type.</span></span>

```csharp
SqlCommand sqlCommand;

private void CreateColumnsFromDataTable()
{
    // Get the output.
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    // Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll();
    output.ExternalMetadataColumnCollection.RemoveAll();

    this.sqlCommand = sqlConnection.CreateCommand();
    this.sqlCommand.CommandType = CommandType.Text;
    this.sqlCommand.CommandText = (string)ComponentMetaData.CustomPropertyCollection["SqlStatement"].Value;
    SqlDataReader schemaReader = this.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly);
    DataTable dataTable = schemaReader.GetSchemaTable();

    // Walk the columns in the schema, 
    // and for each data column create an output column and an external metadata column.
    foreach (DataRow row in dataTable.Rows)
    {
        IDTSOutputColumn100 outColumn = output.OutputColumnCollection.New();
        IDTSExternalMetadataColumn100 exColumn = output.ExternalMetadataColumnCollection.New();

        // Set column data type properties.
        bool isLong = false;
        DataType dt = DataRecordTypeToBufferType((Type)row["DataType"]);
        dt = ConvertBufferDataTypeToFitManaged(dt, ref isLong);
        int length = 0;
        int precision = (short)row["NumericPrecision"];
        int scale = (short)row["NumericScale"];
        int codepage = dataTable.Locale.TextInfo.ANSICodePage;

        switch (dt)
        {
            // The length cannot be zero, and the code page property must contain a valid code page.
            case DataType.DT_STR:
            case DataType.DT_TEXT:
                length = precision;
                precision = 0;
                scale = 0;
                break;

            case DataType.DT_WSTR:
                length = precision;
                codepage = 0;
                scale = 0;
                precision = 0;
                break;

            case DataType.DT_BYTES:
                precision = 0;
                scale = 0;
                codepage = 0;
                break;

            case DataType.DT_NUMERIC:
                length = 0;
                codepage = 0;

                if (precision > 38)
                    precision = 38;

                if (scale > 6)
                    scale = 6;
                break;

            case DataType.DT_DECIMAL:
                length = 0;
                precision = 0;
                codepage = 0;
                break;

            default:
                length = 0;
                precision = 0;
                codepage = 0;
                scale = 0;
                break;

        }

        // Set the properties of the output column.
        outColumn.Name = (string)row["ColumnName"];
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage);
    }
}
```

```vb
Private sqlCommand As SqlCommand

Private Sub CreateColumnsFromDataTable()

    ' Get the output.
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    ' Start clean, and remove the columns from both collections.
    output.OutputColumnCollection.RemoveAll()
    output.ExternalMetadataColumnCollection.RemoveAll()

    Me.sqlCommand = sqlConnection.CreateCommand()
    Me.sqlCommand.CommandType = CommandType.Text
    Me.sqlCommand.CommandText = CStr(ComponentMetaData.CustomPropertyCollection("SqlStatement").Value)

    Dim schemaReader As SqlDataReader = Me.sqlCommand.ExecuteReader(CommandBehavior.SchemaOnly)
    Dim dataTable As DataTable = schemaReader.GetSchemaTable()

    ' Walk the columns in the schema, 
    ' and for each data column create an output column and an external metadata column.
    For Each row As DataRow In dataTable.Rows

        Dim outColumn As IDTSOutputColumn100 = output.OutputColumnCollection.New()
        Dim exColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()

        ' Set column data type properties.
        Dim isLong As Boolean = False
        Dim dt As DataType = DataRecordTypeToBufferType(CType(row("DataType"), Type))
        dt = ConvertBufferDataTypeToFitManaged(dt, isLong)
        Dim length As Integer = 0
        Dim precision As Integer = CType(row("NumericPrecision"), Short)
        Dim scale As Integer = CType(row("NumericScale"), Short)
        Dim codepage As Integer = dataTable.Locale.TextInfo.ANSICodePage

        Select Case dt

            ' The length cannot be zero, and the code page property must contain a valid code page.
            Case DataType.DT_STR
            Case DataType.DT_TEXT
                length = precision
                precision = 0
                scale = 0

            Case DataType.DT_WSTR
                length = precision
                codepage = 0
                scale = 0
                precision = 0

            Case DataType.DT_BYTES
                precision = 0
                scale = 0
                codepage = 0

            Case DataType.DT_NUMERIC
                length = 0
                codepage = 0

                If precision > 38 Then
                    precision = 38
                End If

                If scale > 6 Then
                    scale = 6
                End If

            Case DataType.DT_DECIMAL
                length = 0
                precision = 0
                codepage = 0

            Case Else
                length = 0
                precision = 0
                codepage = 0
                scale = 0
        End Select

        ' Set the properties of the output column.
        outColumn.Name = CStr(row("ColumnName"))
        outColumn.SetDataTypeProperties(dt, length, precision, scale, codepage)
    Next
End Sub
```

### <a name="validating-the-component"></a><span data-ttu-id="5091b-179">驗證元件</span><span class="sxs-lookup"><span data-stu-id="5091b-179">Validating the Component</span></span>
 <span data-ttu-id="5091b-180">您應該驗證來源元件，並確認輸出資料行集合中所定義的資料行，符合在外部資料來源的資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-180">You should validate a source component and verify that the columns defined in its output column collections match the columns at the external data source.</span></span> <span data-ttu-id="5091b-181">有時，針對外部資料來源驗證輸出資料行是無法執行的，例如在中斷連接的狀態下，或是當最好避免長時間往返伺服器時。</span><span class="sxs-lookup"><span data-stu-id="5091b-181">Sometimes, verifying the output columns against the external data source can be impossible, such as in a disconnected state, or when it is preferable to avoid lengthy round trips to the server.</span></span> <span data-ttu-id="5091b-182">在這些情況下，在輸出中的資料行仍然可以使用輸出物件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> 來驗證。</span><span class="sxs-lookup"><span data-stu-id="5091b-182">In these situations, the columns in the output can still be validated by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.ExternalMetadataColumnCollection%2A> of the output object.</span></span> <span data-ttu-id="5091b-183">如需詳細資訊，請參閱[驗證資料流程元件](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="5091b-183">For more information, see [Validating a Data Flow Component](../extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md).</span></span>

 <span data-ttu-id="5091b-184">在輸入和輸出物件上都有這個集合，而且您可以使用外部資料來源的資料行來擴展它。</span><span class="sxs-lookup"><span data-stu-id="5091b-184">This collection exists on both input and output objects and you can populate it with the columns from the external data source.</span></span> <span data-ttu-id="5091b-185">當 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具離線時，或是當 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 屬性是 `false` 時，可以使用這個集合來驗證輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-185">You can use this collection to validate the output columns when [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer is offline, when the component is disconnected, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span> <span data-ttu-id="5091b-186">當建立輸出資料行時，應該同時先擴展集合。</span><span class="sxs-lookup"><span data-stu-id="5091b-186">The collection should be first populated at the same time that the output columns are created.</span></span> <span data-ttu-id="5091b-187">將外部中繼資料行加入集合是相當容易的，因為外部中繼資料行應該一開始便符合輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-187">Adding external metadata columns to the collection is relatively easy because the external metadata column should initially match the output column.</span></span> <span data-ttu-id="5091b-188">資料行的資料類型屬性應該已正確地設定，而且可以將屬性直接複製到 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> 物件。</span><span class="sxs-lookup"><span data-stu-id="5091b-188">The data type properties of the column should have already been set correctly, and the properties can be copied directly to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> object.</span></span>

 <span data-ttu-id="5091b-189">下列範例程式碼會加入以新建立的輸出資料行為基礎的外部中繼資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-189">The following sample code adds an external metadata column that is based on a newly created output column.</span></span> <span data-ttu-id="5091b-190">它會假設已建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-190">It assumes that the output column has already been created.</span></span>

```csharp
private void CreateExternalMetaDataColumn(IDTSOutput100 output, IDTSOutputColumn100 outputColumn)
{

    // Set the properties of the external metadata column.
    IDTSExternalMetadataColumn100 externalColumn = output.ExternalMetadataColumnCollection.New();
    externalColumn.Name = outputColumn.Name;
    externalColumn.Precision = outputColumn.Precision;
    externalColumn.Length = outputColumn.Length;
    externalColumn.DataType = outputColumn.DataType;
    externalColumn.Scale = outputColumn.Scale;

    // Map the external column to the output column.
    outputColumn.ExternalMetadataColumnID = externalColumn.ID;

}
```

```vb
Private Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumn As IDTSOutputColumn100)

        ' Set the properties of the external metadata column.
        Dim externalColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New()
        externalColumn.Name = outputColumn.Name
        externalColumn.Precision = outputColumn.Precision
        externalColumn.Length = outputColumn.Length
        externalColumn.DataType = outputColumn.DataType
        externalColumn.Scale = outputColumn.Scale

        ' Map the external column to the output column.
        outputColumn.ExternalMetadataColumnID = externalColumn.ID

    End Sub
```

## <a name="run-time"></a><span data-ttu-id="5091b-191">執行階段</span><span class="sxs-lookup"><span data-stu-id="5091b-191">Run Time</span></span>
 <span data-ttu-id="5091b-192">在執行期間，元件會將資料列加入資料流程工作所建立的輸出緩衝區，並提供給在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 中的元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-192">During execution, components add rows to output buffers that are created by the data flow task and provided to the component in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="5091b-193">只要為來源元件呼叫一次，此方法就會收到連接到下游元件的元件之每個 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 的輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5091b-193">Called once for source components, the method receives an output buffer for each <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the component that is connected to a downstream component.</span></span>

### <a name="locating-columns-in-the-buffer"></a><span data-ttu-id="5091b-194">找出緩衝區中的資料行</span><span class="sxs-lookup"><span data-stu-id="5091b-194">Locating Columns in the Buffer</span></span>
 <span data-ttu-id="5091b-195">元件的輸出緩衝區包含元件所定義的資料行，以及任何加入下游元件輸出的資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-195">The output buffer for a component contains the columns defined by the component and any columns added to the output of a downstream component.</span></span> <span data-ttu-id="5091b-196">例如，如果來源元件在其輸出中提供三個資料行，而下一個元件加入第四個輸出資料行，則提供給來源元件使用的輸出緩衝區包含這四個資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-196">For example, if a source component provides three columns in its output, and the next component adds a fourth output column, the output buffer provided for use by the source component contains these four columns.</span></span>

 <span data-ttu-id="5091b-197">在緩衝區資料列中的資料行順序，不是由輸出資料行集合中的輸出資料行索引所定義。</span><span class="sxs-lookup"><span data-stu-id="5091b-197">The order of the columns in a buffer row is not defined by the index of the output column in the output column collection.</span></span> <span data-ttu-id="5091b-198">輸出資料行只有透過使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A> 方法，才能正確地位於緩衝區資料列中。</span><span class="sxs-lookup"><span data-stu-id="5091b-198">An output column can only be accurately located in a buffer row by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSBufferManagerClass.FindColumnByLineageID%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.BufferManager%2A>.</span></span> <span data-ttu-id="5091b-199">這個方法會在指定的緩衝區中找到具有指定歷程識別碼的資料行，並傳回它在資料列中的位置。</span><span class="sxs-lookup"><span data-stu-id="5091b-199">This method locates the column with the specified lineage ID in the specified buffer, and returns its location in the row.</span></span> <span data-ttu-id="5091b-200">輸出資料行的索引通常位於 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 方法中，並且會在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 期間儲存以供使用。</span><span class="sxs-lookup"><span data-stu-id="5091b-200">The indexes of the output columns are typically located in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> method, and stored for use during <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span>

 <span data-ttu-id="5091b-201">下列程式碼範例會在呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 的期間，在輸出緩衝區中尋找輸出資料行的位置，並將它們儲存在內部結構中。</span><span class="sxs-lookup"><span data-stu-id="5091b-201">The following code example finds the location of the output columns in the output buffer during a call to <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A>, and stores them in an internal structure.</span></span> <span data-ttu-id="5091b-202">資料行的名稱也會儲存在結構中，而且會用於本主題下一節的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 方法之程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="5091b-202">The name of the column is also stored in the structure and is used in the code example for the  <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> method in the next section of this topic.</span></span>

```csharp
ArrayList columnInformation;

private struct ColumnInfo
{
    public int BufferColumnIndex;
    public string ColumnName;
}

public override void PreExecute()
{
    this.columnInformation = new ArrayList();
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

    foreach (IDTSOutputColumn100 col in output.OutputColumnCollection)
    {
        ColumnInfo ci = new ColumnInfo();
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID);
        ci.ColumnName = col.Name;
        columnInformation.Add(ci);
    }
}
```

```vb
Public Overrides Sub PreExecute()

    Me.columnInformation = New ArrayList()
    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)

    For Each col As IDTSOutputColumn100 In output.OutputColumnCollection

        Dim ci As ColumnInfo = New ColumnInfo()
        ci.BufferColumnIndex = BufferManager.FindColumnByLineageID(output.Buffer, col.LineageID)
        ci.ColumnName = col.Name
        columnInformation.Add(ci)
    Next
End Sub
```

### <a name="processing-rows"></a><span data-ttu-id="5091b-203">處理資料列</span><span class="sxs-lookup"><span data-stu-id="5091b-203">Processing Rows</span></span>
 <span data-ttu-id="5091b-204">透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> 方法，將資料列加入輸出緩衝區，這將會建立資料行中為空值的新緩衝區資料列。</span><span class="sxs-lookup"><span data-stu-id="5091b-204">Rows are added to the output buffer by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.AddRow%2A> method, which creates a new buffer row with empty values in its columns.</span></span> <span data-ttu-id="5091b-205">元件就會將值指派給個別資料行。</span><span class="sxs-lookup"><span data-stu-id="5091b-205">The component then assigns values to the individual columns.</span></span> <span data-ttu-id="5091b-206">資料流程工作會建立和監視提供給元件的輸出緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5091b-206">The output buffers provided to a component are created and monitored by the data flow task.</span></span> <span data-ttu-id="5091b-207">當它們變滿時，會將緩衝區中的資料列移到下一個元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-207">As they become full, the rows in the buffer are moved to the next component.</span></span> <span data-ttu-id="5091b-208">並沒有任何方法可以判斷何時會將資料列批次傳送到下一個元件，因為由資料流程工作來移動資料列，對元件開發人員而言是透明的，而且 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> 屬性在輸出緩衝區中永遠都是零。</span><span class="sxs-lookup"><span data-stu-id="5091b-208">There is no way to determine when a batch of rows has been sent to the next component because the movement of rows by the data flow task is transparent to the component developer, and the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.RowCount%2A> property is always zero on output buffers.</span></span> <span data-ttu-id="5091b-209">當來源元件完成將資料列加入其輸出緩衝區時，它會透過呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> 方法，來通知資料流程工作，而且在緩衝區中的其餘資料列會傳遞到下一個元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-209">When a source component is finished adding rows to its output buffer, it notifies the data flow task by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.SetEndOfRowset%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer>, and the remaining rows in the buffer are passed to the next component.</span></span>

 <span data-ttu-id="5091b-210">當來源元件從外部資料來源讀取資料列時，您可能會想要呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> 方法，以更新 "Rows read" 或是 "BLOB bytes read" 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="5091b-210">While the source component reads rows from the external data source, you may want to update the "Rows read" or "BLOB bytes read" performance counters by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.IncrementPipelinePerfCounter%2A> method.</span></span> <span data-ttu-id="5091b-211">如需相關資訊，請參閱 [Performance Counters](../performance/performance-counters.md)。</span><span class="sxs-lookup"><span data-stu-id="5091b-211">For more information, see [Performance Counters](../performance/performance-counters.md).</span></span>

 <span data-ttu-id="5091b-212">下列程式碼範例顯示將資料列加入 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> 中的輸出緩衝區的元件。</span><span class="sxs-lookup"><span data-stu-id="5091b-212">The following code example shows a component that adds rows to an output buffer in <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>.</span></span> <span data-ttu-id="5091b-213">在上述程式碼範例中使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> 來找到緩衝區中的輸出資料行索引。</span><span class="sxs-lookup"><span data-stu-id="5091b-213">The indexes of the output columns in the buffer were located using <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PreExecute%2A> in the previous code example.</span></span>

```csharp
public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
{
    IDTSOutput100 output = ComponentMetaData.OutputCollection[0];
    PipelineBuffer buffer = buffers[0];

    SqlDataReader dataReader = sqlCommand.ExecuteReader();

    // Loop over the rows in the DataReader, 
    // and add them to the output buffer.
    while (dataReader.Read())
    {
        // Add a row to the output buffer.
        buffer.AddRow();

        for (int x = 0; x < columnInformation.Count; x++)
        {
            ColumnInfo ci = (ColumnInfo)columnInformation[x];
            int ordinal = dataReader.GetOrdinal(ci.ColumnName);

            if (dataReader.IsDBNull(ordinal))
                buffer.SetNull(ci.BufferColumnIndex);
            else
            {
                buffer[ci.BufferColumnIndex] = dataReader[ci.ColumnName];
            }
        }
    }
    buffer.SetEndOfRowset();
}
```

```vb
Public Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer())

    Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0)
    Dim buffer As PipelineBuffer = buffers(0)

    Dim dataReader As SqlDataReader = sqlCommand.ExecuteReader()

    ' Loop over the rows in the DataReader, 
    ' and add them to the output buffer.
    While (dataReader.Read())

        ' Add a row to the output buffer.
        buffer.AddRow()

        For x As Integer = 0 To columnInformation.Count

            Dim ci As ColumnInfo = CType(columnInformation(x), ColumnInfo)

            Dim ordinal As Integer = dataReader.GetOrdinal(ci.ColumnName)

            If (dataReader.IsDBNull(ordinal)) Then
                buffer.SetNull(ci.BufferColumnIndex)
            Else
                buffer(ci.BufferColumnIndex) = dataReader(ci.ColumnName)

            End If
        Next

    End While

    buffer.SetEndOfRowset()
End Sub
```

## <a name="sample"></a><span data-ttu-id="5091b-214">範例</span><span class="sxs-lookup"><span data-stu-id="5091b-214">Sample</span></span>
 <span data-ttu-id="5091b-215">下列範例顯示範例來源元件，它使用檔案連接管理員來將檔案的二進位內容載入資料流程。</span><span class="sxs-lookup"><span data-stu-id="5091b-215">The following sample shows a simple source component that uses a File connection manager to load the binary contents of files into the data flow.</span></span> <span data-ttu-id="5091b-216">這個範例並未示範本主題中討論的所有方法與功能。</span><span class="sxs-lookup"><span data-stu-id="5091b-216">This sample does not demonstrate all the methods and functionality discussed in this topic.</span></span> <span data-ttu-id="5091b-217">它示範每個自訂來源元件必須覆寫的重要方法，但是並不包含設計階段驗證的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5091b-217">It demonstrates the important methods that every custom source component must override, but does not contain code for design-time validation.</span></span>

```csharp
using System;
using System.IO;
using Microsoft.SqlServer.Dts.Pipeline;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

namespace BlobSrc
{
  [DtsPipelineComponent(DisplayName = "BLOB Inserter Source", Description = "Inserts files into the data flow as BLOBs")]
  public class BlobSrc : PipelineComponent
  {
    IDTSConnectionManager100 m_ConnMgr;
    int m_FileNameColumnIndex = -1;
    int m_FileBlobColumnIndex = -1;

    public override void ProvideComponentProperties()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection.New();
      output.Name = "BLOB File Inserter Output";

      IDTSOutputColumn100 column = output.OutputColumnCollection.New();
      column.Name = "FileName";
      column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0);

      column = output.OutputColumnCollection.New();
      column.Name = "FileBLOB";
      column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0);

      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection.New();
      conn.Name = "FileConnection";
    }

    public override void AcquireConnections(object transaction)
    {
      IDTSRuntimeConnection100 conn = ComponentMetaData.RuntimeConnectionCollection[0];
      m_ConnMgr = conn.ConnectionManager;
    }

    public override void ReleaseConnections()
    {
      m_ConnMgr = null;
    }

    public override void PreExecute()
    {
      IDTSOutput100 output = ComponentMetaData.OutputCollection[0];

      m_FileNameColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[0].LineageID);
      m_FileBlobColumnIndex = (int)BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection[1].LineageID);
    }

    public override void PrimeOutput(int outputs, int[] outputIDs, PipelineBuffer[] buffers)
    {
      string strFileName = (string)m_ConnMgr.AcquireConnection(null);

      while (strFileName != null)
      {
        buffers[0].AddRow();

        buffers[0].SetString(m_FileNameColumnIndex, strFileName);

        FileInfo fileInfo = new FileInfo(strFileName);
        byte[] fileData = new byte[fileInfo.Length];
        FileStream fs = new FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read);
        fs.Read(fileData, 0, fileData.Length);

        buffers[0].AddBlobData(m_FileBlobColumnIndex, fileData);

        strFileName = (string)m_ConnMgr.AcquireConnection(null);
      }

      buffers[0].SetEndOfRowset();
    }
  }
}
```

```vb
Imports System 
Imports System.IO 
Imports Microsoft.SqlServer.Dts.Pipeline 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper 
Namespace BlobSrc 

 <DtsPipelineComponent(DisplayName="BLOB Inserter Source", Description="Inserts files into the data flow as BLOBs")> _ 
 Public Class BlobSrc 
 Inherits PipelineComponent 
   Private m_ConnMgr As IDTSConnectionManager100 
   Private m_FileNameColumnIndex As Integer = -1 
   Private m_FileBlobColumnIndex As Integer = -1 

   Public  Overrides Sub ProvideComponentProperties() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection.New 
     output.Name = "BLOB File Inserter Output" 
     Dim column As IDTSOutputColumn100 = output.OutputColumnCollection.New 
     column.Name = "FileName" 
     column.SetDataTypeProperties(DataType.DT_WSTR, 256, 0, 0, 0) 
     column = output.OutputColumnCollection.New 
     column.Name = "FileBLOB" 
     column.SetDataTypeProperties(DataType.DT_IMAGE, 0, 0, 0, 0) 
     Dim conn As IDTSRuntimeConnection90 = ComponentMetaData.RuntimeConnectionCollection.New 
     conn.Name = "FileConnection" 
   End Sub 

   Public  Overrides Sub AcquireConnections(ByVal transaction As Object) 
     Dim conn As IDTSRuntimeConnection100 = ComponentMetaData.RuntimeConnectionCollection(0) 
     m_ConnMgr = conn.ConnectionManager 
   End Sub 

   Public  Overrides Sub ReleaseConnections() 
     m_ConnMgr = Nothing 
   End Sub 

   Public  Overrides Sub PreExecute() 
     Dim output As IDTSOutput100 = ComponentMetaData.OutputCollection(0) 
     m_FileNameColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(0).LineageID), Integer) 
     m_FileBlobColumnIndex = CType(BufferManager.FindColumnByLineageID(output.Buffer, output.OutputColumnCollection(1).LineageID), Integer) 
   End Sub 

   Public  Overrides Sub PrimeOutput(ByVal outputs As Integer, ByVal outputIDs As Integer(), ByVal buffers As PipelineBuffer()) 
     Dim strFileName As String = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     While Not (strFileName Is Nothing) 
       buffers(0).AddRow 
       buffers(0).SetString(m_FileNameColumnIndex, strFileName) 
       Dim fileInfo As FileInfo = New FileInfo(strFileName) 
       Dim fileData(fileInfo.Length) As Byte 
       Dim fs As FileStream = New FileStream(strFileName, FileMode.Open, FileAccess.Read, FileShare.Read) 
       fs.Read(fileData, 0, fileData.Length) 
       buffers(0).AddBlobData(m_FileBlobColumnIndex, fileData) 
       strFileName = CType(m_ConnMgr.AcquireConnection(Nothing), String) 
     End While 
     buffers(0).SetEndOfRowset 
   End Sub 
 End Class 
End Namespace
```

<span data-ttu-id="5091b-218">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="5091b-218">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5091b-219">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="5091b-219">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5091b-220">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="5091b-220">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5091b-221">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="5091b-221">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5091b-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5091b-222">See Also</span></span>
 <span data-ttu-id="5091b-223">開發[使用腳本元件建立來源](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)的[自訂目的地元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span><span class="sxs-lookup"><span data-stu-id="5091b-223">[Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md) [Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)</span></span>


