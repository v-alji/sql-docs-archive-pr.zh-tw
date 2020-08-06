---
title: 驗證資料流程元件 | Microsoft Docs
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
- ReinitializeMetaData method
- Validate method
- component validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- data flow components [Integration Services], validating
- validation [Integration Services]
ms.assetid: 1a7d5925-b387-4e31-af7f-c7f3c5151040
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9a78588c1e75697235e62e8955b65da466a37ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594122"
---
# <a name="validating-a-data-flow-component"></a><span data-ttu-id="1c54f-102">驗證資料流程元件</span><span class="sxs-lookup"><span data-stu-id="1c54f-102">Validating a Data Flow Component</span></span>
  <span data-ttu-id="1c54f-103">提供 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法，可以避免執行設定不正確的元件。</span><span class="sxs-lookup"><span data-stu-id="1c54f-103">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class is provided to prevent execution of a component that is not configured correctly.</span></span> <span data-ttu-id="1c54f-104">使用這個方法可確認元件具有預期的輸入和輸出物件數、此元件的自訂屬性具有可接受的值，以及指定了任何需要的連接。</span><span class="sxs-lookup"><span data-stu-id="1c54f-104">Use this method to verify that a component has the expected number of input and output objects, that the custom properties of the component have acceptable values, and that any connections, if required, are specified.</span></span> <span data-ttu-id="1c54f-105">使用這個方法也可確認輸入和輸出集合內的資料行具有正確的資料類型，以及每一個資料行的 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> 都針對此元件適當地設定。</span><span class="sxs-lookup"><span data-stu-id="1c54f-105">Use this method also to verify that the columns in the input and output collections have the correct data types and that the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> of each column is set appropriately for the component.</span></span> <span data-ttu-id="1c54f-106">基底類別實作會協助驗證程序，其方式是檢查此元件的輸入資料行集合，並確保此集合中的每一個資料行都會參考上游元件之 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> 中的資料行。</span><span class="sxs-lookup"><span data-stu-id="1c54f-106">The base class implementation assists in the validation process by checking the input column collection of the component and ensuring that each column in the collection refers to a column in the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> of the upstream component.</span></span>  
  
## <a name="validate-method"></a><span data-ttu-id="1c54f-107">Validate 方法</span><span class="sxs-lookup"><span data-stu-id="1c54f-107">Validate Method</span></span>  
 <span data-ttu-id="1c54f-108">在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中編輯元件時，便會重複呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c54f-108">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method is called repeatedly when a component is edited in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="1c54f-109">您可以透過 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> 列舉傳回值及藉由公佈警告和錯誤，提供意見給此元件的設計人員和使用者。</span><span class="sxs-lookup"><span data-stu-id="1c54f-109">You can provide feedback to the designer and to users of the component through the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration return value, and by posting warnings and errors.</span></span> <span data-ttu-id="1c54f-110"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> 列舉包含可指示失敗的各個階段的三個值，以及第四個值 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>，該值會指出此元件是否已正確設定並準備好要執行。</span><span class="sxs-lookup"><span data-stu-id="1c54f-110">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> enumeration contains three values that indicate various stages of failure, and a fourth, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>, that indicates whether the component is correctly configured and ready to execute.</span></span>  
  
 <span data-ttu-id="1c54f-111"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> 值指出 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 中有錯誤存在，而且此元件可修復錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c54f-111">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> value indicates that an error exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>, and that the component can repair the errors.</span></span> <span data-ttu-id="1c54f-112">如果元件遇到了可以修復的中繼資料錯誤，它不應該修正 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 方法中的錯誤，而且驗證期間不應該修改 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>。</span><span class="sxs-lookup"><span data-stu-id="1c54f-112">If a component encounters a metadata error that it can repair, it should not fix the error in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method, and <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> should not be modified during validation.</span></span> <span data-ttu-id="1c54f-113">而是 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 方法應該只能傳回 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>，而且此元件應該在 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法的呼叫中修復此錯誤，如同本章節稍後所述。</span><span class="sxs-lookup"><span data-stu-id="1c54f-113">Instead, the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method should return only <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>, and the component should repair the error in a call to the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method, as described later in this section.</span></span>  
  
 <span data-ttu-id="1c54f-114"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> 值指出，此元件的錯誤可以在設計師中編輯此元件來加以修正。</span><span class="sxs-lookup"><span data-stu-id="1c54f-114">The <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> value indicates that the component has an error that can be rectified by editing the component in the designer.</span></span> <span data-ttu-id="1c54f-115">此錯誤通常是因為自訂屬性或是未指定或設定錯誤的必要連接所造成。</span><span class="sxs-lookup"><span data-stu-id="1c54f-115">The error is typically caused by a custom property or a required connection that is not specified or is set incorrectly.</span></span>  
  
 <span data-ttu-id="1c54f-116">最後的錯誤值是 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>，該值指出此元件發現的錯誤只有在直接修改了 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 屬性時才應該發生 (不論是編輯封裝 XML 或使用物件模型)。</span><span class="sxs-lookup"><span data-stu-id="1c54f-116">The final error value is <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>, which indicates that the component has discovered errors that should only occur if the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> property has been modified directly, either by editing the package XML or by using the object model.</span></span> <span data-ttu-id="1c54f-117">例如，當元件只加入了單一輸入，但是驗證作業發現 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> 中有一個以上的輸入存在時，就會發生這種錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c54f-117">For example, this kind of error occurs when a component has added only a single input, but validation discovers that more than one input exists in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>.</span></span> <span data-ttu-id="1c54f-118">若要修復產生這個傳回值的錯誤，只能重設此元件或是使用 [進階編輯器] 對話方塊中的 [重設] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1c54f-118">Errors that generate this return value can only be repaired by resetting the component by using the **Reset** button in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="1c54f-119">除了傳回錯誤值以外，元件還會藉由公佈驗證期間的警告或錯誤來提供意見。</span><span class="sxs-lookup"><span data-stu-id="1c54f-119">Besides returning error values, components provide feedback by posting warnings or errors during validation.</span></span> <span data-ttu-id="1c54f-120"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> 方法會提供這項機制。</span><span class="sxs-lookup"><span data-stu-id="1c54f-120">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A> methods provide this mechanism.</span></span> <span data-ttu-id="1c54f-121">當呼叫這些方法時，這些事件會在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 的 [錯誤清單] 視窗內公佈。</span><span class="sxs-lookup"><span data-stu-id="1c54f-121">When these methods are called, these events are posted in the **Error List** window of [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="1c54f-122">然後元件開發人員可以提供有關所發生之錯誤的直接意見給使用者，並在適當的情況下提供修正錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="1c54f-122">Component developers can then provide direct feedback to users on the errors that have occurred, and if appropriate, how to correct them.</span></span>  
  
 <span data-ttu-id="1c54f-123">下列程式碼範例會示範已覆寫的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 實作。</span><span class="sxs-lookup"><span data-stu-id="1c54f-123">The following code example shows an overridden implementation of <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    bool pbCancel = false;  
  
    // Validate that there is one input.  
    if (ComponentMetaData.InputCollection.Count != 1)  
    {  
    ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, out pbCancel);  
    return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Validate that the UserName custom property is set.  
    if (ComponentMetaData.CustomPropertyCollection["UserName"].Value == null || ((string)ComponentMetaData.CustomPropertyCollection["UserName"].Value).Length == 0)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISBROKEN;  
    }  
  
    // Validate that there is one output.  
    if (ComponentMetaData.OutputCollection.Count != 1)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Let the base class verify that the input column reflects the output   
    // of the upstream component.  
    return base.Validate();  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
  
 Dim pbCancel As Boolean = False  
  
 ' Validate that there is one input.  
 If Not (ComponentMetaData.InputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Validate that the UserName custom property is set.  
 If ComponentMetaData.CustomPropertyCollection("UserName").Value Is Nothing OrElse CType(ComponentMetaData.CustomPropertyCollection("UserName").Value, String).Length = 0 Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISBROKEN   
 End If   
  
 ' Validate that there is one output.  
 If Not (ComponentMetaData.OutputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Let the base class verify that the input column reflects the output   
 ' of the upstream component.  
  
 Return MyBase.Validate   
  
End Function  
```  
  
## <a name="reinitializemetadata-method"></a><span data-ttu-id="1c54f-124">ReinitializeMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="1c54f-124">ReinitializeMetaData Method</span></span>  
 <span data-ttu-id="1c54f-125">當您編輯的元件從其 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法傳回 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> 時，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計工具便會呼叫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1c54f-125">The <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method is called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer whenever you edit a component that returns <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> from its <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> method.</span></span> <span data-ttu-id="1c54f-126">元件包含的程式碼，應能偵測及修正此元件在驗證期間所指出的各項問題。</span><span class="sxs-lookup"><span data-stu-id="1c54f-126">Components should contain code that detects and corrects the problems identified by the component during validation.</span></span>  
  
 <span data-ttu-id="1c54f-127">下列範例所示的元件，會在驗證期間偵測問題，並使用 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> 方法修正這些錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c54f-127">The following example shows a component that detects problems during validation and fixes these errors in the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> method.</span></span>  
  
```csharp  
private bool areInputColumnsValid = true;  
public override DTSValidationStatus Validate()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
    bool Cancel = false;  
    foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
    {  
        try  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
        }  
        catch  
        {  
            ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, out Cancel);  
            areInputColumnsValid = false;  
            return DTSValidationStatus.VS_NEEDSNEWMETADATA;  
        }  
    }  
  
    return DTSValidationStatus.VS_ISVALID;  
}  
public override void ReinitializeMetaData()  
{  
    if (!areInputColumnsValid)  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection[0];  
        IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
        foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
  
            if (vColumn == null)  
                input.InputColumnCollection.RemoveObjectByID(column.ID);  
        }  
        areInputColumnsValid = true;  
    }  
}  
```  
  
```vb  
Private areInputColumnsValid As Boolean = True   
  
Public  Overrides Function Validate() As DTSValidationStatus   
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
 Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
 Dim Cancel As Boolean = False   
 For Each column As IDTSInputColumn100 In input.InputColumnCollection   
   Try   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
   Catch   
     ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, Cancel)   
     areInputColumnsValid = False   
     Return DTSValidationStatus.VS_NEEDSNEWMETADATA   
   End Try   
 Next   
 Return DTSValidationStatus.VS_ISVALID   
End Function   
  
Public  Overrides Sub ReinitializeMetaData()   
 If Not areInputColumnsValid Then   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
   Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
   For Each column As IDTSInputColumn100 In input.InputColumnCollection   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
     If vColumn Is Nothing Then   
       input.InputColumnCollection.RemoveObjectByID(column.ID)   
     End If   
   Next   
   areInputColumnsValid = True   
 End If   
End Sub  
```  
  
<span data-ttu-id="1c54f-128">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="1c54f-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1c54f-129">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="1c54f-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1c54f-130">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="1c54f-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1c54f-131">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="1c54f-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
