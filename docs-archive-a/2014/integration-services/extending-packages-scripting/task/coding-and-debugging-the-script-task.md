---
title: 編碼和偵錯指令碼工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], debugging
- SSIS Script task, development environment
- SSIS Script task, debugging
- Script task [Integration Services], development environment
- Script task [Integration Services], coding
- debugging [Integration Services], scripts
- VSTA
- SSIS Script task, coding
ms.assetid: 687c262f-fcab-42e8-92ae-e956f3d92d69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f4383469368ac1fe3c70ff82f8c8bb2cf755838
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687053"
---
# <a name="coding-and-debugging-the-script-task"></a><span data-ttu-id="3ac8f-102">指令碼工作的程式碼撰寫和偵錯</span><span class="sxs-lookup"><span data-stu-id="3ac8f-102">Coding and Debugging the Script Task</span></span>
  <span data-ttu-id="3ac8f-103">在 [指令碼工作編輯器]  中設定指令碼工作之後，於指令碼工作開發環境中撰寫自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-103">After configuring the Script task in the **Script Task Editor**, you write your custom code in the Script task development environment.</span></span>

## <a name="script-task-development-environment"></a><span data-ttu-id="3ac8f-104">指令碼工作開發環境</span><span class="sxs-lookup"><span data-stu-id="3ac8f-104">Script Task Development Environment</span></span>
 <span data-ttu-id="3ac8f-105">指令碼工作使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 作為指令碼本身的開發環境。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-105">The Script task uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the development environment for the script itself.</span></span>

 <span data-ttu-id="3ac8f-106">指令碼是以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 撰寫。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-106">Script code is written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span> <span data-ttu-id="3ac8f-107">您可以在 [指令碼工作編輯器] 中設定 [ScriptLanguage] 屬性來指定指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-107">You specify the script language by setting the **ScriptLanguage** property in the **Script Task Editor**.</span></span> <span data-ttu-id="3ac8f-108">如果想要使用其他的程式語言，可以用您所選的語言開發自訂組件，然後在指令碼工作中，從程式碼呼叫其功能。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-108">If you prefer to use another programming language, you can develop a custom assembly in your language of choice and call its functionality from the code in the Script task.</span></span>

 <span data-ttu-id="3ac8f-109">您在指令碼工作中建立的指令碼會儲存在封裝定義中，</span><span class="sxs-lookup"><span data-stu-id="3ac8f-109">The script that you create in the Script task is stored in the package definition.</span></span> <span data-ttu-id="3ac8f-110">而沒有個別的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-110">There is no separate script file.</span></span> <span data-ttu-id="3ac8f-111">因此，使用指令碼工作並不會影響封裝部署。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-111">Therefore, the use of the Script task does not affect package deployment.</span></span>

> [!NOTE]
>  <span data-ttu-id="3ac8f-112">當您設計封裝和偵錯指令碼時，指令碼會暫時寫入專案檔案。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-112">When you design the package and debug the script, the script code is temporarily written to a project file.</span></span> <span data-ttu-id="3ac8f-113">因為將敏感資訊儲存在檔案中會造成潛在的安全性風險，所以我們建議您不要在指令碼中包含密碼之類的敏感資訊。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-113">Because storing sensitive information in a file is a potential security risk, we recommend that you do not include sensitive information such as passwords in the script code.</span></span>

 <span data-ttu-id="3ac8f-114">依預設，在 IDE 中會停用 `Option Strict`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-114">By default, `Option Strict` is disabled in the IDE.</span></span>

## <a name="script-task-project-structure"></a><span data-ttu-id="3ac8f-115">指令碼工作專案結構</span><span class="sxs-lookup"><span data-stu-id="3ac8f-115">Script Task Project Structure</span></span>
 <span data-ttu-id="3ac8f-116">當您建立或修改包含在指令碼工作中的指令碼時，VSTA 會開啟空的新專案或是重新開啟現有的專案。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-116">When you create or modify the script that is contained in a Script task, VSTA opens an empty new project or reopens the existing project.</span></span> <span data-ttu-id="3ac8f-117">這個 VSTA 專案的建立不會影響專案的部署，因為專案是儲存在封裝檔案中；指令碼工作不會建立其他檔案。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-117">The creation of this VSTA project does not affect the deployment of the package, because the project is saved inside the package file; the Script task does not create additional files.</span></span>

### <a name="project-items-and-classes-in-the-script-task-project"></a><span data-ttu-id="3ac8f-118">指令碼工作專案中的專案項目和類別</span><span class="sxs-lookup"><span data-stu-id="3ac8f-118">Project Items and Classes in the Script Task Project</span></span>
 <span data-ttu-id="3ac8f-119">依預設，顯示在 VSTA [專案總管] 視窗中的指令碼工作專案包含單一項目：`ScriptMain`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-119">By default, the Script task project displayed in the VSTA Project Explorer window contains a single item, `ScriptMain`.</span></span> <span data-ttu-id="3ac8f-120">`ScriptMain` 項目則包含單一類別，同樣名為 `ScriptMain`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-120">The `ScriptMain` item, in turn, contains a single class, also named `ScriptMain`.</span></span> <span data-ttu-id="3ac8f-121">類別中的程式碼項目會根據您針對指令碼工作所選取的程式語言而變更。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-121">The code elements in the class vary depending on the programming language that you selected for the Script task:</span></span>

-   <span data-ttu-id="3ac8f-122">針對程式設計語言設定腳本工作時， [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] `ScriptMain` 類別具有公用副程式 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-122">When the Script task is configured for the [!INCLUDE[vb_orcas_long](../../../includes/vb-orcas-long-md.md)] programming language, the `ScriptMain` class has a public subroutine, `Main`.</span></span> <span data-ttu-id="3ac8f-123">`ScriptMain.Main` 副程式是當您執行指令碼工作時，執行階段呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-123">The `ScriptMain.Main` subroutine is the method that the runtime calls when you run your Script task.</span></span>

     <span data-ttu-id="3ac8f-124">依預設，在新指令碼的 `Main` 副程式中的唯一程式碼是 `Dts.TaskResult = ScriptResults.Success` 這一行。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-124">By default, the only code in the `Main` subroutine of a new script is the line `Dts.TaskResult = ScriptResults.Success`.</span></span> <span data-ttu-id="3ac8f-125">這行會通知執行階段，工作的作業已成功。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-125">This line informs the runtime that the task was successful in its operation.</span></span> <span data-ttu-id="3ac8f-126">`Dts.TaskResult`[從腳本工作傳回結果](../../extending-packages-scripting/task/returning-results-from-the-script-task.md)中會討論屬性。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-126">The `Dts.TaskResult` property is discussed in [Returning Results from the Script Task](../../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>

-   <span data-ttu-id="3ac8f-127">當為 Visual C# 程式語言設定指令碼工作時，`ScriptMain` 類別具有公用的方法 `Main`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-127">When the Script task is configured for the Visual C# programming language, the `ScriptMain` class has a public method, `Main`.</span></span> <span data-ttu-id="3ac8f-128">此方法是在指令碼工作執行時呼叫。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-128">The method is called when the Script task runs.</span></span>

     <span data-ttu-id="3ac8f-129">依預設，`Main` 方法包括此行：`Dts.TaskResult = (int)ScriptResults.Success`。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-129">By default, the `Main` method includes the line `Dts.TaskResult = (int)ScriptResults.Success`.</span></span> <span data-ttu-id="3ac8f-130">這行會通知執行階段，工作的作業已成功。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-130">This line informs the runtime that the task was successful in its operation.</span></span>

 <span data-ttu-id="3ac8f-131">`ScriptMain` 項目可以包含 `ScriptMain` 類別以外的類別。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-131">The `ScriptMain` item can contain classes other than the `ScriptMain` class.</span></span> <span data-ttu-id="3ac8f-132">類別僅可供其所在的指令碼工作使用。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-132">Classes are available only to the Script task in which they reside.</span></span>

 <span data-ttu-id="3ac8f-133">依預設，`ScriptMain` 專案項目包含下列自動產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-133">By default, the `ScriptMain` project item contains the following autogenerated code.</span></span> <span data-ttu-id="3ac8f-134">程式碼範本也會提供指令碼工作的概觀，以及有關如何擷取與操作 SSIS 物件 (例如變數、事件與連接) 的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-134">The code template also provides an overview of the Script task, and additional information on how to retrieve and manipulate SSIS objects, such as variables, events, and connections.</span></span>

```vb
' Microsoft SQL Server Integration Services Script Task
' Write scripts using Microsoft Visual Basic 2008.
' The ScriptMain is the entry point class of the script.

Imports System
Imports System.Data
Imports System.Math
Imports Microsoft.SqlServer.Dts.Runtime.VSTAProxy

<System.AddIn.AddIn("ScriptMain", Version:="1.0", Publisher:="", Description:="")> _
Partial Class ScriptMain

Private Sub ScriptMain_Startup(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Startup

End Sub

Private Sub ScriptMain_Shutdown(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Shutdown
Try
' Unlock variables from the read-only and read-write variable collection properties
If (Dts.Variables.Count <> 0) Then
Dts.Variables.Unlock()
End If
Catch ex As Exception
        End Try
End Sub

Enum ScriptResults
Success = DTSExecResult.Success
Failure = DTSExecResult.Failure
End Enum

' The execution engine calls this method when the task executes.
' To access the object model, use the Dts property. Connections, variables, events,
' and logging features are available as members of the Dts property as shown in the following examples.
'
' To reference a variable, call Dts.Variables("MyCaseSensitiveVariableName").Value
' To post a log entry, call Dts.Log("This is my log text", 999, Nothing)
' To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, True)
'
' To use the connections collection use something like the following:
' ConnectionManager cm = Dts.Connections.Add("OLEDB")
' cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;"
'
' Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.
' 
' To open Help, press F1.

Public Sub Main()
'
' Add your code here
'
Dts.TaskResult = ScriptResults.Success
End Sub

End Class
```

```csharp
/*
   Microsoft SQL Server Integration Services Script Task
   Write scripts using Microsoft Visual C# 2008.
   The ScriptMain is the entry point class of the script.
*/

using System;
using System.Data;
using Microsoft.SqlServer.Dts.Runtime.VSTAProxy;
using System.Windows.Forms;

namespace ST_1bcfdbad36d94f8ba9f23a10375abe53.csproj
{
    [System.AddIn.AddIn("ScriptMain", Version = "1.0", Publisher = "", Description = "")]
    public partial class ScriptMain
    {
        private void ScriptMain_Startup(object sender, EventArgs e)
        {

        }

        private void ScriptMain_Shutdown(object sender, EventArgs e)
        {
            try
            {
                // Unlock variables from the read-only and read-write variable collection properties
                if (Dts.Variables.Count != 0)
                {
                    Dts.Variables.Unlock();
                }
            }
            catch
            {
            }
        }

        #region VSTA generated code
        private void InternalStartup()
        {
            this.Startup += new System.EventHandler(ScriptMain_Startup);
            this.Shutdown += new System.EventHandler(ScriptMain_Shutdown);
        }
        enum ScriptResults
        {
            Success = DTSExecResult.Success,
            Failure = DTSExecResult.Failure
        };

        #endregion

        /*
The execution engine calls this method when the task executes.
To access the object model, use the Dts property. Connections, variables, events,
and logging features are available as members of the Dts property as shown in the following examples.

To reference a variable, call Dts.Variables["MyCaseSensitiveVariableName"].Value;
To post a log entry, call Dts.Log("This is my log text", 999, null);
To fire an event, call Dts.Events.FireInformation(99, "test", "hit the help message", "", 0, true);

To use the connections collection use something like the following:
ConnectionManager cm = Dts.Connections.Add("OLEDB");
cm.ConnectionString = "Data Source=localhost;Initial Catalog=AdventureWorks;Provider=SQLNCLI10;Integrated Security=SSPI;Auto Translate=False;";

Before returning from this method, set the value of Dts.TaskResult to indicate success or failure.

To open Help, press F1.
*/

        public void Main()
        {
            // TODO: Add your code here
            Dts.TaskResult = (int)ScriptResults.Success;
        }
    }
```

### <a name="additional-project-items-in-the-script-task-project"></a><span data-ttu-id="3ac8f-135">指令碼工作專案中的其他專案項目</span><span class="sxs-lookup"><span data-stu-id="3ac8f-135">Additional Project Items in the Script Task Project</span></span>
 <span data-ttu-id="3ac8f-136">指令碼工作專案可以包含預設 `ScriptMain` 項目以外的項目。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-136">The Script task project can include items other than the default `ScriptMain` item.</span></span> <span data-ttu-id="3ac8f-137">您可以將類別、模組和程式碼檔案加入專案。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-137">You can add classes, modules, and code files to the project.</span></span> <span data-ttu-id="3ac8f-138">您也可以使用資料夾來組織項目的群組。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-138">You can also use folders to organize groups of items.</span></span> <span data-ttu-id="3ac8f-139">所有您加入的項目都會保存在封裝內。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-139">All the items that you add are persisted inside the package.</span></span>

### <a name="references-in-the-script-task-project"></a><span data-ttu-id="3ac8f-140">指令碼工作專案中的參考</span><span class="sxs-lookup"><span data-stu-id="3ac8f-140">References in the Script Task Project</span></span>
 <span data-ttu-id="3ac8f-141">您可以在 [專案總管]  中以滑鼠右鍵按一下「指令碼」工作專案，再按 [新增參考]  ，新增 Managed 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-141">You can add references to managed assemblies by right-clicking the Script task project in **Project Explorer**, and then clicking **Add Reference**.</span></span> <span data-ttu-id="3ac8f-142">如需詳細資訊，請參閱[參考指令碼解決方案中的其他組件](../referencing-other-assemblies-in-scripting-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-142">For more information, see [Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="3ac8f-143">您可以在 VSTA IDE 中的 [類別檢視]  或 [專案總管]  中，檢視專案參考。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-143">You can view project references in the VSTA IDE in **Class View** or in **Project Explorer**.</span></span> <span data-ttu-id="3ac8f-144">您可以從 [檢視]  功能表中開啟任一個視窗。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-144">You open either of these windows from the **View** menu.</span></span> <span data-ttu-id="3ac8f-145">您可以從 [專案]  功能表、[專案總管]  或 [類別檢視]  新增參考。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-145">You can add a new reference from the **Project** menu, from **Project Explorer**, or from **Class View**.</span></span>

## <a name="interacting-with-the-package-in-the-script-task"></a><span data-ttu-id="3ac8f-146">與指令碼工作中的封裝互動</span><span class="sxs-lookup"><span data-stu-id="3ac8f-146">Interacting with the Package in the Script Task</span></span>
 <span data-ttu-id="3ac8f-147">指令碼工作使用全域 `Dts` 物件 (<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 類別的執行個體) 及其成員與包含封裝和 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段互動。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-147">The Script task uses the global `Dts` object, which is an instance of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, and its members to interact with the containing package and with the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime.</span></span>

 <span data-ttu-id="3ac8f-148">下表列出 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 類別的主要公用成員，這個類別是透過全域 `Dts` 物件向指令碼工作程式碼公開。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-148">The following table lists the principal public members of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class, which is exposed to Script task code through the global `Dts` object.</span></span> <span data-ttu-id="3ac8f-149">本節中的主題會更詳細地討論這些成員的使用。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-149">The topics in this section discuss the use of these members in more detail.</span></span>

|<span data-ttu-id="3ac8f-150">member</span><span class="sxs-lookup"><span data-stu-id="3ac8f-150">Member</span></span>|<span data-ttu-id="3ac8f-151">目的</span><span class="sxs-lookup"><span data-stu-id="3ac8f-151">Purpose</span></span>|
|------------|-------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>|<span data-ttu-id="3ac8f-152">提供定義在封裝中的連接管理員之存取權。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-152">Provides access to connection managers defined in the package.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>|<span data-ttu-id="3ac8f-153">提供事件介面，讓指令碼工作引發錯誤、警告及參考訊息。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-153">Provides an events interface to let the Script task raise errors, warnings, and informational messages.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>|<span data-ttu-id="3ac8f-154">提供簡單的方法將 `TaskResult` 以外的單一物件傳回執行階段，也可用於工作流程分支。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-154">Provides a simple way to return a single object to the runtime (in addition to the `TaskResult`) that can also be used for workflow branching.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>|<span data-ttu-id="3ac8f-155">將工作進度與結果等資訊記錄到啟用的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-155">Logs information such as task progress and results to enabled log providers.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A>|<span data-ttu-id="3ac8f-156">報告工作的成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-156">Reports the success or failure of the task.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Transaction%2A>|<span data-ttu-id="3ac8f-157">提供工作的容器執行範圍內的交易 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-157">Provides the transaction, if any, within which the task's container is running.</span></span>|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>|<span data-ttu-id="3ac8f-158">提供列在 `ReadOnlyVariables` 與 `ReadWriteVariables` 工作屬性中的變數存取權，以供在指令碼中使用。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-158">Provides access to the variables listed in the `ReadOnlyVariables` and `ReadWriteVariables` task properties for use within the script.</span></span>|

 <span data-ttu-id="3ac8f-159"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> 類別也包含一些您可能不會使用的公用成員。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-159">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> class also contains some public members that you will probably not use.</span></span>

|<span data-ttu-id="3ac8f-160">member</span><span class="sxs-lookup"><span data-stu-id="3ac8f-160">Member</span></span>|<span data-ttu-id="3ac8f-161">描述</span><span class="sxs-lookup"><span data-stu-id="3ac8f-161">Description</span></span>|
|------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>|<span data-ttu-id="3ac8f-162"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性會提供更為便利的變數存取方式。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-162">The <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property provides more convenient access to variables.</span></span> <span data-ttu-id="3ac8f-163">雖然您可以使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>，但是必須明確地呼叫方法以鎖定和解除鎖定要讀取和寫入的變數。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-163">Although you can use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must explicitly call methods to lock and unlock variables for reading and writing.</span></span> <span data-ttu-id="3ac8f-164">當您使用 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性時，指令碼工作會為您處理鎖定語意。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-164">The Script task handles locking semantics for you when you use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property.</span></span>|

## <a name="debugging-the-script-task"></a><span data-ttu-id="3ac8f-165">偵錯指令碼工作</span><span class="sxs-lookup"><span data-stu-id="3ac8f-165">Debugging the Script Task</span></span>
 <span data-ttu-id="3ac8f-166">若要偵錯指令碼工作中的程式碼，請在程式碼中設定至少一個中斷點，然後關閉 VSTA IDE 以便在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-166">To debug the code in your Script task, set at least one breakpoint in the code, and then close the VSTA IDE to run the package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="3ac8f-167">當封裝執行進入指令碼工作時，VSTA IDE 會在唯讀模式下重新開啟和顯示您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-167">When package execution enters the Script task, the VSTA IDE reopens and displays your code in read-only mode.</span></span> <span data-ttu-id="3ac8f-168">在執行到達中斷點之後，您可以檢查變數值並逐步完成其餘的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-168">After execution reaches your breakpoint, you can examine variable values and step through the remaining code.</span></span>

> [!WARNING]
>  <span data-ttu-id="3ac8f-169">您可以在以 64 位元模式執行封裝時，為指令碼工作偵錯。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-169">You can debug the Script task when you run the package in 64-bit mode.</span></span>

> [!NOTE]
>  <span data-ttu-id="3ac8f-170">您必須執行封裝以進入指令碼工作中偵錯。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-170">You must execute the package to debug into your Script task.</span></span> <span data-ttu-id="3ac8f-171">如果您只執行個別的工作，則會忽略指令碼工作程式碼內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-171">If you execute only the individual task, breakpoints in the Script task code are ignored.</span></span>

> [!NOTE]
>  <span data-ttu-id="3ac8f-172">當您在「執行封裝工作」的子封裝內執行指令碼工作時，將無法偵錯指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-172">You cannot debug a Script task when you run the Script task as part of a child package that is run from an Execute Package task.</span></span> <span data-ttu-id="3ac8f-173">在這些情況下，會略過您在子封裝的指令碼工作中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-173">Breakpoints that you set in the Script task in the child package are disregarded in these circumstances.</span></span> <span data-ttu-id="3ac8f-174">您可以分開執行子封裝，以利正常地偵錯子封裝。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-174">You can debug the child package normally by running it separately.</span></span>

> [!NOTE]
>  <span data-ttu-id="3ac8f-175">當您偵錯包含多個指令碼工作的封裝時，偵錯工具會偵錯其中一個指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-175">When you debug a package that contains multiple Script tasks, the debugger debugs one Script task.</span></span> <span data-ttu-id="3ac8f-176">如果偵錯工具完成，系統就可以偵錯另一個指令碼工作，如同 Foreach 迴圈或 For 迴圈容器的情況。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-176">The system can debug another Script task if the debugger completes, as in the case of a Foreach Loop or For Loop container.</span></span>

## <a name="external-resources"></a><span data-ttu-id="3ac8f-177">外部資源</span><span class="sxs-lookup"><span data-stu-id="3ac8f-177">External Resources</span></span>

-   <span data-ttu-id="3ac8f-178">blogs.msdn.com 上的部落格文章：[VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661) (SSIS 2008 和 R2 安裝的 VSTA 安裝與設定問題)。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-178">Blog entry, [VSTA setup and configuration troubles for SSIS 2008 and R2 installations](https://go.microsoft.com/fwlink/?LinkId=215661), on blogs.msdn.com.</span></span>

<span data-ttu-id="3ac8f-179">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="3ac8f-179">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3ac8f-180">若要取得 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的最新下載、文件、範例和影片以及社群中的選定方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="3ac8f-180">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3ac8f-181">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="3ac8f-181">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3ac8f-182">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="3ac8f-182">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ac8f-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ac8f-183">See Also</span></span>
 <span data-ttu-id="3ac8f-184">[參考腳本解決方案中的其他元件在](../referencing-other-assemblies-in-scripting-solutions.md)[腳本工作編輯器中設定腳本工作](configuring-the-script-task-in-the-script-task-editor.md)</span><span class="sxs-lookup"><span data-stu-id="3ac8f-184">[Referencing Other Assemblies in Scripting Solutions](../referencing-other-assemblies-in-scripting-solutions.md) [Configuring the Script Task in the Script Task Editor](configuring-the-script-task-in-the-script-task-editor.md)</span></span>


