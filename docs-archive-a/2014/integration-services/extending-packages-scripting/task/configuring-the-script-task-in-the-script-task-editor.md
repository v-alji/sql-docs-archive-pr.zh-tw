---
title: 在指令碼工作編輯器設定指令碼工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75b4a030e6c5baa2e26c610b0e8216843c8cca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593450"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a><span data-ttu-id="bc848-102">在指令碼工作編輯器設定指令碼工作</span><span class="sxs-lookup"><span data-stu-id="bc848-102">Configuring the Script Task in the Script Task Editor</span></span>
  <span data-ttu-id="bc848-103">在指令碼工作內撰寫自訂程式碼之前，必須先在 [指令碼工作編輯器]  的三個頁面中設定其主要屬性。</span><span class="sxs-lookup"><span data-stu-id="bc848-103">Before you write custom code in the Script task, you configure its principal properties in the three pages of the **Script Task Editor**.</span></span> <span data-ttu-id="bc848-104">您可以使用 [屬性] 視窗，設定其他非指令碼工作專用的工作屬性。</span><span class="sxs-lookup"><span data-stu-id="bc848-104">You can configure additional task properties that are not unique to the Script task by using the Properties window.</span></span>

> [!NOTE]
>  <span data-ttu-id="bc848-105">不同於在舊版中可以指出是否已編譯了指令碼，所有指令碼在 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 中皆會先進行編譯。</span><span class="sxs-lookup"><span data-stu-id="bc848-105">Unlike earlier versions where you could indicate whether scripts were precompiled, all scripts are precompiled beginning in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].</span></span>

## <a name="general-page-of-the-script-task-editor"></a><span data-ttu-id="bc848-106">指令碼工作編輯器的一般頁面</span><span class="sxs-lookup"><span data-stu-id="bc848-106">General Page of the Script Task Editor</span></span>
 <span data-ttu-id="bc848-107">在 [指令碼工作編輯器] 的 [一般] 頁面上，為指令碼工作指派唯一的名稱與描述。</span><span class="sxs-lookup"><span data-stu-id="bc848-107">On the **General** page of the **Script Task Editor**, you assign a unique name and a description for the Script task.</span></span>

## <a name="script-page-of-the-script-task-editor"></a><span data-ttu-id="bc848-108">指令碼工作編輯器的指令碼頁面</span><span class="sxs-lookup"><span data-stu-id="bc848-108">Script Page of the Script Task Editor</span></span>
 <span data-ttu-id="bc848-109">[指令碼工作編輯器] 的 [指令碼] 頁面會顯示指令碼工作的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="bc848-109">The **Script** page of the **Script Task Editor** displays the custom properties of the Script task.</span></span>

### <a name="scriptlanguage-property"></a><span data-ttu-id="bc848-110">ScriptLanguage 屬性</span><span class="sxs-lookup"><span data-stu-id="bc848-110">ScriptLanguage Property</span></span>
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="bc848-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 支援 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="bc848-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# programming languages.</span></span> <span data-ttu-id="bc848-112">當您在指令碼工作內建立指令碼之後，就無法變更 **ScriptLanguage** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bc848-112">After you create a script in the Script task, you cannot change value of the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="bc848-113">若要為指令碼工作和指令碼元件設定預設指令碼語言，請使用 [選項] 對話方塊之 [一般] 頁面上的 **ScriptLanguage** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bc848-113">To set the default script language for Script tasks and Script components, use the **ScriptLanguage** property on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="bc848-114">如需相關資訊，請參閱 [General Page](../../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="bc848-114">For more information, see [General Page](../../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="entrypoint-property"></a><span data-ttu-id="bc848-115">EntryPoint 屬性</span><span class="sxs-lookup"><span data-stu-id="bc848-115">EntryPoint Property</span></span>
 <span data-ttu-id="bc848-116">`EntryPoint` 屬性會將 VSTA 專案中 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段所呼叫的 `ScriptMain` 類別方法指定為指令碼工作程式碼的進入點。</span><span class="sxs-lookup"><span data-stu-id="bc848-116">The `EntryPoint` property specifies the method on the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="bc848-117">`ScriptMain`類別是腳本範本所產生的預設類別。</span><span class="sxs-lookup"><span data-stu-id="bc848-117">The `ScriptMain` class is the default class generated by the script templates.</span></span>

 <span data-ttu-id="bc848-118">如果您在 VSTA 專案內變更此方法的名稱，您就必須變更 `EntryPoint` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bc848-118">If you change the name of the method in the VSTA project, you must change the value of the `EntryPoint` property.</span></span>

### <a name="readonlyvariables-and-readwritevariables-properties"></a><span data-ttu-id="bc848-119">ReadOnlyVariables 與 ReadWriteVariables 屬性</span><span class="sxs-lookup"><span data-stu-id="bc848-119">ReadOnlyVariables and ReadWriteVariables Properties</span></span>
 <span data-ttu-id="bc848-120">您可以輸入現有變數的逗號分隔清單做為這些屬性的值，使得變數可在指令碼工作程式碼中以唯讀或讀取/寫入的方式來存取。</span><span class="sxs-lookup"><span data-stu-id="bc848-120">You can enter comma-delimited lists of existing variables as the values of these properties to make the variables available for read-only or read/write access within the Script task code.</span></span> <span data-ttu-id="bc848-121">您可以透過 `Dts` 物件的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 屬性在程式碼中存取這兩種類型的變數。</span><span class="sxs-lookup"><span data-stu-id="bc848-121">Variables of both types are accessed in code through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="bc848-122">如需詳細資訊，請參閱 [在指令碼工作中使用變數](../../extending-packages-scripting/task/using-variables-in-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bc848-122">For more information, see [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="bc848-123">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bc848-123">Variable names are case-sensitive.</span></span>

 <span data-ttu-id="bc848-124">若要選取變數，請按一下屬性欄位旁邊的省略符號 ([...]  ) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bc848-124">To select the variables, click the ellipsis (**...**) button next to the property field.</span></span> <span data-ttu-id="bc848-125">如需詳細資訊，請參閱[選取變數頁面](../../control-flow/select-variables-page.md)。</span><span class="sxs-lookup"><span data-stu-id="bc848-125">For more information, see [Select Variables Page](../../control-flow/select-variables-page.md).</span></span>

### <a name="edit-script-button"></a><span data-ttu-id="bc848-126">編輯指令碼按鈕</span><span class="sxs-lookup"><span data-stu-id="bc848-126">Edit Script Button</span></span>
 <span data-ttu-id="bc848-127">[編輯指令碼]  按鈕會啟動您用來撰寫自訂指令碼的 VSTA 開發環境。</span><span class="sxs-lookup"><span data-stu-id="bc848-127">The **Edit Script** button launches the VSTA development environment in which you write your custom script.</span></span> <span data-ttu-id="bc848-128">如需詳細資訊，請參閱[指令碼工作的程式碼撰寫和偵錯](coding-and-debugging-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="bc848-128">For more information, see [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md).</span></span>

## <a name="expressions-page-of-the-script-task-editor"></a><span data-ttu-id="bc848-129">指令碼工作編輯器的運算式頁面</span><span class="sxs-lookup"><span data-stu-id="bc848-129">Expressions Page of the Script Task Editor</span></span>
 <span data-ttu-id="bc848-130">在 [指令碼工作編輯器] 的 [運算式] 頁面上，您可以使用運算式，針對上面列出之指令碼工作的屬性及許多其他工作屬性來提供值。</span><span class="sxs-lookup"><span data-stu-id="bc848-130">On the **Expressions** page of the **Script Task Editor**, you can use expressions to provide values for the properties of the Script task listed above and for many other task properties.</span></span> <span data-ttu-id="bc848-131">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)為止。</span><span class="sxs-lookup"><span data-stu-id="bc848-131">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>

<span data-ttu-id="bc848-132">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="bc848-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bc848-133">若要取得 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的最新下載、文件、範例和影片以及社群中的選定方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="bc848-133">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bc848-134">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="bc848-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bc848-135">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="bc848-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc848-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc848-136">See Also</span></span>
 [<span data-ttu-id="bc848-137">指令碼工作的程式碼撰寫和偵錯</span><span class="sxs-lookup"><span data-stu-id="bc848-137">Coding and Debugging the Script Task</span></span>](coding-and-debugging-the-script-task.md)


