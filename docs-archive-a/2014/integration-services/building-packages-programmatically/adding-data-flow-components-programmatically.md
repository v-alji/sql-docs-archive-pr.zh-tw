---
title: 以程式設計方式新增資料流程元件 | Microsoft Docs
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: c06065cf-43e5-4b6b-9824-7309d7f5e35e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 807e758e42b738c4b0bf64b1d6f48bc29649ae6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594653"
---
# <a name="adding-data-flow-components-programmatically"></a><span data-ttu-id="bd16b-102">以程式設計方式加入資料流程元件</span><span class="sxs-lookup"><span data-stu-id="bd16b-102">Adding Data Flow Components Programmatically</span></span>
  <span data-ttu-id="bd16b-103">當您建立資料流程時，可以從加入元件開始。</span><span class="sxs-lookup"><span data-stu-id="bd16b-103">When you build a data flow, you start by adding components.</span></span> <span data-ttu-id="bd16b-104">接著您會設定這些元件，然後將它們連接在一起以便在執行階段建立資料流程。</span><span class="sxs-lookup"><span data-stu-id="bd16b-104">Then you configure those components and connect them together to establish the flow of data at run time.</span></span> <span data-ttu-id="bd16b-105">本章節描述將元件加入資料流程工作，建立元件的設計階段執行個體，然後設定元件。</span><span class="sxs-lookup"><span data-stu-id="bd16b-105">This section describes adding a component to the data flow task, creating the design-time instance of the component, and then configuring the component.</span></span> <span data-ttu-id="bd16b-106">如需如何連線元件的資訊，請參閱[以程式設計方式連線資料流程元件](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="bd16b-106">For information about how to connect components, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-component"></a><span data-ttu-id="bd16b-107">加入元件</span><span class="sxs-lookup"><span data-stu-id="bd16b-107">Adding a Component</span></span>  
 <span data-ttu-id="bd16b-108">呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> 方法，以建立新元件並將它加入資料流程工作中。</span><span class="sxs-lookup"><span data-stu-id="bd16b-108">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A> collection to create a new component and add it to the data flow task.</span></span> <span data-ttu-id="bd16b-109">這個方法會傳回元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面。</span><span class="sxs-lookup"><span data-stu-id="bd16b-109">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component.</span></span> <span data-ttu-id="bd16b-110">不過，此時，<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 並不包含任何一個元件的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="bd16b-110">However, at this point, the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> does not contain information specific to any one component.</span></span> <span data-ttu-id="bd16b-111">設定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 屬性以識別元件的類型。</span><span class="sxs-lookup"><span data-stu-id="bd16b-111">Set the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property to identify the type of component.</span></span> <span data-ttu-id="bd16b-112">資料流程工作使用此屬性值在執行階段建立元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd16b-112">The data flow task uses the value of this property to create an instance of the component at run time.</span></span>  
  
 <span data-ttu-id="bd16b-113">在 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 屬性中指定的值，可以是 CLSID、PROGID 或是元件的 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="bd16b-113">The value specified in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property can be the CLSID, PROGID, or <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> property of the component.</span></span> <span data-ttu-id="bd16b-114">CLSID 通常會顯示在 [屬性] 視窗中，做為元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="bd16b-114">The CLSID is normally displayed in the Properties window as the value of the component's <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="bd16b-115">如需取得此屬性及可用元件其他屬性的資訊，請參閱[以程式設計方式探索資料流程元件](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="bd16b-115">For information about obtaining this property and other properties of available components, see [Discovering Data Flow Components Programmatically](../building-packages-programmatically/discovering-data-flow-components-programmatically.md).</span></span>  
  
## <a name="adding-a-managed-component"></a><span data-ttu-id="bd16b-116">加入 Managed 元件</span><span class="sxs-lookup"><span data-stu-id="bd16b-116">Adding a Managed Component</span></span>  
 <span data-ttu-id="bd16b-117">您無法使用 CLSID 或 PROGID 將 Managed 資料流程元件加入資料流程，因為這些值會指向包裝函數，而不是元件本身。</span><span class="sxs-lookup"><span data-stu-id="bd16b-117">You cannot use the CLSID or PROGID to add one the managed data flow components to the data flow, because these values point to a wrapper and not to the component itself.</span></span> <span data-ttu-id="bd16b-118">您可以改用 `CreationName` 屬性或是 `AssemblyQualifiedName` 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bd16b-118">Instead you can use the `CreationName` property or the `AssemblyQualifiedName` property as shown in the following sample.</span></span>  
  
 <span data-ttu-id="bd16b-119">如果您打算使用 `AssemblyQualifiedName` 屬性，則必須在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 專案中加入含有 Managed 元件之組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bd16b-119">If you intend to use the `AssemblyQualifiedName` property, then you must add a reference in your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] project to the assembly that contains the managed component.</span></span> <span data-ttu-id="bd16b-120">這些組件不會列在 [新增參考]  對話方塊的 [.NET] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="bd16b-120">These assemblies are not listed on the .NET tab of the **Add Reference** dialog box.</span></span> <span data-ttu-id="bd16b-121">通常必須在 **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** 資料夾中瀏覽以找出組件。</span><span class="sxs-lookup"><span data-stu-id="bd16b-121">Normally you must browse to locate the assembly in the **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents** folder.</span></span>  
  
 <span data-ttu-id="bd16b-122">內建的 Managed 資料流程元件包括：</span><span class="sxs-lookup"><span data-stu-id="bd16b-122">The built-in managed data flow components include:</span></span>  
  
-   [!INCLUDE[vstecado](../../includes/vstecado-md.md)] <span data-ttu-id="bd16b-123">來源</span><span class="sxs-lookup"><span data-stu-id="bd16b-123">Source</span></span>  
  
-   <span data-ttu-id="bd16b-124">XML 來源</span><span class="sxs-lookup"><span data-stu-id="bd16b-124">XML Source</span></span>  
  
-   <span data-ttu-id="bd16b-125">DataReader 目的地</span><span class="sxs-lookup"><span data-stu-id="bd16b-125">DataReader Destination</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="bd16b-126">Compact 目的地</span><span class="sxs-lookup"><span data-stu-id="bd16b-126">Compact Destination</span></span>  
  
-   <span data-ttu-id="bd16b-127">指令碼元件</span><span class="sxs-lookup"><span data-stu-id="bd16b-127">Script Component</span></span>  
  
 <span data-ttu-id="bd16b-128">下列程式碼範例顯示兩種將 Managed 元件加入資料流程的方法：</span><span class="sxs-lookup"><span data-stu-id="bd16b-128">The following code sample shows both ways of adding a managed component to the data flow:</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Microsoft.SqlServer.Dts.Runtime.Package package = new Microsoft.SqlServer.Dts.Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Microsoft.SqlServer.Dts.Runtime.TaskHost thMainPipe = (Microsoft.SqlServer.Dts.Runtime.TaskHost)e;  
      MainPipe dataFlowTask = (MainPipe)thMainPipe.InnerObject;  
  
      // The Application object will be used to obtain the CreationName  
      //  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
      Application app = new Application();  
  
      // Add a first ADO NET source to the data flow.  
      //  The CreationName property requires an Application instance.  
      IDTSComponentMetaData100 component1 = dataFlowTask.ComponentMetaDataCollection.New();  
      component1.Name = "DataReader Source";  
      component1.ComponentClassID = app.PipelineComponentInfos["DataReader Source"].CreationName;  
  
      // Add a second ADO NET source to the data flow.  
      //  The AssemblyQualifiedName property requires a reference to the assembly.  
      IDTSComponentMetaData100 component2 = dataFlowTask.ComponentMetaDataCollection.New();  
      component2.Name = "DataReader Source";  
      component2.ComponentClassID = typeof(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName;  
    }  
  }  
}  
  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' The Application object will be used to obtain the CreationName  
    '  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
    Dim app As New Application()  
  
    ' Add a first ADO NET source to the data flow.  
    '  The CreationName property requires an Application instance.  
    Dim component1 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component1.Name = "DataReader Source"  
    component1.ComponentClassID = app.PipelineComponentInfos("DataReader Source").CreationName  
  
    ' Add a second ADO NET source to the data flow.  
    '  The AssemblyQualifiedName property requires a reference to the assembly.  
    Dim component2 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component2.Name = "DataReader Source"  
    component2.ComponentClassID = _  
      GetType(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName  
  
  End Sub  
  
End Module  
```  
  
## <a name="creating-the-design-time-instance-of-the-component"></a><span data-ttu-id="bd16b-129">建立元件的設計階段執行個體</span><span class="sxs-lookup"><span data-stu-id="bd16b-129">Creating the Design-time Instance of the Component</span></span>  
 <span data-ttu-id="bd16b-130">呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> 方法以建立 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> 屬性所識別的元件之設計階段執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd16b-130">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method to create the design time instance of the component identified by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> property.</span></span> <span data-ttu-id="bd16b-131">此方法會傳回 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 物件，它是 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 介面的 Managed 包裝函數。</span><span class="sxs-lookup"><span data-stu-id="bd16b-131">This method returns the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> object, which is the managed wrapper for the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>  
  
 <span data-ttu-id="bd16b-132">請盡可能使用設計階段執行個體的方法來修改元件，而不要採用直接修改元件中繼資料的方式。</span><span class="sxs-lookup"><span data-stu-id="bd16b-132">Whenever possible, you should modify a component by using the methods of the design-time instance instead of by modifying the component metadata directly.</span></span> <span data-ttu-id="bd16b-133">雖然在中繼資料中有一些項目是必須直接設定的 (例如連接)，不過，通常不建議直接修改中繼資料，因為您會略過元件監視並驗證變更的能力。</span><span class="sxs-lookup"><span data-stu-id="bd16b-133">Although there are items in the metadata that you must set directly, such as connections, generally it is inadvisable to modify the metadata directly because you bypass the ability of the component to monitor and validate changes.</span></span>  
  
## <a name="assigning-connections"></a><span data-ttu-id="bd16b-134">指派連接</span><span class="sxs-lookup"><span data-stu-id="bd16b-134">Assigning Connections</span></span>  
 <span data-ttu-id="bd16b-135">有些元件 (例如 OLE DB 來源元件) 需要外部資料的連接，並為了此用途使用封裝中現有的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件。</span><span class="sxs-lookup"><span data-stu-id="bd16b-135">Some components, such as the OLE DB Source component, require a connection to external data and use an existing <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object in the package for this purpose.</span></span> <span data-ttu-id="bd16b-136"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 屬性會指出元件所需的執行階段 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件數目。</span><span class="sxs-lookup"><span data-stu-id="bd16b-136">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> collection indicates the number of run-time <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects required by the component.</span></span> <span data-ttu-id="bd16b-137">如果計數大於零，則元件需要連接。</span><span class="sxs-lookup"><span data-stu-id="bd16b-137">If the count is greater than zero, the component requires a connection.</span></span> <span data-ttu-id="bd16b-138">藉由指定 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> 內第一個連接的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> 屬性，將連接管理員從封裝指派至元件。</span><span class="sxs-lookup"><span data-stu-id="bd16b-138">Assign a connection manager from the package to the component by specifying the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> properties of the first connection in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>.</span></span> <span data-ttu-id="bd16b-139">請注意，執行階段連線集合中的連線管理員名稱，必須符合從套件參考的連線管理員名稱。</span><span class="sxs-lookup"><span data-stu-id="bd16b-139">Note that the name of the connection manager in the run-time connection collection must match the name of the connection managerreferenced from the package.</span></span>  
  
## <a name="setting-the-values-of-custom-properties"></a><span data-ttu-id="bd16b-140">設定自訂屬性值</span><span class="sxs-lookup"><span data-stu-id="bd16b-140">Setting the Values of Custom Properties</span></span>  
 <span data-ttu-id="bd16b-141">在建立元件的設計階段執行個體之後，呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bd16b-141">After creating the design-time instance of the component, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="bd16b-142">此方法類似於建構函式，因為它會建立其自訂屬性及其輸入和輸出物件，以初始化新建立的元件。</span><span class="sxs-lookup"><span data-stu-id="bd16b-142">This method is similar to a constructor because it initializes a newly created component by creating its custom properties and its input and output objects.</span></span> <span data-ttu-id="bd16b-143">請勿在一個元件上呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 超過一次，因為元件可能會重設本身，並且遺失之前對其中繼資料所做的任何修改。</span><span class="sxs-lookup"><span data-stu-id="bd16b-143">Do not call <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> more than one time on a component, because the component may reset itself and lose any modifications previously made to its metadata.</span></span>  
  
 <span data-ttu-id="bd16b-144">元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> 包含該元件特有的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 物件之集合。</span><span class="sxs-lookup"><span data-stu-id="bd16b-144">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> of the component contains a collection of <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> objects specific to the component.</span></span> <span data-ttu-id="bd16b-145">與其他程式設計模型不同的是，物件的屬性在物件上永遠是可見的，而元件只會在您呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> 方法時，擴展其自訂屬性集合。</span><span class="sxs-lookup"><span data-stu-id="bd16b-145">Unlike other programming models, where the properties of an object are always visible on the object, components only populate their custom property collections when you call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="bd16b-146">在您呼叫方法之後，請使用元件設計階段執行個體的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> 方法，將值指派到其自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="bd16b-146">After you call method, use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> method of the design-time instance of the component to assign values to its custom properties.</span></span> <span data-ttu-id="bd16b-147">此方法會接受識別自訂屬性的名稱/值組，並提供它的新值。</span><span class="sxs-lookup"><span data-stu-id="bd16b-147">This method accepts a name/value pair that identifies the custom property and provides its new value.</span></span>  
  
## <a name="initializing-output-columns"></a><span data-ttu-id="bd16b-148">初始化輸出資料行</span><span class="sxs-lookup"><span data-stu-id="bd16b-148">Initializing Output Columns</span></span>  
 <span data-ttu-id="bd16b-149">在您將元件加入工作並設定它之後，會初始化物件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 中之資料行集合。</span><span class="sxs-lookup"><span data-stu-id="bd16b-149">After you add a component to the task and configure it, initialize the collection of columns in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> of the object.</span></span> <span data-ttu-id="bd16b-150">這個步驟對於來源元件特別重要，但是可能無法初始化轉換與目的地元件的資料行，因為它們通常與從上游元件收到的資料行相依。</span><span class="sxs-lookup"><span data-stu-id="bd16b-150">This step is especially relevant for source components, but may not initialize the columns for transformation and destination components because they generally depend on the columns that they receive from upstream components.</span></span>  
  
 <span data-ttu-id="bd16b-151">呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> 方法以初始化來源元件輸出中的資料行。</span><span class="sxs-lookup"><span data-stu-id="bd16b-151">Call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> method to initialize the columns in the outputs of a source component.</span></span> <span data-ttu-id="bd16b-152">因為元件不會自動連接到外部資料來源，所以請在呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> 之前先呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> 方法，以提供其外部資料來源的元件存取權，以及擴展其資料行中繼資料的能力。</span><span class="sxs-lookup"><span data-stu-id="bd16b-152">Because components do not automatically connect to external data sources, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> method before calling <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A> to provide the component access to its external data source and the ability to populate its column metadata.</span></span> <span data-ttu-id="bd16b-153">最後，呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> 方法以釋放連接。</span><span class="sxs-lookup"><span data-stu-id="bd16b-153">Finally, call the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A> method to release the connection.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="bd16b-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="bd16b-154">Next Step</span></span>  
 <span data-ttu-id="bd16b-155">在新增和設定元件之後，下一個步驟就是要在兩個元件之間建立路徑，也就是[在兩個元件之間建立路徑](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)主題所討論的內容。</span><span class="sxs-lookup"><span data-stu-id="bd16b-155">After adding and configuring the component, the next step is to create paths between components, which is discussed in the topic, [Creating a Path Between Two Components](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
## <a name="sample"></a><span data-ttu-id="bd16b-156">範例</span><span class="sxs-lookup"><span data-stu-id="bd16b-156">Sample</span></span>  
 <span data-ttu-id="bd16b-157">下列程式碼範例會將 OLE DB 來源元件加入資料流程工作，建立元件的設計階段執行個體，然後設定元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bd16b-157">The following code sample adds the OLE DB Source component to a data flow task, creates a design-time instance of the component, and configures the component's properties.</span></span> <span data-ttu-id="bd16b-158">這個範例需要 Microsoft.SqlServer.DTSRuntimeWrap 組件的額外參考。</span><span class="sxs-lookup"><span data-stu-id="bd16b-158">This example requires an additional reference to the assembly Microsoft.SqlServer.DTSRuntimeWrap.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Runtime.Package package = new Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Runtime.TaskHost thMainPipe = e as Runtime.TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Add an OLEDB connection manager to the package.  
      ConnectionManager cm = package.Connections.Add("OLEDB");  
      cm.Name = "OLEDB ConnectionManager";  
      cm.ConnectionString = "Data Source=(local);" +   
        "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" +   
        "Integrated Security=SSPI;"  
  
      // Add an OLE DB source to the data flow.  
      IDTSComponentMetaData100 component =   
        dataFlowTask.ComponentMetaDataCollection.New();  
      component.Name = "OLEDBSource";  
      component.ComponentClassID = "DTSAdapter.OleDbSource.1";  
      // You can also use the CLSID of the component instead of the PROGID.  
      //component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
      // Get the design time instance of the component.  
      CManagedComponentWrapper instance = component.Instantiate();  
  
      // Initialize the component  
      instance.ProvideComponentProperties();  
  
      // Specify the connection manager.  
      if (component.RuntimeConnectionCollection.Count > 0)  
      {  
        component.RuntimeConnectionCollection[0].ConnectionManager =   
          DtsConvert.GetExtendedInterface(package.Connections[0]);  
        component.RuntimeConnectionCollection[0].ConnectionManagerID =   
          package.Connections[0].ID;      }  
  
      // Set the custom properties.  
      instance.SetComponentProperty("AccessMode", 2);  
      instance.SetComponentProperty("SqlCommand",   
        "Select * from Production.Product");  
  
      // Reinitialize the metadata.  
      instance.AcquireConnections(null);  
      instance.ReinitializeMetaData();  
      instance.ReleaseConnections();  
  
      // Add other components to the data flow and connect them.  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Add an OLEDB connection manager to the package.  
    Dim cm As ConnectionManager = package.Connections.Add("OLEDB")  
    cm.Name = "OLEDB ConnectionManager"  
    cm.ConnectionString = "Data Source=(local);" & _  
      "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;"  
  
    ' Add an OLE DB source to the data flow.  
    Dim component As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component.Name = "OLEDBSource"  
    component.ComponentClassID = "DTSAdapter.OleDbSource.1"  
    ' You can also use the CLSID of the component instead of the PROGID.  
    'component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
    ' Get the design time instance of the component.  
    Dim instance As CManagedComponentWrapper = component.Instantiate()  
  
    ' Initialize the component.  
    instance.ProvideComponentProperties()  
  
    ' Specify the connection manager.  
    If component.RuntimeConnectionCollection.Count > 0 Then  
      component.RuntimeConnectionCollection(0).ConnectionManager = _  
        DtsConvert.GetExtendedInterface(package.Connections(0))  
      component.RuntimeConnectionCollection(0).ConnectionManagerID = _  
        package.Connections(0).ID  
    End If  
  
    ' Set the custom properties.  
    instance.SetComponentProperty("AccessMode", 2)  
    instance.SetComponentProperty("SqlCommand", _  
      "Select * from Production.Product")  
  
    ' Reinitialize the metadata.  
    instance.AcquireConnections(vbNull)  
    instance.ReinitializeMetaData()  
    instance.ReleaseConnections()  
  
    ' Add other components to the data flow and connect them.  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="bd16b-159">外部資源</span><span class="sxs-lookup"><span data-stu-id="bd16b-159">External Resources</span></span>  
 <span data-ttu-id="bd16b-160">blogs.msdn.com 上的部落格文章：[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) (EzAPI - 針對 SQL Server 2012 更新)。</span><span class="sxs-lookup"><span data-stu-id="bd16b-160">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="bd16b-161">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="bd16b-161">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bd16b-162">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="bd16b-162">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bd16b-163">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="bd16b-163">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bd16b-164">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="bd16b-164">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd16b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd16b-165">See Also</span></span>  
 [<span data-ttu-id="bd16b-166">以程式設計的方式連接資料流程元件</span><span class="sxs-lookup"><span data-stu-id="bd16b-166">Connecting Data Flow Components Programmatically</span></span>](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
  
  
