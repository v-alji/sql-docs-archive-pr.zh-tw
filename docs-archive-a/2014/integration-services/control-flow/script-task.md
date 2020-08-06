---
title: 指令碼工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584677"
---
# <a name="script-task"></a><span data-ttu-id="15a69-102">指令碼工作</span><span class="sxs-lookup"><span data-stu-id="15a69-102">Script Task</span></span>
  <span data-ttu-id="15a69-103">指令碼工作提供程式碼，用來執行無法在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的內建工作和轉換中使用的函式。</span><span class="sxs-lookup"><span data-stu-id="15a69-103">The Script task provides code to perform functions that are not available in the built-in tasks and transformations that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="15a69-104">指令碼工作亦可在一個指令碼中結合函數，而不使用多項工作和轉換。</span><span class="sxs-lookup"><span data-stu-id="15a69-104">The Script task can also combine functions in one script instead of using multiple tasks and transformations.</span></span> <span data-ttu-id="15a69-105">您可以使用指令碼工作處理必須在封裝中執行一次 (或是每個列舉物件一次) 的工作，而非每個資料列執行一次的工作。</span><span class="sxs-lookup"><span data-stu-id="15a69-105">You use the Script task for work that must be done once in a package (or once per enumerated object), instead than once per data row.</span></span>  
  
 <span data-ttu-id="15a69-106">您可將指令碼工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="15a69-106">You can use the Script task for the following purposes:</span></span>  
  
-   <span data-ttu-id="15a69-107">使用其他不受內建連接類型支援的技術存取資料。</span><span class="sxs-lookup"><span data-stu-id="15a69-107">Access data by using other technologies that are not supported by built-in connection types.</span></span> <span data-ttu-id="15a69-108">例如，指令碼可使用「Active Directory 服務介面」(ADSI) 存取並擷取 Active Directory 中的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="15a69-108">For example, a script can use Active Directory Service Interfaces (ADSI) to access and extract user names from Active Directory.</span></span>  
  
-   <span data-ttu-id="15a69-109">建立封裝專屬的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="15a69-109">Create a package-specific performance counter.</span></span> <span data-ttu-id="15a69-110">例如，指令碼可建立效能計數器，並於複雜或效能不佳的工作執行時進行更新。</span><span class="sxs-lookup"><span data-stu-id="15a69-110">For example, a script can create a performance counter that is updated while a complex or poorly performing task runs.</span></span>  
  
-   <span data-ttu-id="15a69-111">識別指定的檔案是否空白或其中包含多少資料列，然後根據這項資訊，判斷其是否會影響封裝中的控制流程。</span><span class="sxs-lookup"><span data-stu-id="15a69-111">Identify whether specified files are empty or how many rows they contain, and then based on that information affect the control flow in a package.</span></span> <span data-ttu-id="15a69-112">例如，如果檔案包含零個資料列，變數值便會設為 0，而評估該值的優先順序條件約束則會讓「檔案系統」工作無法複製檔案。</span><span class="sxs-lookup"><span data-stu-id="15a69-112">For example, if a file contains zero rows, the value of a variable set to 0, and a precedence constraint that evaluates the value prevents a File System task from copying the file.</span></span>  
  
 <span data-ttu-id="15a69-113">如果您必須使用指令碼在集合的每一列資料上執行相同的工作，您應該使用指令碼元件，而非指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="15a69-113">If you have to use the script to do the same work for each row of data in a set, you should use the Script component instead of the Script task.</span></span> <span data-ttu-id="15a69-114">例如，如果要評估合理的郵資金額，並略過金額過高或過低的資料列，請使用「指令碼」元件。</span><span class="sxs-lookup"><span data-stu-id="15a69-114">For example, if you want to assess the reasonableness of a postage amount and skip data rows that have very high or low amounts, you would use a Script component.</span></span> <span data-ttu-id="15a69-115">如需詳細資訊，請參閱 [指令碼元件](../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="15a69-115">For more information, see [Script Component](../data-flow/transformations/script-component.md).</span></span>  
  
 <span data-ttu-id="15a69-116">如果有多個封裝使用指令碼，請考慮撰寫自訂工作，而不要使用指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="15a69-116">If more than one package uses a script, consider writing a custom task instead of using the Script task.</span></span> <span data-ttu-id="15a69-117">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="15a69-117">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
 <span data-ttu-id="15a69-118">確定指令碼工作是適用於您封裝的選擇之後，您必須同時開發該工作使用的指令碼，以及設定工作本身。</span><span class="sxs-lookup"><span data-stu-id="15a69-118">After you decide that the Script task is the appropriate choice for your package, you have to both develop the script that the task uses and configure the task itself.</span></span>  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a><span data-ttu-id="15a69-119">撰寫並執行工作使用的指令碼</span><span class="sxs-lookup"><span data-stu-id="15a69-119">Writing and Running the Script that the Task Uses</span></span>  
 <span data-ttu-id="15a69-120">指令碼工作使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 作為撰寫指令碼的環境，以及執行這些指令碼的引擎。</span><span class="sxs-lookup"><span data-stu-id="15a69-120">The Script task uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts and the engine that runs those scripts.</span></span>  
  
 <span data-ttu-id="15a69-121">VSTA 提供 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 環境的所有標準功能，例如色彩編碼的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 編輯器、IntelliSense 和 [物件總管]  。</span><span class="sxs-lookup"><span data-stu-id="15a69-121">VSTA provides all the standard features of the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor, IntelliSense, and **Object Explorer**.</span></span> <span data-ttu-id="15a69-122">VSTA 也使用其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 開發工作使用的相同偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="15a69-122">VSTA also uses the same debugger that other [!INCLUDE[msCoName](../../includes/msconame-md.md)] development tools use.</span></span> <span data-ttu-id="15a69-123">指令碼中的中斷點能與 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 工作和容器上的中斷點合作無間。</span><span class="sxs-lookup"><span data-stu-id="15a69-123">Breakpoints in the script work seamlessly with breakpoints on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and containers.</span></span> <span data-ttu-id="15a69-124">VSTA 支援 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 程式語言。</span><span class="sxs-lookup"><span data-stu-id="15a69-124">VSTA supports both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages.</span></span>  
  
 <span data-ttu-id="15a69-125">若要執行指令碼，必須在封裝執行的電腦上安裝 VSTA。</span><span class="sxs-lookup"><span data-stu-id="15a69-125">To run a script, you must have VSTA installed on the computer where the package runs.</span></span> <span data-ttu-id="15a69-126">當封裝執行時，工作會載入指令碼引擎並執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="15a69-126">When the package runs, the task loads the script engine and runs the script.</span></span> <span data-ttu-id="15a69-127">您可以在專案中將參考加入至組件，藉此在指令碼中存取外部 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="15a69-127">You can access external .NET assemblies in scripts by adding references to the assemblies in the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15a69-128">不像在舊版中可以指出是否已經先行編譯指令碼，所有指令碼在 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 和更新的版本中都會先行編譯。</span><span class="sxs-lookup"><span data-stu-id="15a69-128">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="15a69-129">指令碼經過先行編譯後，在執行階段不會載入語言引擎，因此封裝的執行速度會更快。</span><span class="sxs-lookup"><span data-stu-id="15a69-129">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="15a69-130">不過，先行編譯的二進位檔案會使用大量的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="15a69-130">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-task"></a><span data-ttu-id="15a69-131">設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="15a69-131">Configuring the Script Task</span></span>  
 <span data-ttu-id="15a69-132">您可以利用下列方式設定指令碼工作：</span><span class="sxs-lookup"><span data-stu-id="15a69-132">You can configure the Script task in the following ways:</span></span>  
  
-   <span data-ttu-id="15a69-133">提供工作執行的自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="15a69-133">Provide the custom script that the task runs.</span></span>  
  
-   <span data-ttu-id="15a69-134">在 VSTA 專案中，將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行階段呼叫的方法指定為指令碼工作程式碼的進入點。</span><span class="sxs-lookup"><span data-stu-id="15a69-134">Specify the method in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span>  
  
-   <span data-ttu-id="15a69-135">指定指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="15a69-135">Specify the script language.</span></span>  
  
-   <span data-ttu-id="15a69-136">選擇性地提供於指令碼中使用的唯讀和讀/寫變數清單。</span><span class="sxs-lookup"><span data-stu-id="15a69-136">Optionally, provide lists of read-only and read/write variables for use in the script.</span></span>  
  
 <span data-ttu-id="15a69-137">您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計的方式來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="15a69-137">You can set these properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-task-in-the-designer"></a><span data-ttu-id="15a69-138">在設計師中設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="15a69-138">Configuring the Script Task in the Designer</span></span>  
 <span data-ttu-id="15a69-139">下表描述可以為指令碼工作記錄的 `ScriptTaskLogEntry` 事件。</span><span class="sxs-lookup"><span data-stu-id="15a69-139">The following table describes the `ScriptTaskLogEntry` event that can be logged for Script task.</span></span> <span data-ttu-id="15a69-140">在 `ScriptTaskLogEntry` [**設定 SSIS 記錄**] 對話方塊的 [**詳細資料**] 索引標籤上，已選取要記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="15a69-140">The `ScriptTaskLogEntry` event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box.</span></span> <span data-ttu-id="15a69-141">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="15a69-141">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="15a69-142">記錄項目</span><span class="sxs-lookup"><span data-stu-id="15a69-142">Log entry</span></span>|<span data-ttu-id="15a69-143">描述</span><span class="sxs-lookup"><span data-stu-id="15a69-143">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="15a69-144">報告在指令碼內實作記錄的結果。</span><span class="sxs-lookup"><span data-stu-id="15a69-144">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="15a69-145">每次呼叫 `Log` 物件的 `Dts` 方法時，工作都會寫入記錄項目。</span><span class="sxs-lookup"><span data-stu-id="15a69-145">The task writes a log entry for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="15a69-146">工作會在程式碼執行時撰寫這些項目。</span><span class="sxs-lookup"><span data-stu-id="15a69-146">The task writes these entries when the code is run.</span></span> <span data-ttu-id="15a69-147">如需詳細資訊，請參閱 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="15a69-147">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
 <span data-ttu-id="15a69-148">如需有關可在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="15a69-148">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="15a69-149">指令碼工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="15a69-149">Script Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="15a69-150">指令碼工作編輯器 &#40;指令碼頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="15a69-150">Script Task Editor &#40;Script Page&#41;</span></span>](../script-task-editor-script-page.md)  
  
-   [<span data-ttu-id="15a69-151">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="15a69-151">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="15a69-152">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="15a69-152">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="15a69-153">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="15a69-153">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a><span data-ttu-id="15a69-154">以程式設計的方式設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="15a69-154">Configuring the Script Task Programmatically</span></span>  
 <span data-ttu-id="15a69-155">如需有關以程式設計方式設定這些屬性的詳細資訊，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="15a69-155">For more information about programmatically setting these properties, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a><span data-ttu-id="15a69-156">相關內容</span><span class="sxs-lookup"><span data-stu-id="15a69-156">Related Content</span></span>  
  
-   <span data-ttu-id="15a69-157">shareourideas.com 上的技術文件： [如何在 C# 中傳送包含傳遞通知的電子郵件](https://go.microsoft.com/fwlink/?LinkId=237625)(如何在 C# 中傳送包含傳遞通知的電子郵件)</span><span class="sxs-lookup"><span data-stu-id="15a69-157">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
  
