---
title: 指令碼元件的程式碼撰寫和偵錯 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9363ad447ca3d0031289eafb1d8f616320fca5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597220"
---
# <a name="coding-and-debugging-the-script-component"></a><span data-ttu-id="e305e-102">指令碼元件的程式碼撰寫和偵錯</span><span class="sxs-lookup"><span data-stu-id="e305e-102">Coding and Debugging the Script Component</span></span>
  <span data-ttu-id="e305e-103">在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中，指令碼元件有中繼資料設計與程式碼設計兩種模式。</span><span class="sxs-lookup"><span data-stu-id="e305e-103">In [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata design mode and code design mode.</span></span> <span data-ttu-id="e305e-104">當您開啟 [指令碼轉換編輯器]  時，元件就會進入中繼資料設計模式，您可在其中設定中繼資料及元件屬性。</span><span class="sxs-lookup"><span data-stu-id="e305e-104">When you open the **Script Transformation Editor**, the component enters metadata design mode, in which you configure metadata and set component properties.</span></span> <span data-ttu-id="e305e-105">在您於中繼資料設計模式設定好指令碼元件的屬性和輸入及輸出後，就可以切換到程式碼設計模式編寫自訂的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e305e-105">After you have set the properties of the Script component and configured the input and outputs in metadata design mode, you can switch to code design mode to write your custom script.</span></span> <span data-ttu-id="e305e-106">如需中繼資料設計模式和程式碼設計模式的詳細資訊，請參閱[在指令碼元件編輯器中設定指令碼元件](configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-106">For more information about metadata design mode and code design mode, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md).</span></span>

## <a name="writing-the-script-in-code-design-mode"></a><span data-ttu-id="e305e-107">在程式碼設計模式中撰寫指令碼</span><span class="sxs-lookup"><span data-stu-id="e305e-107">Writing the Script in Code Design Mode</span></span>

### <a name="script-component-development-environment"></a><span data-ttu-id="e305e-108">指令碼元件開發環境</span><span class="sxs-lookup"><span data-stu-id="e305e-108">Script Component Development Environment</span></span>
 <span data-ttu-id="e305e-109">若要撰寫指令碼，請在 [指令碼轉換編輯器]  的 [指令碼]  頁面上按一下 [編輯指令碼]  以開啟 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE。</span><span class="sxs-lookup"><span data-stu-id="e305e-109">To write your script, click **Edit Script** on the **Script** page of the **Script Transformation Editor** to open the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE.</span></span> <span data-ttu-id="e305e-110">VSTA IDE 包含 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET 環境的所有標準功能，例如色彩編碼的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 編輯器、IntelliSense 和物件瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="e305e-110">The VSTA IDE includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span>

 <span data-ttu-id="e305e-111">指令碼是以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 撰寫。</span><span class="sxs-lookup"><span data-stu-id="e305e-111">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="e305e-112">您可以在 [指令碼轉換編輯器] 中，藉由設定 **ScriptLanguage** 屬性來指定指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="e305e-112">You specify the script language by setting the **ScriptLanguage** property in the **Script Transformation Editor**.</span></span> <span data-ttu-id="e305e-113">如果想要使用其他的程式語言，可以用您所選的語言開發自訂組件，然後在指令碼元件中，從程式碼呼叫其功能。</span><span class="sxs-lookup"><span data-stu-id="e305e-113">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script component.</span></span>

 <span data-ttu-id="e305e-114">您在指令碼元件中建立的指令碼會儲存在封裝定義中，</span><span class="sxs-lookup"><span data-stu-id="e305e-114">The script that you create in the Script component is stored in the package definition.</span></span> <span data-ttu-id="e305e-115">而沒有個別的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="e305e-115">There is no separate script file.</span></span> <span data-ttu-id="e305e-116">因此，使用指令碼元件並不會影響封裝部署。</span><span class="sxs-lookup"><span data-stu-id="e305e-116">Therefore, the use of the Script component does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="e305e-117">在您設計封裝時，指令碼會暫時寫入專案檔。</span><span class="sxs-lookup"><span data-stu-id="e305e-117">While you design the package, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="e305e-118">因為將敏感性資訊儲存在檔案中會造成潛在的安全性風險，所以我們建議您不要在指令碼中包含密碼之類的敏感性資訊。</span><span class="sxs-lookup"><span data-stu-id="e305e-118">Because storing sensitive information in a file is a potential security risk, we recommended that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="e305e-119">依預設，在 IDE 中會停用 `Option Strict`。</span><span class="sxs-lookup"><span data-stu-id="e305e-119">By default, `Option Strict` is disabled in the IDE.</span></span>

### <a name="script-component-project-structure"></a><span data-ttu-id="e305e-120">指令碼元件專案結構</span><span class="sxs-lookup"><span data-stu-id="e305e-120">Script Component Project Structure</span></span>
 <span data-ttu-id="e305e-121">指令碼元件的優點在於可以產生基礎結構程式碼，所以能夠減少所必須撰寫的程式碼量。</span><span class="sxs-lookup"><span data-stu-id="e305e-121">The power of the Script component is that it can generate infrastructure code that reduces the amount of code that you must write.</span></span> <span data-ttu-id="e305e-122">這項功能的前提是，輸入和輸出及其資料行和屬性都是固定的，而且已預先知道。</span><span class="sxs-lookup"><span data-stu-id="e305e-122">This feature relies on the fact that inputs and outputs and their columns and properties are fixed and known in advance.</span></span> <span data-ttu-id="e305e-123">因此，對元件中繼資料所進行的任何後續變更，都可能會造成已撰寫的程式碼無效。</span><span class="sxs-lookup"><span data-stu-id="e305e-123">Therefore, any subsequent changes that you make to the component's metadata may invalidate the code that you have written.</span></span> <span data-ttu-id="e305e-124">這會在封裝執行期間造成編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="e305e-124">This causes compilation errors during execution of the package.</span></span>

#### <a name="project-items-and-classes-in-the-script-component-project"></a><span data-ttu-id="e305e-125">指令碼元件專案中的專案項目和類別</span><span class="sxs-lookup"><span data-stu-id="e305e-125">Project Items and Classes in the Script Component Project</span></span>
 <span data-ttu-id="e305e-126">當您切換到程式碼設計模式時，VSTA IDE 就會開啟並顯示 `ScriptMain` 專案項目。</span><span class="sxs-lookup"><span data-stu-id="e305e-126">When you switch to code design mode, the VSTA IDE opens and displays the `ScriptMain` project item.</span></span> <span data-ttu-id="e305e-127">`ScriptMain` 專案項目包含可編輯的 `ScriptMain` 類別，這可充當指令碼的進入點，也就是撰寫程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="e305e-127">The `ScriptMain` project item contains the editable `ScriptMain` class, which serves as the entry point for the script and which is where you write your code.</span></span> <span data-ttu-id="e305e-128">類別中的程式碼項目會根據您針對指令碼工作所選取的程式語言而變更。</span><span class="sxs-lookup"><span data-stu-id="e305e-128">The code elements in the class vary depending on the programming language that you selected for the Script task.</span></span>

 <span data-ttu-id="e305e-129">指令碼專案包含兩個額外的、自動產生的唯讀專案項目：</span><span class="sxs-lookup"><span data-stu-id="e305e-129">The script project contains two additional auto-generated read-only project items:</span></span>

-   <span data-ttu-id="e305e-130">`ComponentWrapper` 專案項目包含三個類別：</span><span class="sxs-lookup"><span data-stu-id="e305e-130">The `ComponentWrapper` project item contains three classes:</span></span>

    -   <span data-ttu-id="e305e-131">`UserComponent` 類別，這個類別繼承自 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>，且包含用於處理資料並與封裝互動的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="e305e-131">The `UserComponent` class, which inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> and contains the methods and properties that you will use to process data and to interact with the package.</span></span> <span data-ttu-id="e305e-132">`ScriptMain` 類別繼承自 `UserComponent` 類別。</span><span class="sxs-lookup"><span data-stu-id="e305e-132">The `ScriptMain` class inherits from the `UserComponent` class.</span></span>

    -   <span data-ttu-id="e305e-133">`Connections` 集合類別，這個類別包含 [指令碼轉換編輯器] 的 [連接管理員] 頁面上所選取連接的參考。</span><span class="sxs-lookup"><span data-stu-id="e305e-133">A `Connections` collection class that contains references to the connections selected on the Connection Manager page of the Script Transformation Editor.</span></span>

    -   <span data-ttu-id="e305e-134">`Variables`集合類別，其中包含在 [ `ReadOnlyVariable` `ReadWriteVariables` **腳本轉換編輯器**] 的 [**腳本**] 頁面上，和屬性中所輸入之變數的參考。</span><span class="sxs-lookup"><span data-stu-id="e305e-134">A `Variables` collection class that contains references to the variables entered in the `ReadOnlyVariable` and `ReadWriteVariables` properties on the **Script** page of the **Script Transformation Editor**.</span></span>

-   <span data-ttu-id="e305e-135">`BufferWrapper`專案專案所包含的類別，會 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 針對 [**腳本轉換編輯器**] 的 [**輸入和輸出**] 頁面上所設定的每個輸入和輸出，繼承自。</span><span class="sxs-lookup"><span data-stu-id="e305e-135">The `BufferWrapper` project item contains a class that inherits from <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> for each input and output configured on the **Inputs and Outputs** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="e305e-136">這其中每個類別所包含的類型存取子屬性，都與設定的輸入和輸出資料行以及包含這些資料行的資料流緩衝區相對應。</span><span class="sxs-lookup"><span data-stu-id="e305e-136">Each of these classes contains typed accessor properties that correspond to the configured input and output columns, and the data flow buffers that contain the columns.</span></span>

 <span data-ttu-id="e305e-137">如需如何使用這些物件、方法和屬性的資訊，請參閱[了解指令碼元件物件模型](understanding-the-script-component-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-137">For information about how to use these objects, methods, and properties, see [Understanding the Script Component Object Model](understanding-the-script-component-object-model.md).</span></span> <span data-ttu-id="e305e-138">如需如何在特定的指令碼元件類型中使用這些類別的方法和屬性的資訊，請參閱[其他指令碼元件範例](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-138">For information about how to use the methods and properties of these classes in a particular type of Script component, see the section [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span> <span data-ttu-id="e305e-139">範例主題也包含完整的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="e305e-139">The example topics also contain complete code samples.</span></span>

 <span data-ttu-id="e305e-140">當您將指令碼元件設定為轉換時，`ScriptMain` 專案項目會包含下列自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e305e-140">When you configure the Script component as a transformation, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="e305e-141">程式碼範本也會提供指令碼元件的概觀，以及有關如何擷取與操作 SSIS 物件 (例如變數、事件與連接) 的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e305e-141">The code template also provides an overview of the Script component, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Component
' Write scripts using Microsoft Visual Basic 2008.
' ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper

<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _
<CLSCompliant(False)> _
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub PreExecute()
        MyBase.PreExecute()
        '
        ' Add your code here for preprocessing or remove if not needed
        '
    End Sub

    Public Overrides Sub PostExecute()
        MyBase.PostExecute()
        '
        ' Add your code here for postprocessing or remove if not needed
        ' You can set read/write variables here, for example:
        ' Me.Variables.MyIntVar = 100
        '
    End Sub

    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)
        '
        ' Add your code here
        '
    End Sub

End Class
```

```csharp
/* Microsoft SQL Server Integration Services user script component
*  Write scripts using Microsoft Visual C# 2008.
*  ScriptMain is the entry point class of the script.*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime.Wrapper;

[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]
public class ScriptMain : UserComponent
{

    public override void PreExecute()
    {
        base.PreExecute();
        /*
          Add your code here for preprocessing or remove if not needed
        */
    }

    public override void PostExecute()
    {
        base.PostExecute();
        /*
          Add your code here for postprocessing or remove if not needed
          You can set read/write variables here, for example:
          Variables.MyIntVar = 100
        */
    }

    public override void Input0_ProcessInputRow(Input0Buffer Row)
    {
        /*
          Add your code here
        */
    }

}
```

#### <a name="additional-project-items-in-the-script-component-project"></a><span data-ttu-id="e305e-142">指令碼元件專案中的其他專案項目</span><span class="sxs-lookup"><span data-stu-id="e305e-142">Additional Project Items in the Script Component Project</span></span>
 <span data-ttu-id="e305e-143">指令碼元件專案可以包含預設 `ScriptMain` 項目以外的項目。</span><span class="sxs-lookup"><span data-stu-id="e305e-143">The Script component project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="e305e-144">您可以在專案中加入類別、模組、程式碼檔案和資料夾，也可以使用資料夾來整理項目群組。</span><span class="sxs-lookup"><span data-stu-id="e305e-144">You can add classes, modules, code files, and folders to the project, and you can use folders to organize groups of items.</span></span>

 <span data-ttu-id="e305e-145">所有您加入的項目都會保存在封裝內。</span><span class="sxs-lookup"><span data-stu-id="e305e-145">All the items that you add are persisted inside the package.</span></span>

#### <a name="references-in-the-script-component-project"></a><span data-ttu-id="e305e-146">指令碼元件專案中的參考</span><span class="sxs-lookup"><span data-stu-id="e305e-146">References in the Script Component Project</span></span>
 <span data-ttu-id="e305e-147">您可以在 [專案總管]  中以滑鼠右鍵按一下「指令碼」工作專案，再按 [新增參考]  ，新增 Managed 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e305e-147">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="e305e-148">如需詳細資訊，請參閱[參考指令碼解決方案中的其他組件](../referencing-other-assemblies-in-scripting-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-148">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="e305e-149">您可以在 VSTA IDE 中的 [類別檢視]  或 [專案總管]  中，檢視專案參考。</span><span class="sxs-lookup"><span data-stu-id="e305e-149">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="e305e-150">您可以從 [檢視]  功能表中開啟任一個視窗。</span><span class="sxs-lookup"><span data-stu-id="e305e-150">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="e305e-151">您可以從 [專案]  功能表、[專案總管]  或 [類別檢視]  新增參考。</span><span class="sxs-lookup"><span data-stu-id="e305e-151">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-component"></a><span data-ttu-id="e305e-152">與指令碼元件中的封裝互動</span><span class="sxs-lookup"><span data-stu-id="e305e-152">Interacting with the Package in the Script Component</span></span>
 <span data-ttu-id="e305e-153">在指令碼元件中撰寫的自訂指令碼可以在自動產生的基底類別中，透過強型別 (Strongly-Typed) 的存取子從包含的封裝存取及使用變數和連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e305e-153">The custom script that you write in the Script component can access and use variables and connection managers from the containing package through strongly-typed accessors in the auto-generated base classes.</span></span> <span data-ttu-id="e305e-154">不過，如果想要在指令碼中使用變數和連接管理員，則必須先設定變數和連接管理員，才能進入程式碼設計模式。</span><span class="sxs-lookup"><span data-stu-id="e305e-154">However, you must configure both variables and connection managers before entering code-design mode if you want to make them available to your script.</span></span> <span data-ttu-id="e305e-155">您也可以從指令碼元件程式碼引發事件和執行記錄。</span><span class="sxs-lookup"><span data-stu-id="e305e-155">You can also raise events and perform logging from your Script component code.</span></span>

 <span data-ttu-id="e305e-156">指令碼元件專案中自動產生的專案項目會提供下列物件、方法和屬性，可用於與封裝互動。</span><span class="sxs-lookup"><span data-stu-id="e305e-156">The autogenerated project items in the Script component project provide the following objects, methods, and properties for interacting with the package.</span></span>

|<span data-ttu-id="e305e-157">封裝功能</span><span class="sxs-lookup"><span data-stu-id="e305e-157">Package Feature</span></span>|<span data-ttu-id="e305e-158">存取方法</span><span class="sxs-lookup"><span data-stu-id="e305e-158">Access Method</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="e305e-159">變數</span><span class="sxs-lookup"><span data-stu-id="e305e-159">Variables</span></span>|<span data-ttu-id="e305e-160">使用 `Variables` 專案項目的 `ComponentWrapper` 集合類別中的具名和類型存取子屬性，這些屬性是透過 `Variables` 類別的 `ScriptMain` 屬性而公開。</span><span class="sxs-lookup"><span data-stu-id="e305e-160">Use the named and typed accessor properties in the `Variables` collection class in the `ComponentWrapper` project item, exposed through the `Variables` property of the `ScriptMain` class.</span></span><br /><br /> <span data-ttu-id="e305e-161">`PreExecute` 方法只能存取唯讀變數。</span><span class="sxs-lookup"><span data-stu-id="e305e-161">The `PreExecute` method can access only read-only variables.</span></span> <span data-ttu-id="e305e-162">`PostExecute` 方法可以存取唯讀和讀/寫變數。</span><span class="sxs-lookup"><span data-stu-id="e305e-162">The `PostExecute` method can access both read-only and read/write variables.</span></span>|
|<span data-ttu-id="e305e-163">連接</span><span class="sxs-lookup"><span data-stu-id="e305e-163">Connections</span></span>|<span data-ttu-id="e305e-164">使用 `Connections` 專案項目的 `ComponentWrapper` 集合類別中的具名和類型存取子屬性，這些屬性是透過 `Connections` 類別的 `ScriptMain` 屬性而公開。</span><span class="sxs-lookup"><span data-stu-id="e305e-164">Use the named and typed accessor properties in the `Connections` collection class in the `ComponentWrapper` project item, exposed through the `Connections` property of the `ScriptMain` class.</span></span>|
|<span data-ttu-id="e305e-165">事件</span><span class="sxs-lookup"><span data-stu-id="e305e-165">Events</span></span>|<span data-ttu-id="e305e-166">使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> 類別的屬性 `ScriptMain` 和介面的\*\*引發 \<X> \*\*方法，引發事件 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 。</span><span class="sxs-lookup"><span data-stu-id="e305e-166">Raise events by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class and the **Fire\<X>** methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.</span></span>|
|<span data-ttu-id="e305e-167">記錄</span><span class="sxs-lookup"><span data-stu-id="e305e-167">Logging</span></span>|<span data-ttu-id="e305e-168">使用 `ScriptMain` 類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> 方法來執行記錄。</span><span class="sxs-lookup"><span data-stu-id="e305e-168">Perform logging by using the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method of the `ScriptMain` class.</span></span>|

## <a name="debugging-the-script-component"></a><span data-ttu-id="e305e-169">偵錯指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e305e-169">Debugging the Script Component</span></span>
 <span data-ttu-id="e305e-170">若要偵錯指令碼元件中的程式碼，請在程式碼中設定至少一個中斷點，然後關閉 VSTA IDE，以便在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="e305e-170">To debug the code in your Script component, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e305e-171">當封裝執行進入指令碼元件時，VSTA IDE 會在唯讀模式下重新開啟並顯示您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e305e-171">When package execution enters the Script component, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="e305e-172">在執行到達中斷點之後，您可以檢查變數值並逐步完成其餘的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e305e-172">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!NOTE]
>  <span data-ttu-id="e305e-173">當您在執行封裝工作的子封裝內執行指令碼元件時，將無法偵錯指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="e305e-173">You cannot debug a Script component when you run the Script component as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="e305e-174">在這些情況下，系統會略過您在子封裝的指令碼元件中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="e305e-174">Breakpoints that you set in the Script component in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="e305e-175">您可以分開執行子封裝，以利正常地偵錯子封裝。</span><span class="sxs-lookup"><span data-stu-id="e305e-175">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="e305e-176">當您偵錯包含多個指令碼元件的封裝時，偵錯工具會偵錯其中一個指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="e305e-176">When you debug a package that contains multiple Script components, the debugger debugs one Script component.</span></span> <span data-ttu-id="e305e-177">如果偵錯工具完成，系統就可以偵錯另一個指令碼元件，如同 Foreach 迴圈或 For 迴圈容器的情況。</span><span class="sxs-lookup"><span data-stu-id="e305e-177">The system can debug another Script component if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

 <span data-ttu-id="e305e-178">您也可以使用下列方法來監視指令碼元件的執行：</span><span class="sxs-lookup"><span data-stu-id="e305e-178">You can also monitor the execution of the Script component by using the following methods:</span></span>

-   <span data-ttu-id="e305e-179">使用 `MessageBox.Show` **system.web**命名空間中的方法中斷執行，並顯示強制回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e305e-179">Interrupt execution and display a modal message by using the `MessageBox.Show` method in the **System.Windows.Forms** namespace.</span></span> <span data-ttu-id="e305e-180">(請在完成偵錯程序之後移除此程式碼)。</span><span class="sxs-lookup"><span data-stu-id="e305e-180">(Remove this code after you complete the debugging process.)</span></span>

-   <span data-ttu-id="e305e-181">引發資訊訊息、警告和錯誤的事件。</span><span class="sxs-lookup"><span data-stu-id="e305e-181">Raise events for informational messages, warnings, and errors.</span></span> <span data-ttu-id="e305e-182">FireInformation、FireWarning 和 FireError 方法會在 Visual Studio [輸出]  視窗中顯示事件描述。</span><span class="sxs-lookup"><span data-stu-id="e305e-182">The FireInformation, FireWarning, and FireError methods display the event description in the Visual Studio **Output** window.</span></span> <span data-ttu-id="e305e-183">不過，FireProgress 方法、Console.Write 方法和 Console.WriteLine 方法不會在 [輸出]  視窗中顯示任何資訊。</span><span class="sxs-lookup"><span data-stu-id="e305e-183">However, the FireProgress method, the Console.Write method, and Console.WriteLine method do not display any information in the **Output** window.</span></span> <span data-ttu-id="e305e-184">FireProgress 事件的訊息會顯示在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師的 [進度] 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="e305e-184">Messages from the FireProgress event appear on the **Progress** tab of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="e305e-185">如需詳細資訊，請參閱[在指令碼元件中引發事件](../../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-185">For more information, see [Raising Events in the Script Component](../../data-flow/transformations/script-component.md).</span></span>

-   <span data-ttu-id="e305e-186">將事件或使用者定義的訊息記錄到啟用的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="e305e-186">Log events or user-defined messages to enabled logging providers.</span></span> <span data-ttu-id="e305e-187">如需詳細資訊，請參閱[在指令碼元件中記錄](logging-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-187">For more information, see [Logging in the Script Component](logging-in-the-script-component.md).</span></span>

 <span data-ttu-id="e305e-188">如果只需要檢查設定為來源或轉換的指令碼元件的輸出，而不將資料儲存到目的地，可以使用[資料列計數轉換](../../data-flow/transformations/row-count-transformation.md)停止資料流程，並將資料檢視器附加到指令碼元件的輸出。</span><span class="sxs-lookup"><span data-stu-id="e305e-188">If you just want to examine the output of a Script component configured as a source or as a transformation, without saving the data to a destination, you can stop the data flow with a [Row Count Transformation](../../data-flow/transformations/row-count-transformation.md) and attach a data viewer to the output of the Script component.</span></span> <span data-ttu-id="e305e-189">如需資料檢視器的資訊，請參閱[偵錯資料流程](../../troubleshooting/debugging-data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="e305e-189">For information about data viewers, see [Debugging Data Flow](../../troubleshooting/debugging-data-flow.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e305e-190">本節內容</span><span class="sxs-lookup"><span data-stu-id="e305e-190">In This Section</span></span>
 <span data-ttu-id="e305e-191">如需有關撰寫指令碼元件程式碼的詳細資訊，請參閱此章節中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="e305e-191">For more information about coding the Script component, see the following topics in this section.</span></span>

 <span data-ttu-id="e305e-192">[瞭解腳本元件物件模型](understanding-the-script-component-object-model.md)說明如何使用腳本元件中可用的物件、方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="e305e-192">[Understanding the Script Component Object Model](understanding-the-script-component-object-model.md) Explains how to use the objects, methods, and properties available in the Script component.</span></span>

 <span data-ttu-id="e305e-193">[參考腳本解決方案中的其他元件](../referencing-other-assemblies-in-scripting-solutions.md)說明如何從 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 腳本元件中的類別庫參考物件。</span><span class="sxs-lookup"><span data-stu-id="e305e-193">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) Explains how to reference objects from the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library in the Script component.</span></span>

 <span data-ttu-id="e305e-194">[模擬腳本元件的錯誤輸出](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)說明如何針對在腳本元件處理期間引發錯誤的資料列，模擬錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e305e-194">[Simulating an Error Output for the Script Component](../../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md) Explains how to simulate an error output for rows that raise errors during processing by the Script component.</span></span>

## <a name="external-resources"></a><span data-ttu-id="e305e-195">外部資源</span><span class="sxs-lookup"><span data-stu-id="e305e-195">External Resources</span></span>

-   <span data-ttu-id="e305e-196">blogs.msdn.com 上的部落格文章：[VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661) (SSIS 2008 和 R2 安裝的 VSTA 安裝與設定問題)。</span><span class="sxs-lookup"><span data-stu-id="e305e-196">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="e305e-197">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="e305e-197">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e305e-198">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="e305e-198">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e305e-199">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="e305e-199">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e305e-200">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="e305e-200">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e305e-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e305e-201">See Also</span></span>
 [<span data-ttu-id="e305e-202">在指令碼元件編輯器中設定指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e305e-202">Configuring the Script Component in the Script Component Editor</span></span>](configuring-the-script-component-in-the-script-component-editor.md)


