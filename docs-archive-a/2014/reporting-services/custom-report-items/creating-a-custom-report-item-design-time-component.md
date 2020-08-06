---
title: 建立自訂報表項目設計階段元件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b663dc3b0a9c54d1674bf153ee09dd36e0de7a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585152"
---
# <a name="creating-a-custom-report-item-design-time-component"></a><span data-ttu-id="26a45-102">建立自訂報表項目設計階段元件</span><span class="sxs-lookup"><span data-stu-id="26a45-102">Creating a Custom Report Item Design-Time Component</span></span>
  <span data-ttu-id="26a45-103">自訂報表項目設計階段元件是可用於 Visual Studio 報表設計工具環境的控制項。</span><span class="sxs-lookup"><span data-stu-id="26a45-103">A custom report item design-time component is a control that can be used in the Visual Studio Report Designer environment.</span></span> <span data-ttu-id="26a45-104">自訂報表項目設計階段元件提供啟動的設計介面，這個介面與 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 屬性瀏覽器相整合，可接受拖放作業，並能夠提供自訂屬性編輯器。</span><span class="sxs-lookup"><span data-stu-id="26a45-104">The custom report item design-time component provides an activated design surface that can accept drag-and-drop operations, integration with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser, and the ability to provide custom property editors.</span></span>  
  
 <span data-ttu-id="26a45-105">藉由自訂報表項目設計階段元件，使用者可以在設計環境中將自訂報表項目放置於報表上，並在自訂報表項目上設定自訂屬性，然後再將自訂報表項目儲存為報表專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="26a45-105">With a custom report item design-time component, the user can position a custom report item on a report in the design environment, set custom data properties on the custom report item, and then save the custom report item as part of the report project.</span></span>  
  
 <span data-ttu-id="26a45-106">在程式開發環境中使用設計階段元件所設定的屬性，會由主設計環境序列化和還原序列化，然後儲存為報表定義語言 (RDL) 檔案中的元素。</span><span class="sxs-lookup"><span data-stu-id="26a45-106">The properties that are set using the design-time component in the development environment are serialized and deserialized by the host design environment and then stored as elements in the Report Definition Language (RDL) file.</span></span> <span data-ttu-id="26a45-107">當報表由報表處理器執行時，使用設計階段元件所設定的屬性會由報表處理器傳遞至自訂報表項目執行階段元件，這個元件會轉譯自訂報表項目，然後將其傳回給報表處理器。</span><span class="sxs-lookup"><span data-stu-id="26a45-107">When the report is executed by the report processor, the properties that are set using the design-time component are passed by the report processor to a custom report item run-time component, which renders the custom report item and passes it back to the report processor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26a45-108">自訂報表項目設計階段元件會實作為 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="26a45-108">The custom report item design-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component.</span></span> <span data-ttu-id="26a45-109">本文件將描述自訂報表項目設計階段元件特定的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="26a45-109">This document will describe implementation details specific to the custom report item design-time component.</span></span> <span data-ttu-id="26a45-110">如需使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 來開發元件的詳細資訊，請參閱 MSDN Library 中的 [Visual Studio 中的元件](https://go.microsoft.com/fwlink/?LinkId=116576)。</span><span class="sxs-lookup"><span data-stu-id="26a45-110">For more information about developing components using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see [Components in Visual Studio](https://go.microsoft.com/fwlink/?LinkId=116576) in the MSDN library.</span></span>  
  
 <span data-ttu-id="26a45-111">如需完全實作的自訂報表項目的範例，請參閱 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (SQL Server Reporting Services 產品範例)。</span><span class="sxs-lookup"><span data-stu-id="26a45-111">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="implementing-a-design-time-component"></a><span data-ttu-id="26a45-112">實作設計階段元件</span><span class="sxs-lookup"><span data-stu-id="26a45-112">Implementing a Design-Time Component</span></span>  
 <span data-ttu-id="26a45-113">自訂報表項目設計階段元件的主類別是繼承自 `Microsoft.ReportDesigner.CustomReportItemDesigner` 類別。</span><span class="sxs-lookup"><span data-stu-id="26a45-113">The main class of a custom report item design-time component is inherited from the `Microsoft.ReportDesigner.CustomReportItemDesigner` class.</span></span> <span data-ttu-id="26a45-114">除了用於 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 控制項的標準屬性外，元件類別還應該定義 `CustomReportItem` 屬性。</span><span class="sxs-lookup"><span data-stu-id="26a45-114">In addition to the standard attributes used for a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] control, your component class should define a `CustomReportItem` attribute.</span></span> <span data-ttu-id="26a45-115">這個屬性必須與定義於 reportserver.config 檔案中的自訂報表項目的名稱相對應。</span><span class="sxs-lookup"><span data-stu-id="26a45-115">This attribute must correspond to the name of the custom report item as it is defined in the reportserver.config file.</span></span> <span data-ttu-id="26a45-116">如需 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 屬性的清單，請參閱 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件集中的＜屬性＞。</span><span class="sxs-lookup"><span data-stu-id="26a45-116">For a list of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] attributes, see Attributes in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="26a45-117">下列程式碼範例示範套用至自訂報表項目設計階段控制項的屬性：</span><span class="sxs-lookup"><span data-stu-id="26a45-117">The following code example shows attributes being applied to a custom report item design-time control:</span></span>  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a><span data-ttu-id="26a45-118">初始化元件</span><span class="sxs-lookup"><span data-stu-id="26a45-118">Initializing the Component</span></span>  
 <span data-ttu-id="26a45-119">使用 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 類別傳遞自訂報表項目的使用者指定屬性。</span><span class="sxs-lookup"><span data-stu-id="26a45-119">You pass user-specified properties for a custom report item using a <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class.</span></span> <span data-ttu-id="26a45-120">您的 `CustomReportItemDesigner` 類別實作應該覆寫 `InitializeNewComponent` 方法，以建立元件 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 類別的新執行個體，並將其設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="26a45-120">Your implementation of the `CustomReportItemDesigner` class should override the `InitializeNewComponent` method to create a new instance of your component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class and set it to default values.</span></span>  
  
 <span data-ttu-id="26a45-121">下列程式碼範例示範自訂報表項目設計階段元件類別，這個類別會覆寫 `CustomReportItemDesigner.InitializeNewComponent` 方法以初始化元件的 <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 類別：</span><span class="sxs-lookup"><span data-stu-id="26a45-121">The following code example shows an example of a custom report item design-time component class overriding the `CustomReportItemDesigner.InitializeNewComponent` method to initialize the component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class:</span></span>  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a><span data-ttu-id="26a45-122">修改元件屬性</span><span class="sxs-lookup"><span data-stu-id="26a45-122">Modifying Component Properties</span></span>  
 <span data-ttu-id="26a45-123">您可以用數種方式在設計環境中修改 `CustomData` 屬性。</span><span class="sxs-lookup"><span data-stu-id="26a45-123">You can modify `CustomData` properties in the design environment in several ways.</span></span> <span data-ttu-id="26a45-124">您可以修改任何由設計階段元件所公開的屬性 (Property)，這些屬性都會藉由 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 屬性瀏覽器以 <xref:System.ComponentModel.BrowsableAttribute> 屬性 (Attribute) 標示。</span><span class="sxs-lookup"><span data-stu-id="26a45-124">You can modify any properties that are exposed by the design-time component that are marked with the <xref:System.ComponentModel.BrowsableAttribute> attribute by using the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser.</span></span> <span data-ttu-id="26a45-125">此外，您也可以藉由下列方式修改屬性：將項目拖曳到自訂報表項目的設計介面，或者在設計環境中以滑鼠右鍵按一下控制項，然後選取捷徑功能表的 [屬性]\*\*\*\* 以顯示自訂屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="26a45-125">In addition, you can modify properties by dragging items onto the custom report item's design surface, or by right-clicking the control in the design environment and selecting **Properties** on the shortcut menu to display a custom properties window.</span></span>  
  
 <span data-ttu-id="26a45-126">下列程式碼範例顯示套用了 <xref:System.ComponentModel.BrowsableAttribute> 屬性 (Attribute) 的 `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` 屬性 (Property)：</span><span class="sxs-lookup"><span data-stu-id="26a45-126">The following code example shows a `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` property that has the <xref:System.ComponentModel.BrowsableAttribute> attribute applied:</span></span>  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 <span data-ttu-id="26a45-127">您可以使用自訂屬性編輯器對話方塊來提供設計階段元件。</span><span class="sxs-lookup"><span data-stu-id="26a45-127">You can provide your design-time component with a custom properties editor dialog box.</span></span> <span data-ttu-id="26a45-128">自訂屬性編輯器實作應該繼承自 <xref:System.ComponentModel.ComponentEditor> 類別，而且會建立可用於屬性編輯的對話方塊執行個體。</span><span class="sxs-lookup"><span data-stu-id="26a45-128">The custom property editor implementation should inherit from the <xref:System.ComponentModel.ComponentEditor> class, and it should create an instance of a dialog box that can be used for property editing.</span></span>  
  
 <span data-ttu-id="26a45-129">下列範例示範繼承自 <xref:System.ComponentModel.ComponentEditor> 之類別的實作，並顯示自訂屬性編輯器對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26a45-129">The following example shows an implementation of a class that inherits from <xref:System.ComponentModel.ComponentEditor> and displays a custom property editor dialog box:</span></span>  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="26a45-130">您的自訂屬性編輯器對話方塊可以叫用報表設計工具運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="26a45-130">Your custom property editor dialog box can invoke the Report Designer Expression Editor.</span></span> <span data-ttu-id="26a45-131">在下列範例中，當使用者選取下拉式方塊中的第一個元素時就會叫用運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="26a45-131">In the following example, the Expression Editor is invoked when the user selects the first element in the combo box:</span></span>  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a><span data-ttu-id="26a45-132">使用設計工具動詞</span><span class="sxs-lookup"><span data-stu-id="26a45-132">Using Designer Verbs</span></span>  
 <span data-ttu-id="26a45-133">設計工具動詞命令是連結至事件處理常式的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="26a45-133">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="26a45-134">若要在設計環境中使用自訂報表項目執行階段控制項，您可以加入要顯示在元件之捷徑功能表的設計工具動詞命令。</span><span class="sxs-lookup"><span data-stu-id="26a45-134">You can add designer verbs that will appear in a component's shortcut menu when your custom report item run-time control is being used in the design environment.</span></span> <span data-ttu-id="26a45-135">您可以使用 `Verbs` 屬性，從執行階段元件傳回可用的設計工具動詞清單。</span><span class="sxs-lookup"><span data-stu-id="26a45-135">You can return the list of available designer verbs from your run-time component by using the `Verbs` property.</span></span>  
  
 <span data-ttu-id="26a45-136">下列程式碼範例示範加入至 <xref:System.ComponentModel.Design.DesignerVerbCollection> 的設計工具動詞和事件處理常式，以及事件處理常式程式碼：</span><span class="sxs-lookup"><span data-stu-id="26a45-136">The following code example shows a designer verb and an event handler being added to the <xref:System.ComponentModel.Design.DesignerVerbCollection>, as well as the event handler code:</span></span>  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a><span data-ttu-id="26a45-137">使用裝飾</span><span class="sxs-lookup"><span data-stu-id="26a45-137">Using Adornments</span></span>  
 <span data-ttu-id="26a45-138">自訂報表項目類型也可以實作 `Microsoft.ReportDesigner.Design.Adornment` 類別。</span><span class="sxs-lookup"><span data-stu-id="26a45-138">Custom report item classes can also implement a `Microsoft.ReportDesigner.Design.Adornment` class.</span></span> <span data-ttu-id="26a45-139">透過裝飾，自訂報表項目控制項可以在設計介面的主要矩形之外提供區域。</span><span class="sxs-lookup"><span data-stu-id="26a45-139">An adornment allows the custom report item control to provide areas outside the main rectangle of the design surface.</span></span> <span data-ttu-id="26a45-140">這些區域可以處理使用者介面事件，例如按一下滑鼠和拖放作業等。</span><span class="sxs-lookup"><span data-stu-id="26a45-140">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span> <span data-ttu-id="26a45-141">在 `Adornment` 命名空間中定義的類別 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` 是 <xref:System.Windows.Forms.Design.Behavior.Adorner> 在 Windows Forms 中找到之類別的傳遞執行。</span><span class="sxs-lookup"><span data-stu-id="26a45-141">The `Adornment` class that is defined in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` namespace is a pass-through implementation of the <xref:System.Windows.Forms.Design.Behavior.Adorner> class found in Windows Forms.</span></span> <span data-ttu-id="26a45-142">如需類別的完整檔 `Adorner` ，請參閱 MSDN library 中的[行為服務總覽](https://go.microsoft.com/fwlink/?LinkId=116673)。</span><span class="sxs-lookup"><span data-stu-id="26a45-142">For complete documentation on the `Adorner` class, see [Behavior Service Overview](https://go.microsoft.com/fwlink/?LinkId=116673) in the MSDN library.</span></span> <span data-ttu-id="26a45-143">如需可執行類別的範例程式碼 `Microsoft.ReportDesigner.Design.Adornment` ，請參閱[SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="26a45-143">For sample code that implements a `Microsoft.ReportDesigner.Design.Adornment` class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
 <span data-ttu-id="26a45-144">如需有關在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中進行程式開發和使用 Windows Form 的詳細資訊，請參閱 MSDN Library 中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="26a45-144">For more information about programming and using Windows Forms in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see these topics in the MSDN Library:</span></span>  
  
-   <span data-ttu-id="26a45-145">元件的設計階段屬性</span><span class="sxs-lookup"><span data-stu-id="26a45-145">Design-Time Attributes for Components</span></span>  
  
-   <span data-ttu-id="26a45-146">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的元件</span><span class="sxs-lookup"><span data-stu-id="26a45-146">Components in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
-   <span data-ttu-id="26a45-147">逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="26a45-147">Walkthrough: Creating a Windows Forms Control that Takes Advantage of Visual Studio Design-Time Features</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a45-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a45-148">See Also</span></span>  
 <span data-ttu-id="26a45-149">[自訂報表專案架構](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="26a45-149">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="26a45-150">[建立自訂報表專案執行時間元件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="26a45-150">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="26a45-151">[自訂報表專案類別庫](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="26a45-151">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="26a45-152">操作說明：部署自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="26a45-152">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
