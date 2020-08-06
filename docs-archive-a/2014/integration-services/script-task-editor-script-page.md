---
title: 腳本工作編輯器 (腳本頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4eec491cc689d7d5c616e0819075e1ee5159d4e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687043"
---
# <a name="script-task-editor-script-page"></a><span data-ttu-id="e8ad2-102">指令碼工作編輯器 (指令碼頁面)</span><span class="sxs-lookup"><span data-stu-id="e8ad2-102">Script Task Editor (Script Page)</span></span>
  <span data-ttu-id="e8ad2-103">使用 **[指令碼工作編輯器]** 對話方塊的 **[指令碼]** 頁面，即可設定指令碼屬性以及指定指令碼可存取的變數。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-103">Use the **Script** page of the **Script Task Editor** dialog box to set script properties and specify variables that can be accessed by the script.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8ad2-104">在 [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] 和更新的版本中，所有指令碼都是先行編譯。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-104">In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] and later versions, all scripts are precompiled.</span></span> <span data-ttu-id="e8ad2-105">在舊版中，您會設定 **[PrecompileScriptIntoBinaryCode]** 屬性來指定指令碼已先行編譯。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-105">In earlier versions, you set a **PrecompileScriptIntoBinaryCode** property to specify that the script was precompiled.</span></span>  
  
 <span data-ttu-id="e8ad2-106">若要深入了解指令碼工作，請參閱＜ [Script Task](control-flow/script-task.md) ＞和＜ [在指令碼工作編輯器設定指令碼工作](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-106">To learn more about the Script task, see [Script Task](control-flow/script-task.md) and [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md).</span></span> <span data-ttu-id="e8ad2-107">若要了解如何以程式設計方式編寫指令碼工作，請參閱＜ [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-107">To learn about programming the Script task, see [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e8ad2-108">選項</span><span class="sxs-lookup"><span data-stu-id="e8ad2-108">Options</span></span>  
 <span data-ttu-id="e8ad2-109">**ScriptLanguage**</span><span class="sxs-lookup"><span data-stu-id="e8ad2-109">**ScriptLanguage**</span></span>  
 <span data-ttu-id="e8ad2-110">為此工作選取指令碼語言，可以是 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-110">Select the scripting language for the task, either [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="e8ad2-111">當您為此工作建立指令碼之後，就無法變更 **[ScriptLanguage]** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-111">After you have created a script for the task, you cannot change the value of the **ScriptLanguage** property.</span></span>  
  
 <span data-ttu-id="e8ad2-112">若要為指令碼工作設定預設指令碼語言，請使用 **[選項]** 對話方塊上 **[一般]** 頁面上的 **[指令碼語言]** 選項。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-112">To set the default scripting language for the Script task, use the **Scripting language** option on **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="e8ad2-113">如需相關資訊，請參閱 [General Page](general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-113">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>  
  
 <span data-ttu-id="e8ad2-114">**EntryPoint**</span><span class="sxs-lookup"><span data-stu-id="e8ad2-114">**EntryPoint**</span></span>  
 <span data-ttu-id="e8ad2-115">將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 執行階段呼叫的方法指定為指令碼工作程式碼的進入點。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-115">Specify the method that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime calls as the entry point into the code of the Script task.</span></span> <span data-ttu-id="e8ad2-116">指定的方法必須位於 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 應用程式之 TOOLS (VSTA) 專案的 ScriptMain 類別中。 ScriptMain 類別是腳本範本所產生的預設類別。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-116">The specified method must be in the ScriptMain class of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) project The ScriptMain class is the default class generated by the script templates.</span></span>  
  
 <span data-ttu-id="e8ad2-117">如果您在 VSTA 專案內變更此方法的名稱，您就必須變更 **[EntryPoint]** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-117">If you change the name of the method in the VSTA project, you must change the value of the **EntryPoint** property.</span></span>  
  
 <span data-ttu-id="e8ad2-118">**ReadOnlyVariables**</span><span class="sxs-lookup"><span data-stu-id="e8ad2-118">**ReadOnlyVariables**</span></span>  
 <span data-ttu-id="e8ad2-119">鍵入以逗號分隔且指令碼可以使用的唯讀變數清單，或是按一下省略符號 (**...**) 按鈕，並在 [選取變數]\*\*\*\* 對話方塊中選取變數。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-119">Type a comma-separated list of read-only variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8ad2-120">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-120">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="e8ad2-121">**ReadWriteVariables**</span><span class="sxs-lookup"><span data-stu-id="e8ad2-121">**ReadWriteVariables**</span></span>  
 <span data-ttu-id="e8ad2-122">鍵入以逗號分隔且指令碼可以使用的可讀寫變數清單，或是按一下省略符號 (**...**) 按鈕，並在 [選取變數]\*\*\*\* 對話方塊中選取變數。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-122">Type a comma-separated list of read/write variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8ad2-123">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-123">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="e8ad2-124">**編輯指令碼**</span><span class="sxs-lookup"><span data-stu-id="e8ad2-124">**Edit Script**</span></span>  
 <span data-ttu-id="e8ad2-125">開啟 VSTA IDE，您可在此建立或修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="e8ad2-125">Opens the VSTA IDE where you can create or modify the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ad2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8ad2-126">See Also</span></span>  
 <span data-ttu-id="e8ad2-127">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e8ad2-128">[一般頁面](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-128">[General Page](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="e8ad2-129">[[腳本工作編輯器] &#40;一般頁面&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-129">[Script Task Editor &#40;General Page&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="e8ad2-130">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-130">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="e8ad2-131">[腳本工作範例](extending-packages-scripting-task-examples/script-task-examples.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-131">[Script Task Examples](extending-packages-scripting-task-examples/script-task-examples.md) </span></span>  
 <span data-ttu-id="e8ad2-132">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e8ad2-132">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="e8ad2-133">加入、刪除、變更封裝中使用者定義變數的範圍</span><span class="sxs-lookup"><span data-stu-id="e8ad2-133">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
