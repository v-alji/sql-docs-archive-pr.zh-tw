---
title: 開發自訂工作的使用者介面 | Microsoft Docs
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
- custom user interfaces [Integration Services]
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- custom tasks [Integration Services], user interface
- custom user interface [Integration Services], custom tasks
- user interface [Integration Services]
- SSIS custom tasks, user interface
ms.assetid: 1e940cd1-c5f8-4527-b678-e89ba5dc398a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed96bbc302cba4c207e5ce7b2e4fb4b74fed4ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599593"
---
# <a name="developing-a-user-interface-for-a-custom-task"></a><span data-ttu-id="93ac1-102">開發自訂工作的使用者介面</span><span class="sxs-lookup"><span data-stu-id="93ac1-102">Developing a User Interface for a Custom Task</span></span>
  <span data-ttu-id="93ac1-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 物件模型會提供自訂工作開發人員能夠輕鬆地針對工作建立自訂使用者介面的能力 (該介面之後可以在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中整合及顯示)。</span><span class="sxs-lookup"><span data-stu-id="93ac1-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] object model provides custom task developers the ability to easily create a custom user interface for a task that can then be integrated and displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="93ac1-104">使用者介面可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中提供有用的資訊給使用者，然後指引使用者正確地設定自訂工作的屬性和設定。</span><span class="sxs-lookup"><span data-stu-id="93ac1-104">The user interface can provide helpful information to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and guide users to correctly configure the properties and settings of the custom task.</span></span>  
  
 <span data-ttu-id="93ac1-105">為工作開發自訂使用者介面牽涉到兩個重要類別的使用。</span><span class="sxs-lookup"><span data-stu-id="93ac1-105">Developing a custom user interface for a task involves using two important classes.</span></span> <span data-ttu-id="93ac1-106">下表將描述這些類別。</span><span class="sxs-lookup"><span data-stu-id="93ac1-106">The following table describes those classes.</span></span>  
  
|<span data-ttu-id="93ac1-107">類別</span><span class="sxs-lookup"><span data-stu-id="93ac1-107">Class</span></span>|<span data-ttu-id="93ac1-108">描述</span><span class="sxs-lookup"><span data-stu-id="93ac1-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<span data-ttu-id="93ac1-109">識別受管理的工作，並透過它的屬性來提供設計階段資訊，以控制 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師如何顯示物件以及與物件互動的屬性。</span><span class="sxs-lookup"><span data-stu-id="93ac1-109">An attribute that identifies a managed task, and supplies design-time information through its properties to control how [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer displays and interacts with the object.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|<span data-ttu-id="93ac1-110">此工作所使用，以便將此工作與其自訂使用者介面產生關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="93ac1-110">An interface used by the task to associate the task with its custom user interface.</span></span>|  
  
 <span data-ttu-id="93ac1-111">本章節描述當您為自訂工作開發使用者介面時 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性和 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 介面的角色，並提供有關如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師內建立、整合、部署及偵錯此工作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="93ac1-111">This section describes the role of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface when you are developing a user interface for a custom task, and provides details about how to create, integrate, deploy, and debug the task within [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="93ac1-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師針對此工作提供使用者介面的多個進入點：使用者可以在捷徑功能表上選取 [編輯]  、按兩下此工作，或是按一下屬性表底部的 [顯示編輯器]  連結。</span><span class="sxs-lookup"><span data-stu-id="93ac1-112">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer provides multiple entry points to the user interface for the task: the user can select **Edit** on the shortcut menu, double-click the task, or click the **Show Editor** link at the bottom of the property sheet.</span></span> <span data-ttu-id="93ac1-113">當使用者存取其中一個進入點時，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師就會尋找及載入包含此工作之使用者介面的組件。</span><span class="sxs-lookup"><span data-stu-id="93ac1-113">When the user accesses one of these entry points, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer locates and loads the assembly that contains the user interface for the task.</span></span> <span data-ttu-id="93ac1-114">此工作的使用者介面要負責建立對話方塊的屬性，該對話方塊會在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="93ac1-114">The user interface for the task is responsible for creating the properties dialog box that is displayed to the user in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="93ac1-115">工作和它的使用者介面是不同的實體。</span><span class="sxs-lookup"><span data-stu-id="93ac1-115">A task and its user interface are separate entities.</span></span> <span data-ttu-id="93ac1-116">它們應該在不同的組件中實作，以減少當地語系化、部署和維護工作。</span><span class="sxs-lookup"><span data-stu-id="93ac1-116">They should be implemented in separate assemblies to reduce localization, deployment, and maintenance work.</span></span> <span data-ttu-id="93ac1-117">工作 DLL 不會載入、呼叫，或是通常會包含有關其使用者介面的任何知識，除了在工作中編碼之 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性值內包含的資訊以外。</span><span class="sxs-lookup"><span data-stu-id="93ac1-117">The task DLL does not load, call, or generally contain any knowledge of its user interface, except for the information that is contained in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute values coded in the task.</span></span> <span data-ttu-id="93ac1-118">這是工作與其使用者介面產生關聯的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="93ac1-118">This is the only way that a task and its user interface are associated.</span></span>  
  
## <a name="the-dtstask-attribute"></a><span data-ttu-id="93ac1-119">DtsTask 屬性</span><span class="sxs-lookup"><span data-stu-id="93ac1-119">The DtsTask Attribute</span></span>  
 <span data-ttu-id="93ac1-120"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性會包含在工作類別程式碼中，好讓工作與其使用者介面產生關聯。</span><span class="sxs-lookup"><span data-stu-id="93ac1-120">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute is included in the task class code to associate a task with its user interface.</span></span> <span data-ttu-id="93ac1-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會使用此屬性 (Attribute) 的屬性 (Property) 來決定此工作如何顯示在設計師內。</span><span class="sxs-lookup"><span data-stu-id="93ac1-121">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the properties of the attribute to determine how to display the task in the designer.</span></span> <span data-ttu-id="93ac1-122">這些屬性包含顯示名稱和圖示 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="93ac1-122">These properties include the name to display and the icon, if any.</span></span>  
  
 <span data-ttu-id="93ac1-123">下表描述 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="93ac1-123">The following table describes the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute.</span></span>  
  
|<span data-ttu-id="93ac1-124">屬性</span><span class="sxs-lookup"><span data-stu-id="93ac1-124">Property</span></span>|<span data-ttu-id="93ac1-125">描述</span><span class="sxs-lookup"><span data-stu-id="93ac1-125">Description</span></span>|  
|--------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>|<span data-ttu-id="93ac1-126">在控制流程工具箱內顯示工作名稱。</span><span class="sxs-lookup"><span data-stu-id="93ac1-126">Displays the task name in the Control Flow toolbox.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>|<span data-ttu-id="93ac1-127">工作描述 (繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="93ac1-127">The task description (inherited from <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>).</span></span> <span data-ttu-id="93ac1-128">這個屬性會顯示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="93ac1-128">This property is shown in ToolTips.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A>|<span data-ttu-id="93ac1-129">顯示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中的圖示。</span><span class="sxs-lookup"><span data-stu-id="93ac1-129">The icon displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.RequiredProductLevel%2A>|<span data-ttu-id="93ac1-130">如果有使用的話，請將它設定為 <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> 列舉內的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="93ac1-130">If used, set it to one of the values in the <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> enumeration.</span></span> <span data-ttu-id="93ac1-131">例如： `RequiredProductLevel = DTSProductLevel.None` 。</span><span class="sxs-lookup"><span data-stu-id="93ac1-131">For example, `RequiredProductLevel = DTSProductLevel.None`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskContact%2A>|<span data-ttu-id="93ac1-132">保留連絡人資訊給此工作需要技術支援的情況使用。</span><span class="sxs-lookup"><span data-stu-id="93ac1-132">Holds contact information for occasions when the task requires technical support.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskType%2A>|<span data-ttu-id="93ac1-133">指派類型給此工作。</span><span class="sxs-lookup"><span data-stu-id="93ac1-133">Assigns a type to the task.</span></span>|  
|<span data-ttu-id="93ac1-134">Attribute.TypeId</span><span class="sxs-lookup"><span data-stu-id="93ac1-134">Attribute.TypeId</span></span>|<span data-ttu-id="93ac1-135">在衍生類別中實作時，取得這個屬性的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="93ac1-135">When implemented in a derived class, gets a unique identifier for this Attribute.</span></span> <span data-ttu-id="93ac1-136">如需詳細資訊，請參閱 .NET Framework 類別庫中的 `Attribute.TypeID` 屬性。</span><span class="sxs-lookup"><span data-stu-id="93ac1-136">For more information, see `Attribute.TypeID` property in the .NET Framework Class Library.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>|<span data-ttu-id="93ac1-137">此組件的類型名稱，由 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師用來載入此組件。</span><span class="sxs-lookup"><span data-stu-id="93ac1-137">The type name of the assembly that is used by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to load the assembly.</span></span> <span data-ttu-id="93ac1-138">這個屬性是用來尋找此工作的使用者介面組件。</span><span class="sxs-lookup"><span data-stu-id="93ac1-138">This property is used to find the user interface assembly for the task.</span></span>|  
  
 <span data-ttu-id="93ac1-139">下列程式碼範例會顯示 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 的面貌 (在類別定義上方編碼)。</span><span class="sxs-lookup"><span data-stu-id="93ac1-139">The following code example shows the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> as it would look, coded above the class definition.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
 <span data-ttu-id="93ac1-140">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會使用此屬性 (Attribute) 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> 屬性 (Property)，該屬性 (Attribute) 包含組件名稱、類型名稱、版本、文化特性和公開金鑰 Token，以便在全域組件快取 (GAC) 中尋找組件，並載入它供設計師使用。</span><span class="sxs-lookup"><span data-stu-id="93ac1-140">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property of the attribute that includes the assembly name, type name, version, culture, and public key token, to locate the assembly in the Global Assembly Cache (GAC) and load it for use by the designer.</span></span>  
  
 <span data-ttu-id="93ac1-141">當找到組件以後，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會使用此屬性 (Attribute) 中的其他屬性 (Property)，在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中顯示有關此工作的其他資訊，例如此工作的名稱、圖示和描述。</span><span class="sxs-lookup"><span data-stu-id="93ac1-141">After the assembly has been located, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the other properties in the attribute to display additional information about the task in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, such as the name, icon, and description of the task.</span></span>  
  
 <span data-ttu-id="93ac1-142"><xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 屬性會指定此工作要如何呈現給使用者。</span><span class="sxs-lookup"><span data-stu-id="93ac1-142">The <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> properties specify how the task is presented to the user.</span></span> <span data-ttu-id="93ac1-143"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> 屬性包含內嵌在使用者介面組件內之圖示的資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="93ac1-143">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> property contains the resource ID of the icon embedded in the user interface assembly.</span></span> <span data-ttu-id="93ac1-144">此設計師會從組件中依照識別碼載入圖示資源，並在此工作加入到封裝時，將它顯示在工具箱和設計介面上的工作名稱旁邊。</span><span class="sxs-lookup"><span data-stu-id="93ac1-144">The designer loads the icon resource by ID from the assembly, and displays it next to the task name in the toolbox and on the designer surface when the task is added to a package.</span></span> <span data-ttu-id="93ac1-145">如果工作不提供圖示資源，設計師會針對此工作使用預設圖示。</span><span class="sxs-lookup"><span data-stu-id="93ac1-145">If a task does not provide an icon resource, the designer uses a default icon for the task.</span></span>  
  
## <a name="the-idtstaskui-interface"></a><span data-ttu-id="93ac1-146">IDTSTaskUI 介面</span><span class="sxs-lookup"><span data-stu-id="93ac1-146">The IDTSTaskUI Interface</span></span>  
 <span data-ttu-id="93ac1-147"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 介面會定義 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師所呼叫之方法和屬性的集合，以初始化及顯示與此工作有關的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="93ac1-147">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface defines the collection of methods and properties called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to initialize and display the user interface associated with the task.</span></span> <span data-ttu-id="93ac1-148">當叫用工作的使用者介面時，設計師會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> 方法 (當您撰寫此方法時，它會由工作使用者介面所實作)，然後分別提供此工作和封裝的 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合當做參數。</span><span class="sxs-lookup"><span data-stu-id="93ac1-148">When the user interface for a task is invoked, the designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> method, implemented by the task user interface when you wrote it, and then provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collections of the task and package, respectively, as parameters.</span></span> <span data-ttu-id="93ac1-149">這些集合會儲存在本機，而且之後會在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法中使用。</span><span class="sxs-lookup"><span data-stu-id="93ac1-149">These collections are stored locally, and used subsequently in the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method.</span></span>  
  
 <span data-ttu-id="93ac1-150">設計師會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法，要求顯示於 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中的視窗。</span><span class="sxs-lookup"><span data-stu-id="93ac1-150">The designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method to request the window that is displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="93ac1-151">此工作會建立包含此工作之使用者介面的視窗執行個體，並將此使用者介面傳回給設計師以供顯示。</span><span class="sxs-lookup"><span data-stu-id="93ac1-151">The task creates an instance of the window that contains the user interface for the task, and returns the user interface to the designer for display.</span></span> <span data-ttu-id="93ac1-152">一般來說，<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 物件會透過多載建構函式提供給視窗，好讓它們可用於設定工作。</span><span class="sxs-lookup"><span data-stu-id="93ac1-152">Typically, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> objects are provided to the window through an overloaded constructor so they can be used to configure the task.</span></span>  
  
 <span data-ttu-id="93ac1-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會呼叫工作使用者介面的 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> 方法，以顯示此工作的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="93ac1-153">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method of the task UI to display the user interface for the task.</span></span> <span data-ttu-id="93ac1-154">此工作使用者介面會從這個方法傳回 Windows Form，而 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會將這個表單顯示為強制回應對話方塊。</span><span class="sxs-lookup"><span data-stu-id="93ac1-154">The task user interface returns the Windows form from this method, and [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer shows this form as a modal dialog box.</span></span> <span data-ttu-id="93ac1-155">當關閉此表單時，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會檢查此表單之 `DialogResult` 屬性的值，以判斷此工作是否已經修改過，以及是否應該儲存這些修改。</span><span class="sxs-lookup"><span data-stu-id="93ac1-155">When the form is closed, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer examines the value of the `DialogResult` property of the form to determine whether the task has been modified and if these modifications should be saved.</span></span> <span data-ttu-id="93ac1-156">如果 `DialogResult` 屬性的值是 `OK`，[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會呼叫此工作的保存方法來儲存變更，否則會捨棄這些變更。</span><span class="sxs-lookup"><span data-stu-id="93ac1-156">If the value of the `DialogResult` property is `OK`, the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the persistence methods of the task to save the changes; otherwise, the changes are discarded.</span></span>  
  
 <span data-ttu-id="93ac1-157">下列程式碼範例會實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> 介面，並假設有一個名為 SampleTaskForm 的 Windows Form 類別存在。</span><span class="sxs-lookup"><span data-stu-id="93ac1-157">The following code sample implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface, and assumes the existence of a Windows form class named SampleTaskForm.</span></span>  
  
```csharp  
using System;  
using System.Windows.Forms;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Design;  
  
namespace Sample  
{  
   public class HelloWorldTaskUI : IDtsTaskUI  
   {  
      TaskHost   taskHost;  
      Connections connections;  
      public void Initialize(TaskHost taskHost, IServiceProvider serviceProvider)  
      {  
         this.taskHost = taskHost;  
         IDtsConnectionService cs = serviceProvider.GetService  
         ( typeof( IDtsConnectionService ) ) as   IDtsConnectionService;   
         this.connections = cs.GetConnections();  
      }  
      public ContainerControl GetView()  
      {  
        return new HelloWorldTaskForm(this.taskHost, this.connections);  
      }  
     public void Delete(IWin32Window parentWindow)  
     {  
     }  
     public void New(IWin32Window parentWindow)  
     {  
     }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Design  
Imports System.Windows.Forms  
  
Public Class HelloWorldTaskUI  
  Implements IDtsTaskUI  
  
  Dim taskHost As TaskHost  
  Dim connections As Connections  
  
  Public Sub Initialize(ByVal taskHost As TaskHost, ByVal serviceProvider As IServiceProvider) _  
    Implements IDtsTaskUI.Initialize  
  
    Dim cs As IDtsConnectionService  
  
    Me.taskHost = taskHost  
    cs = DirectCast(serviceProvider.GetService(GetType(IDtsConnectionService)), IDtsConnectionService)  
    Me.connections = cs.GetConnections()  
  
  End Sub  
  
  Public Function GetView() As ContainerControl _  
    Implements IDtsTaskUI.GetView  
  
    Return New HelloWorldTaskForm(Me.taskHost, Me.connections)  
  
  End Function  
  
  Public Sub Delete(ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.Delete  
  
  End Sub  
  
  Public Sub [New](ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.[New]  
  
  End Sub  
  
End Class  
```  
  
<span data-ttu-id="93ac1-158">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="93ac1-158">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="93ac1-159">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="93ac1-159">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="93ac1-160">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="93ac1-160">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="93ac1-161">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="93ac1-161">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ac1-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93ac1-162">See Also</span></span>  
 <span data-ttu-id="93ac1-163">[建立自訂工作](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="93ac1-163">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="93ac1-164">[撰寫自訂工作的程式碼](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="93ac1-164">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="93ac1-165">開發自訂工作的使用者介面</span><span class="sxs-lookup"><span data-stu-id="93ac1-165">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
