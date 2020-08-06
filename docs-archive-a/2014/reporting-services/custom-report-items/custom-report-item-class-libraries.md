---
title: 自訂報表項目類別庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60f8cf912eb6ff3f5080e9cf757df40f37e65079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585150"
---
# <a name="custom-report-item-class-libraries"></a><span data-ttu-id="889b6-102">自訂報表項目類別庫</span><span class="sxs-lookup"><span data-stu-id="889b6-102">Custom Report Item Class Libraries</span></span>
  <span data-ttu-id="889b6-103">自訂報表項目使用 `Microsoft.ReportDesigner` 命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="889b6-103">Custom report items use classes from the `Microsoft.ReportDesigner` namespace.</span></span> <span data-ttu-id="889b6-104">用於實作自訂報表項目的類別可以分成兩個主要類別：設計為支援自訂報表項目基礎結構的唯一類別，以及封裝相關報表定義語言 (RDL) 元素之功能的 Managed 包裝函數類別。</span><span class="sxs-lookup"><span data-stu-id="889b6-104">The classes used to implement a custom report item can be grouped into two main categories: unique classes designed to support custom report item infrastructure, and managed wrapper classes that encapsulate the functionality of relevant Report Definition Language (RDL) elements.</span></span> <span data-ttu-id="889b6-105">如需如何使用這些類別的程式碼範例，請參閱 [SQL Server Reporting Services 產品範例](https://go.microsoft.com/fwlink/?LinkId=177889)。</span><span class="sxs-lookup"><span data-stu-id="889b6-105">For a code sample on how to use these classes, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-infrastructure-classes"></a><span data-ttu-id="889b6-106">自訂報表項目基礎結構類別</span><span class="sxs-lookup"><span data-stu-id="889b6-106">Custom Report Item Infrastructure Classes</span></span>  
 <span data-ttu-id="889b6-107">下列類別可用於實作自訂報表項目。</span><span class="sxs-lookup"><span data-stu-id="889b6-107">The following classes are used to implement a custom report item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="889b6-108">下表並非完整的清單，其中僅包含每個類別最常用的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="889b6-108">The following tables are not complete listings; they include only the most commonly used properties and methods for each class.</span></span>  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a><span data-ttu-id="889b6-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span><span class="sxs-lookup"><span data-stu-id="889b6-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span></span>  
 <span data-ttu-id="889b6-110">這是主要的自訂報表項目類別。</span><span class="sxs-lookup"><span data-stu-id="889b6-110">This is the main custom report item class.</span></span> <span data-ttu-id="889b6-111">自訂報表項目實作的主要類別必須繼承自這個類別。</span><span class="sxs-lookup"><span data-stu-id="889b6-111">The main class of your custom report item implementation must inherit from this class.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="889b6-112">公用屬性</span><span class="sxs-lookup"><span data-stu-id="889b6-112">Public Properties</span></span>  
  
|||  
|-|-|  
|`Name`|<span data-ttu-id="889b6-113">自訂報表項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="889b6-113">The name of the custom report item.</span></span>|  
|`Type`|<span data-ttu-id="889b6-114">自訂報表項目的類型。</span><span class="sxs-lookup"><span data-stu-id="889b6-114">The type of the custom report item.</span></span>|  
|`CustomData`|<span data-ttu-id="889b6-115"><xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> 物件，用來封裝在設計階段所指定的自訂報表項目資料屬性。</span><span class="sxs-lookup"><span data-stu-id="889b6-115">A <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> object that encapsulates the custom report item data properties specified at design time.</span></span>|  
|`CustomProperties`|<span data-ttu-id="889b6-116">自訂報表項目的自訂屬性集合。</span><span class="sxs-lookup"><span data-stu-id="889b6-116">A collection of custom properties for the custom report item.</span></span>|  
|`Height`|<span data-ttu-id="889b6-117">自訂報表項目控制項的高度。</span><span class="sxs-lookup"><span data-stu-id="889b6-117">The height of the custom report item control.</span></span>|  
|`Width`|<span data-ttu-id="889b6-118">自訂報表項目控制項的寬度。</span><span class="sxs-lookup"><span data-stu-id="889b6-118">The width of the custom report item control.</span></span>|  
|`Report`|<span data-ttu-id="889b6-119">報表層級屬性的容器，例如報表中資料集的清單。</span><span class="sxs-lookup"><span data-stu-id="889b6-119">A container for the report-level properties, such as the list of datasets in the report.</span></span>|  
|`AltReportItem`|<span data-ttu-id="889b6-120">替代報表項目物件，用於不支援自訂報表項目執行階段控制項之處。</span><span class="sxs-lookup"><span data-stu-id="889b6-120">The alternate report item object, to be used where the custom report item run-time control is not supported.</span></span>|  
|`Style`|<span data-ttu-id="889b6-121">自訂報表項目的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="889b6-121">The style properties for the custom report item.</span></span>|  
|`Adornment`|<span data-ttu-id="889b6-122">用於控制項互動式編輯的裝飾視窗。</span><span class="sxs-lookup"><span data-stu-id="889b6-122">An adornment window used for interactive editing of the control.</span></span>|  
|`Site`|<span data-ttu-id="889b6-123">元件的 `ISite`。</span><span class="sxs-lookup"><span data-stu-id="889b6-123">The `ISite` of the component.</span></span>|  
|`DesignerVerbCollection`|<span data-ttu-id="889b6-124">控制項捷徑功能表的自訂動詞命令陣列。</span><span class="sxs-lookup"><span data-stu-id="889b6-124">An array of custom verbs for the control's shortcut menu.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-125">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-125">Public Methods</span></span>  
  
|||  
|-|-|  
|`BeginEdit`|<span data-ttu-id="889b6-126">啟動控制項的互動式編輯。</span><span class="sxs-lookup"><span data-stu-id="889b6-126">Activates interactive editing for the control.</span></span>|  
|`DoDefaultAction`|<span data-ttu-id="889b6-127">在回應按兩下控制項或在控制項上按 Return 鍵時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-127">Called in response to double-clicking or pressing Return on the control.</span></span>|  
|`EndEdit`|<span data-ttu-id="889b6-128">停用控制項的互動式編輯。</span><span class="sxs-lookup"><span data-stu-id="889b6-128">Deactivates interactive editing for the control.</span></span>|  
|`GetService`|<span data-ttu-id="889b6-129">傳回表示服務的物件。</span><span class="sxs-lookup"><span data-stu-id="889b6-129">Returns an object which represents a service.</span></span>|  
|`InitializeNewComponent`|<span data-ttu-id="889b6-130">在建立新的自訂報表項目時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-130">Called when a new custom report item is created.</span></span>|  
|`Invalidate`|<span data-ttu-id="889b6-131">重新繪製控制項的整個介面。</span><span class="sxs-lookup"><span data-stu-id="889b6-131">Repaints the entire surface of the control.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|<span data-ttu-id="889b6-132">在物件拖曳到控制項上時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-132">Called when an object is dragged onto the control.</span></span>|  
|`OnPaint`|<span data-ttu-id="889b6-133">在回應 `Paint` 事件時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-133">Called in response to the `Paint` event.</span></span>|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a><span data-ttu-id="889b6-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span><span class="sxs-lookup"><span data-stu-id="889b6-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span></span>  
 <span data-ttu-id="889b6-135">這是用於識別自訂報表項目類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="889b6-135">This is the attribute used to identify the type of the custom report item.</span></span> <span data-ttu-id="889b6-136">此名稱必須符合 `Name` `ReportItem` 報表設計師設定檔中元素的 <> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="889b6-136">The name must match the value of the <`Name`> attribute of the `ReportItem` element in the Report Designer configuration file.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-137">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-137">Public Methods</span></span>  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|<span data-ttu-id="889b6-138">建構 CustomReportItemAttribute 物件。</span><span class="sxs-lookup"><span data-stu-id="889b6-138">Constructs the CustomReportItemAttribute object.</span></span>|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a><span data-ttu-id="889b6-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span><span class="sxs-lookup"><span data-stu-id="889b6-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span></span>  
 <span data-ttu-id="889b6-140">這是用於指定用於自訂報表項目設計師顯示名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="889b6-140">This is the attribute used to specify display name to use for the custom report item designer.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-141">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-141">Public Methods</span></span>  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|<span data-ttu-id="889b6-142">建構 LocalizedNameAttribute 物件。</span><span class="sxs-lookup"><span data-stu-id="889b6-142">Constructs the LocalizedNameAttribute object.</span></span>|  
  
### <a name="microsoftreportdesigneradornment"></a><span data-ttu-id="889b6-143">Microsoft.ReportDesigner.Adornment</span><span class="sxs-lookup"><span data-stu-id="889b6-143">Microsoft.ReportDesigner.Adornment</span></span>  
 <span data-ttu-id="889b6-144">`Adornment` 類別會由自訂報表項目設計階段元件用於在設計介面主要矩形之外提供區域。</span><span class="sxs-lookup"><span data-stu-id="889b6-144">The `Adornment` class is used by the custom report item design-time component to provide areas outside of the main rectangle of the design surface.</span></span> <span data-ttu-id="889b6-145">這些區域可以處理使用者介面事件，例如按一下滑鼠和拖放作業等。</span><span class="sxs-lookup"><span data-stu-id="889b6-145">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-146">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-146">Public Methods</span></span>  
  
|||  
|-|-|  
|`OnShow`|<span data-ttu-id="889b6-147">在啟動 `Adornment` 時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-147">Called when the `Adornment` is activated.</span></span>|  
|`OnHide`|<span data-ttu-id="889b6-148">在停用 `Adornment` 時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-148">Called when the `Adornment` is deactivated.</span></span>|  
|`Paint`|<span data-ttu-id="889b6-149">在回應 `Paint` 事件時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-149">Called in response to the `Paint` event.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|<span data-ttu-id="889b6-150">在物件拖曳到 `Adornment` 內時呼叫。</span><span class="sxs-lookup"><span data-stu-id="889b6-150">Called when an object is dragged into the `Adornment`.</span></span>|  
  
### <a name="microsoftreportdesigneradornerservice"></a><span data-ttu-id="889b6-151">Microsoft.ReportDesigner.AdornerService</span><span class="sxs-lookup"><span data-stu-id="889b6-151">Microsoft.ReportDesigner.AdornerService</span></span>  
 <span data-ttu-id="889b6-152">這個類別會用於提供顯示服務的集合，自訂報表項目使用此集合來支援自訂報表項目設計階段元件的 `Adornment` 物件。</span><span class="sxs-lookup"><span data-stu-id="889b6-152">This class is used to provide a collection of display services used by the custom report item to support `Adornment` objects for the custom report item design-time component.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="889b6-153">公用屬性</span><span class="sxs-lookup"><span data-stu-id="889b6-153">Public Properties</span></span>  
  
|||  
|-|-|  
|`AdornerWindowBounds`|<span data-ttu-id="889b6-154">裝飾項視窗的界限。</span><span class="sxs-lookup"><span data-stu-id="889b6-154">The bounds of the Adorner window.</span></span>|  
|`AdornerWindowRegion`|<span data-ttu-id="889b6-155">裝飾項視窗的區域。</span><span class="sxs-lookup"><span data-stu-id="889b6-155">The region of the Adorner window.</span></span>|  
|`AdornerWindowGraphics`|<span data-ttu-id="889b6-156">裝飾項視窗的圖形內容。</span><span class="sxs-lookup"><span data-stu-id="889b6-156">A graphics context for the Adorner window.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-157">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-157">Public Methods</span></span>  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|<span data-ttu-id="889b6-158">傳回翻譯成設計工具框架 (Frame) 座標的元件界限。</span><span class="sxs-lookup"><span data-stu-id="889b6-158">Returns the bounds of the component translated into designer frame coordinates.</span></span>|  
|`InvalidateAdorner`|<span data-ttu-id="889b6-159">停用裝飾項視窗。</span><span class="sxs-lookup"><span data-stu-id="889b6-159">Invalidates the Adorner window.</span></span>|  
|`PointToAdorner`|<span data-ttu-id="889b6-160">傳回翻譯成裝飾項視窗座標的點螢幕座標 (Screen Coordinate)。</span><span class="sxs-lookup"><span data-stu-id="889b6-160">Returns a point in screen coordinates translated to Adorner window coordinates.</span></span>|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a><span data-ttu-id="889b6-161">Microsoft.ReportDesigner.ExpressionEditor</span><span class="sxs-lookup"><span data-stu-id="889b6-161">Microsoft.ReportDesigner.ExpressionEditor</span></span>  
 <span data-ttu-id="889b6-162">這個類別可從自訂報表項目設計階段控制項用於叫用運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="889b6-162">This class can be used from your custom report item design-time control to invoke the Expression Editor.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="889b6-163">公用方法</span><span class="sxs-lookup"><span data-stu-id="889b6-163">Public Methods</span></span>  
  
|||  
|-|-|  
|`EditValue`|<span data-ttu-id="889b6-164">叫用運算式編輯器 (以給定的物件值初始化)。</span><span class="sxs-lookup"><span data-stu-id="889b6-164">Invokes the Expression Editor, initialized with the given object value.</span></span>|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a><span data-ttu-id="889b6-165">Microsoft.ReportDesigner.IFieldsDataObject</span><span class="sxs-lookup"><span data-stu-id="889b6-165">Microsoft.ReportDesigner.IFieldsDataObject</span></span>  
 <span data-ttu-id="889b6-166">這個類別是 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 欄位的集合，可用於支援設計環境中的拖放事件。</span><span class="sxs-lookup"><span data-stu-id="889b6-166">This class is a collection of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fields, and is used to support drag-and-drop events in the design environment.</span></span> <span data-ttu-id="889b6-167">繼承自 `IReportItemDataObject`。</span><span class="sxs-lookup"><span data-stu-id="889b6-167">Inherits from `IReportItemDataObject`.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="889b6-168">公用屬性</span><span class="sxs-lookup"><span data-stu-id="889b6-168">Public Properties</span></span>  
  
|||  
|-|-|  
|`DataSetName`|<span data-ttu-id="889b6-169">包含要卸除之欄位的資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="889b6-169">The name of the dataset containing the fields to be dropped.</span></span>|  
|`Fields`|<span data-ttu-id="889b6-170">要卸除的欄位集合 (`Microsoft.ReportDesigner.Field`)。</span><span class="sxs-lookup"><span data-stu-id="889b6-170">The collection of fields (`Microsoft.ReportDesigner.Field`) to be dropped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="889b6-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="889b6-171">See Also</span></span>  
 <span data-ttu-id="889b6-172">[&#40;SSRS&#41;的報表定義語言](../reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="889b6-172">[Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="889b6-173">[建立自訂報表專案執行時間元件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="889b6-173">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 [<span data-ttu-id="889b6-174">建立自訂報表項目設計階段元件</span><span class="sxs-lookup"><span data-stu-id="889b6-174">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
  
  
