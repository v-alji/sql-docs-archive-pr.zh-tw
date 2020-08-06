---
title: 升級資料流程元件的版本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f494793a20f1cdcd108553278b82a44daeea75ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606986"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a><span data-ttu-id="d73f7-102">升級資料流程元件的版本</span><span class="sxs-lookup"><span data-stu-id="d73f7-102">Upgrading the Version of a Data Flow Component</span></span>
  <span data-ttu-id="d73f7-103">使用舊版元件建立的封裝，可能包含不再有效的中繼資料，例如在新版元件中使用方式已有所修改的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="d73f7-103">Packages that were created with an older version of your component may contain metadata that is no longer valid, such as custom properties whose usage has been modified in newer versions of the component.</span></span> <span data-ttu-id="d73f7-104">您可以覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 基底類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> 方法，以更新之前儲存在舊封裝的中繼資料，從而反映元件的目前屬性。</span><span class="sxs-lookup"><span data-stu-id="d73f7-104">You can override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class to update the metadata previously saved in older packages to reflect the current properties of your component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d73f7-105">當您為新版本的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 重新編譯自訂元件時，如果未變更元件的屬性，就不必變更 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-105">When you recompile a custom component for a new version of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], you do not have to change the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property if the component's properties have not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d73f7-106">範例</span><span class="sxs-lookup"><span data-stu-id="d73f7-106">Example</span></span>  
 <span data-ttu-id="d73f7-107">下列範例包含 2.0 版的虛構資料流程元件之程式碼。</span><span class="sxs-lookup"><span data-stu-id="d73f7-107">The following sample contains code from version 2.0 of a fictitious data flow component.</span></span> <span data-ttu-id="d73f7-108">新版本號碼是定義在 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> 的 <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> 屬性中。</span><span class="sxs-lookup"><span data-stu-id="d73f7-108">The new version number is defined in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="d73f7-109">該元件具有一個屬性，它定義如何處理超過臨界值的數值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-109">The component has a property that defines how numeric values that exceed a threshold are to be handled.</span></span> <span data-ttu-id="d73f7-110">在 1.0 版的虛構元件中，這個屬性名為 `RaiseErrorOnInvalidValue` 並接受 True 或 False 的布林值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-110">In version 1.0 of the fictitious component, this property was named `RaiseErrorOnInvalidValue` and accepted a Boolean value of true or false.</span></span> <span data-ttu-id="d73f7-111">在 2.0 版的虛構元件中，該屬性重新命名為 `InvalidValueHandling` 並接受自訂列舉的四個可能值之一。</span><span class="sxs-lookup"><span data-stu-id="d73f7-111">In version 2.0 of the fictitious component, the property has been renamed to `InvalidValueHandling` and accepts one of four possible values from a custom enumeration.</span></span>  
  
 <span data-ttu-id="d73f7-112">下列範例中覆寫的 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 方法會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d73f7-112">The overridden <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the following sample performs the following actions:</span></span>  
  
-   <span data-ttu-id="d73f7-113">取得元件的目前版本。</span><span class="sxs-lookup"><span data-stu-id="d73f7-113">Gets the current version of the component.</span></span>  
  
-   <span data-ttu-id="d73f7-114">取得舊的自訂屬性值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-114">Gets the value of the old custom property.</span></span>  
  
-   <span data-ttu-id="d73f7-115">移除自訂屬性集合中的舊屬性。</span><span class="sxs-lookup"><span data-stu-id="d73f7-115">Removes the old property from the custom property collection.</span></span>  
  
-   <span data-ttu-id="d73f7-116">若有可能的話，根據舊屬性值設定新自訂屬性值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-116">Sets the value of the new custom property based on the value of the old property, if possible.</span></span>  
  
-   <span data-ttu-id="d73f7-117">將版本中繼資料設定成元件的目前版本。</span><span class="sxs-lookup"><span data-stu-id="d73f7-117">Sets the version metadata to the current version of the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d73f7-118">資料流程引擎會在 *pipelineVersion* 參數中將自己的版本號碼傳遞至 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d73f7-118">The data flow engine passes its own version number into the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the *pipelineVersion* parameter.</span></span> <span data-ttu-id="d73f7-119">此參數在 1.0 版的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中沒有用處，但是在後續版本中可能會變成有用。</span><span class="sxs-lookup"><span data-stu-id="d73f7-119">This parameter is not useful in version 1.0 of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], but may become useful in subsequent versions.</span></span>  
  
 <span data-ttu-id="d73f7-120">範例程式碼只會使用兩個列舉值，以直接對應至自訂屬性之前的布林值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-120">The sample code uses only the two enumeration values that map directly to the prior Boolean values for the custom property.</span></span> <span data-ttu-id="d73f7-121">使用者可以透過元件的自訂使用者介面、在 [進階編輯器] 中或是以程式設計方式，選取其他可用的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d73f7-121">Users can select the other available enumeration values through the component's custom user interface, in the Advanced Editor, or programmatically.</span></span> <span data-ttu-id="d73f7-122">如需有關在 [進階編輯器] 中顯示自訂屬性之列舉值的資訊，請參閱[資料流程元件的設計階段方法](design-time-methods-of-a-data-flow-component.md)中的＜建立自訂屬性＞。</span><span class="sxs-lookup"><span data-stu-id="d73f7-122">For information on displaying enumeration values for a custom property in the Advanced Editor, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```  
  
<span data-ttu-id="d73f7-123">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="d73f7-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d73f7-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="d73f7-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d73f7-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="d73f7-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d73f7-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="d73f7-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
