---
title: 資料流程元件的設計階段方法 | Microsoft Docs
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
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e33fc4eb5805318dac217d2c5cbaedfd4bca70fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597964"
---
# <a name="design-time-methods-of-a-data-flow-component"></a><span data-ttu-id="105e1-102">資料流程元件的設計階段方法</span><span class="sxs-lookup"><span data-stu-id="105e1-102">Design-time Methods of a Data Flow Component</span></span>
  <span data-ttu-id="105e1-103">據說在執行之前，資料流程工作會設計狀態階段進行累加變更。</span><span class="sxs-lookup"><span data-stu-id="105e1-103">Before execution, the data flow task is said to be in a design-time state, as it undergoes incremental changes.</span></span> <span data-ttu-id="105e1-104">變更可包括元件的加入或移除、連接元件的路徑物件之加入或移除，以及對於元件中繼資料的變更。</span><span class="sxs-lookup"><span data-stu-id="105e1-104">Changes may include the addition or removal of components, the addition or removal of the path objects that connect components, and changes to the metadata of the components.</span></span> <span data-ttu-id="105e1-105">當中繼資料變更發生時，元件可以監視變更並對其做出反應。</span><span class="sxs-lookup"><span data-stu-id="105e1-105">When metadata changes occur, the component can monitor and react to the changes.</span></span> <span data-ttu-id="105e1-106">例如，元件可以不允許某些變更，或是做其他變更以回應變更。</span><span class="sxs-lookup"><span data-stu-id="105e1-106">For example, a component can disallow certain changes or make additional changes in response to a change.</span></span> <span data-ttu-id="105e1-107">在設計階段，設計工具會透過設計階段 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 介面與元件互動。</span><span class="sxs-lookup"><span data-stu-id="105e1-107">At design time, the designer interacts with a component through the design-time <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span>

## <a name="design-time-implementation"></a><span data-ttu-id="105e1-108">設計階段實作</span><span class="sxs-lookup"><span data-stu-id="105e1-108">Design-Time Implementation</span></span>
 <span data-ttu-id="105e1-109">元件的設計階段介面是由 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 介面所描述。</span><span class="sxs-lookup"><span data-stu-id="105e1-109">The design-time interface of a component is described by the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface.</span></span> <span data-ttu-id="105e1-110">雖然您未明確地實作這個介面，不過熟悉定義在這個介面中的方法，將可協助您了解 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基底類別的哪些方法與元件的設計階段執行個體對應。</span><span class="sxs-lookup"><span data-stu-id="105e1-110">Although you do not explicitly implement this interface, a familiarity with the methods defined in this interface will help you understand which methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class correspond to the design-time instance of a component.</span></span>

 <span data-ttu-id="105e1-111">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中載入元件時，會具現化元件的設計階段執行個體，並在編輯元件時，呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> 介面的方法。</span><span class="sxs-lookup"><span data-stu-id="105e1-111">When a component is loaded in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], the design-time instance of the component is instantiated and the methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> interface are called as the component is edited.</span></span> <span data-ttu-id="105e1-112">基底類別的實作可讓您只覆寫元件所需的方法。</span><span class="sxs-lookup"><span data-stu-id="105e1-112">The implementation of the base class lets you override only those methods that your component requires.</span></span> <span data-ttu-id="105e1-113">在許多情況下，您可以覆寫這些方法以防止對元件的不當編輯。</span><span class="sxs-lookup"><span data-stu-id="105e1-113">In many cases, you may override these methods to prevent inappropriate edits to a component.</span></span> <span data-ttu-id="105e1-114">例如，若要防止使用者將輸出加入元件，請覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="105e1-114">For example, to prevent users from adding an output to a component, override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A> method.</span></span> <span data-ttu-id="105e1-115">否則，呼叫由基底類別實作的此方法時，它會將輸出加入元件。</span><span class="sxs-lookup"><span data-stu-id="105e1-115">Otherwise, when the implementation of this method by the base class is called, it adds an output to the component.</span></span>

 <span data-ttu-id="105e1-116">不論元件的目的或功能為何，您都應該覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 與 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="105e1-116">Regardless of the purpose or functionality of your component, you should override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> methods.</span></span> <span data-ttu-id="105e1-117">如需 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 的詳細資訊，請參閱[驗證資料流程元件](validating-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="105e1-117">For more information about <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, see [Validating a Data Flow Component](validating-a-data-flow-component.md).</span></span>

## <a name="providecomponentproperties-method"></a><span data-ttu-id="105e1-118">提供 ComponentProperties 方法</span><span class="sxs-lookup"><span data-stu-id="105e1-118">ProvideComponentProperties Method</span></span>
 <span data-ttu-id="105e1-119">元件的初始化會發生在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="105e1-119">The initialization of a component occurs in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method.</span></span> <span data-ttu-id="105e1-120">當元件加入資料流程工作時，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會呼叫這個方法，此方法類似類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="105e1-120">This method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer when a component is added to the data flow task, and is similar to a class constructor.</span></span> <span data-ttu-id="105e1-121">元件開發人員應該在此方法呼叫期間，建立並初始化輸入、輸出和自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="105e1-121">Component developers should create and initialize their inputs, outputs, and custom properties during this method call.</span></span> <span data-ttu-id="105e1-122"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法與建構函式不同，因為它並不會在每次具現化元件的設計階段執行個體或是執行階段執行個體時呼叫。</span><span class="sxs-lookup"><span data-stu-id="105e1-122">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method differs from a constructor because it is not called every time that the design-time instance or run-time instance of the component is instantiated.</span></span>

 <span data-ttu-id="105e1-123">該方法的基底類別實作會將輸入和輸出加入元件，並將輸入的識別碼指派到 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="105e1-123">The base class implementation of the method adds an input and an output to the component and assigns the ID of the input to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A> property.</span></span> <span data-ttu-id="105e1-124">不過，在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，並未命名基底類別加入的輸入和輸出物件。</span><span class="sxs-lookup"><span data-stu-id="105e1-124">However, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the input and output objects added by the base class are not named.</span></span> <span data-ttu-id="105e1-125">如果封裝包含的元件所帶有的輸入或輸出物件未設定 Name 屬性，封裝將無法成功載入。</span><span class="sxs-lookup"><span data-stu-id="105e1-125">Packages that contain a component with input or output objects whose Name property is not set will not successfully load.</span></span> <span data-ttu-id="105e1-126">因此，當您使用基底實作時，必須將值明確地指派到預設輸入與輸出的 Name 屬性。</span><span class="sxs-lookup"><span data-stu-id="105e1-126">Therefore, when you use the base implementation, you must assign values explicitly to the Name property of the default input and output.</span></span>

```csharp
public override void ProvideComponentProperties()
{
    /// TODO: Reset the component.
    /// TODO: Add custom properties.
    /// TODO: Add input objects.
    /// TODO: Add output objects.
}
```

```vb
Public Overrides Sub ProvideComponentProperties()
    ' TODO: Reset the component.
    ' TODO: Add custom properties.
    ' TODO: Add input objects.
    ' TODO: Add output objects.
End Sub
```

### <a name="creating-custom-properties"></a><span data-ttu-id="105e1-127">建立自訂屬性</span><span class="sxs-lookup"><span data-stu-id="105e1-127">Creating Custom Properties</span></span>
 <span data-ttu-id="105e1-128">在呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> 方法時，元件開發人員應該將自訂屬性 (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) 加入元件。</span><span class="sxs-lookup"><span data-stu-id="105e1-128">The call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> method is where component developers should add custom properties (<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>) to the component.</span></span> <span data-ttu-id="105e1-129">自訂屬性沒有資料類型屬性。</span><span class="sxs-lookup"><span data-stu-id="105e1-129">Custom properties do not have a data type property.</span></span> <span data-ttu-id="105e1-130">自訂屬性的資料類型是由您指派至其 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> 屬性的值資料類型所設定。</span><span class="sxs-lookup"><span data-stu-id="105e1-130">The data type of a custom property is set by the data type of the value that you assign to its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A> property.</span></span> <span data-ttu-id="105e1-131">不過，在您將初始值指派到自訂屬性之後，您無法以不同的資料類型指派值。</span><span class="sxs-lookup"><span data-stu-id="105e1-131">However, after you have assigned an initial value to the custom property, you cannot assign a value with a different data type.</span></span>

> [!NOTE]
>  <span data-ttu-id="105e1-132"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 介面對於 `Object` 類型的屬性值之支援有限。</span><span class="sxs-lookup"><span data-stu-id="105e1-132">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> interface has limited support for property values of type `Object`.</span></span> <span data-ttu-id="105e1-133">您可以儲存為自訂屬性值的唯一物件是簡單類型的陣列，例如字串或是整數。</span><span class="sxs-lookup"><span data-stu-id="105e1-133">The only object that you can store as the value of a custom property is an array of simple types such as strings or integers.</span></span>

 <span data-ttu-id="105e1-134">您可以將自訂屬性的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> 屬性值設定成 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> 列舉的 `CPET_NOTIFY`，藉此指出自訂屬性支援屬性運算式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="105e1-134">You can indicate that your custom property supports property expressions by setting the value of its <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> property to `CPET_NOTIFY` from the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType> enumeration, as shown in the following example.</span></span> <span data-ttu-id="105e1-135">您不必加入任何程式碼以處理或是驗證使用者所輸入的屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="105e1-135">You do not have to add any code to handle or to validate the property expression entered by the user.</span></span> <span data-ttu-id="105e1-136">您可以為屬性設定預設值、驗證其值，以及正常地讀取和使用其值。</span><span class="sxs-lookup"><span data-stu-id="105e1-136">You can set a default value for the property, validate its value, and read and use its value normally.</span></span>

```csharp
IDTSCustomProperty100 myCustomProperty;
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;
```

```vb
Dim myCustomProperty As IDTSCustomProperty100
...
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY
```

 <span data-ttu-id="105e1-137">您可以使用屬性來限制使用者從列舉中選取自訂屬性值 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> ，如下列範例所示，這會假設您已定義名為的公用列舉 `MyValidValues` 。</span><span class="sxs-lookup"><span data-stu-id="105e1-137">You can limit users to selecting a custom property value from an enumeration by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> property, as shown in the following example, which assumes that you have defined a public enumeration named `MyValidValues`.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the type with the custom property.
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;
// Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne;  
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the type with the custom property.
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName 
' Now you can use the enumeration values directly.
customProperty.Value = MyValidValues.ValueOne
```

 <span data-ttu-id="105e1-138">如需詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022) 中的＜通用類型轉換＞與＜實作類型轉換子＞。</span><span class="sxs-lookup"><span data-stu-id="105e1-138">For more information, see "Generalized Type Conversion" and "Implementing a Type Converter" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

 <span data-ttu-id="105e1-139">您可以使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 屬性，為自訂屬性值指定自訂編輯器對話方塊，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="105e1-139">You can specify a custom editor dialog box for the value of your custom property by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property, as shown in the following example.</span></span> <span data-ttu-id="105e1-140">首先，如果您無法找到符合需求的現有 UI 類型編輯器，必須建立一個繼承自 `System.Drawing.Design.UITypeEditor`的自訂類型編輯器。</span><span class="sxs-lookup"><span data-stu-id="105e1-140">First, you must create a custom type editor that inherits from `System.Drawing.Design.UITypeEditor`, if you cannot locate an existing UI type editor class that fits your needs.</span></span>

```csharp
public class MyCustomTypeEditor : UITypeEditor
{
...
}
```

```vb
Public Class MyCustomTypeEditor
  Inherits UITypeEditor 
  ...
End Class
```

 <span data-ttu-id="105e1-141">接著將此類別指定為自訂屬性的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="105e1-141">Next, specify this class as the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> property of your custom property.</span></span>

```csharp
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();
customProperty.Name = "My Custom Property";
// This line associates the editor with the custom property.
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;
```

```vb
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New 
customProperty.Name = "My Custom Property" 
' This line associates the editor with the custom property.
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName
```

 <span data-ttu-id="105e1-142">如需詳細資訊，請參閱 [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022) 中的＜實作 UI 類型編輯器＞。</span><span class="sxs-lookup"><span data-stu-id="105e1-142">For more information, see "Implementing a UI Type Editor" in the [MSDN Library](https://go.microsoft.com/fwlink/?LinkId=7022).</span></span>

<span data-ttu-id="105e1-143">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="105e1-143">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="105e1-144">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="105e1-144">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="105e1-145">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="105e1-145">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="105e1-146">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="105e1-146">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="105e1-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="105e1-147">See Also</span></span>
 [<span data-ttu-id="105e1-148">資料流程元件的執行階段方法</span><span class="sxs-lookup"><span data-stu-id="105e1-148">Run-time Methods of a Data Flow Component</span></span>](run-time-methods-of-a-data-flow-component.md)


