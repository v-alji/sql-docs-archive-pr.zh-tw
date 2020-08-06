---
title: 開發資料流程元件的使用者介面 | Microsoft Docs
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
- data flow components [Integration Services], custom editors
- user interfaces [Integration Services]
- custom data flow components [Integration Services], custom editors
- custom component editors [Integration Services]
- IDtsComponentUI interface
- UITypeName property
- custom user interface [Integration Services], custom data flow component
- editors [Integration Services]
ms.assetid: 10b829a1-609b-42e3-9070-cfe5a2bb698c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f97f21ad14a5fa67fb49192931a0cb46d0cb41da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688066"
---
# <a name="developing-a-user-interface-for-a-data-flow-component"></a><span data-ttu-id="89f54-102">開發資料流程元件的使用者介面</span><span class="sxs-lookup"><span data-stu-id="89f54-102">Developing a User Interface for a Data Flow Component</span></span>
  <span data-ttu-id="89f54-103">元件開發人員可為元件提供自訂使用者介面，當編輯此元件時會在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中顯示此使用者介面。</span><span class="sxs-lookup"><span data-stu-id="89f54-103">Component developers can provide a custom user interface for a component, which is displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] when the component is edited.</span></span> <span data-ttu-id="89f54-104">實作自訂使用者介面會為您提供通知功能，讓您知道何時在資料流程工作中加入及刪除此元件，以及何時要求此元件的協助。</span><span class="sxs-lookup"><span data-stu-id="89f54-104">Implementing a custom user interface provides you with notification when the component is added to or deleted from a data flow task, and when help is requested for the component.</span></span>

 <span data-ttu-id="89f54-105">如果您並未針對元件提供自訂使用者介面，使用者仍然可以使用進階編輯器來設定此元件和它的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="89f54-105">If you do not provide a custom user interface for your component, users can still configure the component and its custom properties by using the Advanced Editor.</span></span> <span data-ttu-id="89f54-106">您可以確保進階編輯器允許使用者適當地編輯自訂屬性值，其方式是在適當時使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> 屬性。</span><span class="sxs-lookup"><span data-stu-id="89f54-106">You can ensure that the Advanced Editor allows users to edit custom property values appropriately by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> properties of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> when appropriate.</span></span> <span data-ttu-id="89f54-107">如需詳細資訊，請參閱[資料流程元件的設計階段方法](design-time-methods-of-a-data-flow-component.md)中的＜建立自訂屬性＞。</span><span class="sxs-lookup"><span data-stu-id="89f54-107">For more information, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>

## <a name="setting-the-uitypename-property"></a><span data-ttu-id="89f54-108">設定 UITypeName 屬性</span><span class="sxs-lookup"><span data-stu-id="89f54-108">Setting the UITypeName Property</span></span>
 <span data-ttu-id="89f54-109">若要提供自訂使用者介面，開發人員必須將 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 屬性設定為可實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 介面的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="89f54-109">To provide a custom user interface, the developer must set the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> to the name of a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="89f54-110">當此元件設定這個屬性時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 會在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中編輯此元件時載入及呼叫自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="89f54-110">When this property is set by the component, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] loads and calls the custom user interface when the component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="89f54-111"><xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 屬性是以逗號分隔的字串，可識別此類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="89f54-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property is a comma-delimited string that identifies the fully qualified name of the type.</span></span> <span data-ttu-id="89f54-112">下列清單將依序顯示可識別此類型的元素：</span><span class="sxs-lookup"><span data-stu-id="89f54-112">The following list shows, in order, the elements that identify the type:</span></span>

-   <span data-ttu-id="89f54-113">類型名稱</span><span class="sxs-lookup"><span data-stu-id="89f54-113">Type name</span></span>

-   <span data-ttu-id="89f54-114">組件名稱</span><span class="sxs-lookup"><span data-stu-id="89f54-114">Assembly name</span></span>

-   <span data-ttu-id="89f54-115">檔案版本</span><span class="sxs-lookup"><span data-stu-id="89f54-115">File version</span></span>

-   <span data-ttu-id="89f54-116">文化特性</span><span class="sxs-lookup"><span data-stu-id="89f54-116">Culture</span></span>

-   <span data-ttu-id="89f54-117">公開金鑰 Token</span><span class="sxs-lookup"><span data-stu-id="89f54-117">Public key token</span></span>

 <span data-ttu-id="89f54-118">下列程式碼範例顯示一個衍生自 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 基底類別的類別，並指定 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="89f54-118">The following code example shows a class that derives from the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class and specifies the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> property.</span></span>

```csharp
[DtsPipelineComponent(
DisplayName="SampleComponent",
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...",
ComponentType = ComponentType.Transform)]
public class SampleComponent : PipelineComponent
{
//TODO: Implement the component here.
}
```

```vb
<DtsPipelineComponent(DisplayName="SampleComponent", _
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...", ComponentType=ComponentType.Transform)> _ 
Public Class SampleComponent 
 Inherits PipelineComponent 
End Class
```

## <a name="implementing-the-idtscomponentui-interface"></a><span data-ttu-id="89f54-119">實作 IDtsComponentUI 介面</span><span class="sxs-lookup"><span data-stu-id="89f54-119">Implementing the IDtsComponentUI Interface</span></span>
 <span data-ttu-id="89f54-120"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 介面包含了 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師在加入、刪除及編輯元件時所呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="89f54-120">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface contains methods that [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls when a component is added, deleted, and edited.</span></span> <span data-ttu-id="89f54-121">元件開發人員可以在這些方法的實作中提供程式碼，以便與此元件的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="89f54-121">Component developers can provide code in their implementation of these methods to interact with users of the component.</span></span>

 <span data-ttu-id="89f54-122">此類別通常會在與元件本身不同的組件內實作。</span><span class="sxs-lookup"><span data-stu-id="89f54-122">This class is typically implemented in an assembly separate from the component itself.</span></span> <span data-ttu-id="89f54-123">雖然不需要使用不同的組件，但是這樣會讓開發人員彼此單獨來建立及部署元件和使用者介面，並讓元件的二進位檔維持在很小的使用量。</span><span class="sxs-lookup"><span data-stu-id="89f54-123">Although use of a separate assembly is not required, this lets the developer build and deploy the component and the user interface independently of each other, and keeps the binary footprint of the component small.</span></span>

 <span data-ttu-id="89f54-124">實作自訂使用者介面可讓元件開發人員對於此元件有更大的控制權，因為它是在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中編輯。</span><span class="sxs-lookup"><span data-stu-id="89f54-124">Implementing a custom user interface gives the component developer more control over the component as it is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="89f54-125">例如，元件可在 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 方法中加入程式碼 (最初在資料流程工作中加入元件時會呼叫此方法)，並顯示一個精靈，引導使用者進行元件的初始組態設定。</span><span class="sxs-lookup"><span data-stu-id="89f54-125">For example, a component can add code to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> method, which is called when a component is initially added to a data flow task, and display a wizard that guides the user through the initial configuration of the component.</span></span>

 <span data-ttu-id="89f54-126">當您建立一個可實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 介面的類別之後，您必須加入程式碼，以回應使用者與此元件的互動。</span><span class="sxs-lookup"><span data-stu-id="89f54-126">After you have created a class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, you must add code to respond to user interaction with the component.</span></span> <span data-ttu-id="89f54-127"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法會提供此元件的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面，而且會在 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> 和 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="89f54-127">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface of the component, and is called before the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> and <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> methods.</span></span> <span data-ttu-id="89f54-128">這個參考應該儲存在私用成員變數中，而且會在之後用來修改此元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="89f54-128">This reference should be stored in a private member variable and used to modify the component's metadata thereafter.</span></span>

## <a name="modifying-a-component-and-persisting-changes"></a><span data-ttu-id="89f54-129">修改元件及保存變更</span><span class="sxs-lookup"><span data-stu-id="89f54-129">Modifying a Component and Persisting Changes</span></span>
 <span data-ttu-id="89f54-130"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面會當做參數提供給 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="89f54-130">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface is provided as a parameter to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method.</span></span> <span data-ttu-id="89f54-131">這個參考應該由使用者介面程式碼快取在成員變數中，然後用來修改此元件，以回應使用者與使用者介面的互動。</span><span class="sxs-lookup"><span data-stu-id="89f54-131">This reference should be cached in a member variable by the user interface code, and then used to modify the component in response to user interaction with the user interface.</span></span>

 <span data-ttu-id="89f54-132">雖然您可以透過 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 介面直接修改此元件，但是比較好的作法是使用 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 方法建立 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="89f54-132">Although you can modify the component directly through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, it is better to create an instance of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A> method.</span></span> <span data-ttu-id="89f54-133">當您使用此介面直接編輯元件時，您會略過此元件的驗證防護。</span><span class="sxs-lookup"><span data-stu-id="89f54-133">When you edit the component directly by using the interface, you bypass the component's validation safeguards.</span></span> <span data-ttu-id="89f54-134">透過 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> 使用此元件之設計階段執行個體的優點如下：您可確保此元件可控制對它所做的變更。</span><span class="sxs-lookup"><span data-stu-id="89f54-134">The advantage of using the design-time instance of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> is that you ensure that the component has control over the changes made to it.</span></span>

 <span data-ttu-id="89f54-135"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法的傳回值會決定對元件所做的變更是會保存下來還是捨棄。</span><span class="sxs-lookup"><span data-stu-id="89f54-135">The return value of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method determines whether changes made to a component are persisted or discarded.</span></span> <span data-ttu-id="89f54-136">當這個方法傳回 `false` 時，所有的變更都會被捨棄；`true` 會保存對此元件所做的變更，並將此封裝標示為需要儲存。</span><span class="sxs-lookup"><span data-stu-id="89f54-136">When this method returns `false`, all changes are discarded; `true` persists the changes to the component and marks the package as needing to be saved.</span></span>

### <a name="using-the-services-of-the-ssis-designer"></a><span data-ttu-id="89f54-137">使用 SSIS 設計師的服務</span><span class="sxs-lookup"><span data-stu-id="89f54-137">Using the Services of the SSIS Designer</span></span>
 <span data-ttu-id="89f54-138"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> 方法的 `IServiceProvider` 參數會提供對下列 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師服務的存取權：</span><span class="sxs-lookup"><span data-stu-id="89f54-138">The `IServiceProvider` parameter of the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> method provides access to the following services of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer:</span></span>

|<span data-ttu-id="89f54-139">服務</span><span class="sxs-lookup"><span data-stu-id="89f54-139">Service</span></span>|<span data-ttu-id="89f54-140">描述</span><span class="sxs-lookup"><span data-stu-id="89f54-140">Description</span></span>|
|-------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsClipboardService>|<span data-ttu-id="89f54-141">用來判斷此元件是否在複製/貼上或剪下/貼上的作業中產生。</span><span class="sxs-lookup"><span data-stu-id="89f54-141">Used to determine whether the component was generated as part of a copy/paste or cut/paste operation.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionService>|<span data-ttu-id="89f54-142">用來存取現有的連接或是在封裝中建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="89f54-142">Used to access existing connections or to create new connections in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IErrorCollectionService>|<span data-ttu-id="89f54-143">當您需要擷取由此元件所引發的所有錯誤和警告，而不是只接收上一次的錯誤或警告時，用來從資料流程元件中擷取事件。</span><span class="sxs-lookup"><span data-stu-id="89f54-143">Used to capture events from data flow components when you need to capture all the errors and warnings raised by the component instead of receiving only the last error or warning.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsVariableService>|<span data-ttu-id="89f54-144">用來存取現有的變數或是在封裝中建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="89f54-144">Used to access existing variables or to create new variables in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsPipelineEnvironmentService>|<span data-ttu-id="89f54-145">由資料流程元件用來存取父資料流程工作及資料流程中的其他元件。</span><span class="sxs-lookup"><span data-stu-id="89f54-145">Used by data flow components to access the parent Data Flow task and other components in the data flow.</span></span> <span data-ttu-id="89f54-146">這項功能可用來開發類似「緩時變維度精靈」的元件，該元件會視需要建立及連接其他資料流程元件。</span><span class="sxs-lookup"><span data-stu-id="89f54-146">This feature could be used to develop a component like the Slowly Changing Dimension Wizard that creates and connects additional data flow components as needed.</span></span>|

 <span data-ttu-id="89f54-147">這些服務會提供元件開發人員能夠在此元件載入所在的封裝內存取及建立物件的功能。</span><span class="sxs-lookup"><span data-stu-id="89f54-147">These services provide component developers the ability to access and create objects in the package in which the component is loaded.</span></span>

## <a name="sample"></a><span data-ttu-id="89f54-148">範例</span><span class="sxs-lookup"><span data-stu-id="89f54-148">Sample</span></span>
 <span data-ttu-id="89f54-149">下列程式碼範例示範如何整合一個可實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 介面的自訂使用者介面類別，以及一個當做元件之編輯器的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="89f54-149">The following code example shows the integration of a custom user interface class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface, and a Windows form that serves as the editor for a component.</span></span>

### <a name="custom-user-interface-class"></a><span data-ttu-id="89f54-150">自訂使用者介面類別</span><span class="sxs-lookup"><span data-stu-id="89f54-150">Custom User Interface Class</span></span>
 <span data-ttu-id="89f54-151">下列程式碼將示範實作 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> 介面的類別。</span><span class="sxs-lookup"><span data-stu-id="89f54-151">The following code shows the class that implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> interface.</span></span> <span data-ttu-id="89f54-152"><xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法會建立元件編輯器，然後顯示表單。</span><span class="sxs-lookup"><span data-stu-id="89f54-152">The <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method creates the component editor and then displays the form.</span></span> <span data-ttu-id="89f54-153">此表單的傳回值會決定是否保存對此元件所做的變更。</span><span class="sxs-lookup"><span data-stu-id="89f54-153">The return value of the form determines whether changes to the component are persisted.</span></span>

```csharp
using System;
using System.Windows.Forms;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Pipeline.Design;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    public class SampleComponentUI : IDtsComponentUI
    {
        IDTSComponentMetaData100 md;
        IServiceProvider sp;

        public void Help(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void New(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void Delete(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Variables vars, Connections cons)
        {
            // Create and display the form for the user interface.
            SampleComponentUIForm componentEditor = new SampleComponentUIForm(cons, vars, md);

            DialogResult result  = componentEditor.ShowDialog(parentWindow);

            if (result == DialogResult.OK)
                return true;

            return false;
        }
        public void Initialize(IDTSComponentMetaData100 dtsComponentMetadata, IServiceProvider serviceProvider)
        {
            // Store the component metadata.
            this.md = dtsComponentMetadata;
        }
    }
}
```

```vb
Imports System 
Imports System.Windows.Forms 
Imports Microsoft.SqlServer.Dts.Runtime 
Imports Microsoft.SqlServer.Dts.Pipeline.Design 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Class SampleComponentUI 
 Implements IDtsComponentUI 
   Private md As IDTSComponentMetaData100 
   Private sp As IServiceProvider 

   Public Sub Help(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub New(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub Delete(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal vars As Variables, ByVal cons As Connections) As Boolean 
     ' Create and display the form for the user interface.
     Dim componentEditor As SampleComponentUIForm = New SampleComponentUIForm(cons, vars, md) 
     Dim result As DialogResult = componentEditor.ShowDialog(parentWindow) 
     If result = DialogResult.OK Then 
       Return True 
     End If 
     Return False 
   End Function 

   Public Sub Initialize(ByVal dtsComponentMetadata As IDTSComponentMetaData100, ByVal serviceProvider As IServiceProvider) 
     Me.md = dtsComponentMetadata 
   End Sub 
 End Class 

End Namespace
```

### <a name="custom-editor"></a><span data-ttu-id="89f54-154">自訂編輯器</span><span class="sxs-lookup"><span data-stu-id="89f54-154">Custom Editor</span></span>
 <span data-ttu-id="89f54-155">下列程式碼示範在 <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> 方法的呼叫期間所顯示之 Windows Form 的實作。</span><span class="sxs-lookup"><span data-stu-id="89f54-155">The following code shows the implementation of the Windows form that is shown during the call to the <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> method.</span></span>

```csharp
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    public partial class SampleComponentUIForm : System.Windows.Forms.Form
    {
        private Connections connections;
        private Variables variables;
        private IDTSComponentMetaData100 metaData;
        private CManagedComponentWrapper designTimeInstance;
        private System.ComponentModel.IContainer components = null;

        public SampleComponentUIForm( Connections cons, Variables vars, IDTSComponentMetaData100 md)
        {
            variables = vars;
            connections = cons;
            metaData = md;
        }

        private void btnOk_Click(object sender, System.EventArgs e)
        {
            if (designTimeInstance == null)
                designTimeInstance = metaData.Instantiate();

            designTimeInstance.SetComponentProperty( "CustomProperty", txtCustomPropertyValue.Text);

            this.Close();
        }

        private void btnCancel_Click(object sender, System.EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System 
Imports System.Drawing 
Imports System.Collections 
Imports System.ComponentModel 
Imports System.Windows.Forms 
Imports System.Data 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Partial Class SampleComponentUIForm 
  Inherits System.Windows.Forms.Form 
   Private connections As Connections 
   Private variables As Variables 
   Private metaData As IDTSComponentMetaData100 
   Private designTimeInstance As CManagedComponentWrapper 
   Private components As System.ComponentModel.IContainer = Nothing 

   Public Sub New(ByVal cons As Connections, ByVal vars As Variables, ByVal md As IDTSComponentMetaData100) 
     variables = vars 
     connections = cons 
     metaData = md 
   End Sub 

   Private Sub btnOk_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     If designTimeInstance Is Nothing Then 
       designTimeInstance = metaData.Instantiate 
     End If 
     designTimeInstance.SetComponentProperty("CustomProperty", txtCustomPropertyValue.Text) 
     Me.Close 
   End Sub 

   Private Sub btnCancel_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     Me.Close 
   End Sub 
 End Class 

End Namespace
```

<span data-ttu-id="89f54-156">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="89f54-156">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="89f54-157">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="89f54-157">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="89f54-158">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="89f54-158">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="89f54-159">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="89f54-159">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="89f54-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89f54-160">See Also</span></span>
 [<span data-ttu-id="89f54-161">建立自訂資料流程元件</span><span class="sxs-lookup"><span data-stu-id="89f54-161">Creating a Custom Data Flow Component</span></span>](creating-a-custom-data-flow-component.md)


