---
title: 使用指令碼元件建立同步轉換 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- synchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: aa1bee1a-ab06-44d8-9944-4bff03d73016
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34252f1caba4e2c1b3b99788d32527a33793b6ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596776"
---
# <a name="creating-a-synchronous-transformation-with-the-script-component"></a><span data-ttu-id="21797-102">使用指令碼元件建立同步轉換</span><span class="sxs-lookup"><span data-stu-id="21797-102">Creating a Synchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="21797-103">您在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的資料流程中使用轉換元件，以修改及分析從來源傳遞到目的地的資料。</span><span class="sxs-lookup"><span data-stu-id="21797-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="21797-104">具有同步輸出的轉換會處理通過該元件的每個輸入資料列。</span><span class="sxs-lookup"><span data-stu-id="21797-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="21797-105">具有非同步輸出的轉換會等到它收到所有的輸入資料列後，才完成其處理。</span><span class="sxs-lookup"><span data-stu-id="21797-105">A transformation with asynchronous outputs waits until it has received all input rows to complete its processing.</span></span> <span data-ttu-id="21797-106">本主題討論同步轉換。</span><span class="sxs-lookup"><span data-stu-id="21797-106">This topic discusses a synchronous transformation.</span></span> <span data-ttu-id="21797-107">如需非同步轉換的資訊，請參閱[使用指令碼元件建立非同步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-107">For information about asynchronous transformations, see [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).</span></span> <span data-ttu-id="21797-108">如需同步與非同步元件之間差異的詳細資訊，請參閱[了解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-108">For more information about the difference between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="21797-109">如需指令碼元件的概觀，請參閱[使用指令碼元件擴充資料流程](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="21797-110">指令碼元件以及它為您產生的基礎結構程式碼，可大幅簡化開發自訂資料流程元件的程序。</span><span class="sxs-lookup"><span data-stu-id="21797-110">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="21797-111">不過，若要了解指令碼元件運作方式，閱讀[開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)的一節中有關開發自訂資料流程元件所必須遵循的步驟，尤其是[開發具有同步輸出的自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)，可能會非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="21797-111">However, to understand how the Script component works, you may find it useful to read the steps that you must follow in developing a custom data flow component in the section on [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-a-synchronous-transformation-component"></a><span data-ttu-id="21797-112">開始使用同步轉換元件</span><span class="sxs-lookup"><span data-stu-id="21797-112">Getting Started with a Synchronous Transformation Component</span></span>
 <span data-ttu-id="21797-113">當您將指令碼元件新增至 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具的 [資料流程] 窗格時，就會開啟 [選取指令碼元件類型]  對話方塊，並提示您選取 [來源]、[目的地] 或是 [轉換] 元件類型。</span><span class="sxs-lookup"><span data-stu-id="21797-113">When you add a Script component to the Data Flow pane of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a Source, Destination, or Transformation component type.</span></span> <span data-ttu-id="21797-114">在這個對話方塊中，選取 [轉換]  。</span><span class="sxs-lookup"><span data-stu-id="21797-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-a-synchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="21797-115">在中繼資料設計模式中設定同步轉換元件</span><span class="sxs-lookup"><span data-stu-id="21797-115">Configuring a Synchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="21797-116">在您選取可建立轉換元件的選項之後，請使用 [指令碼轉換編輯器]  來設定元件。</span><span class="sxs-lookup"><span data-stu-id="21797-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="21797-117">如需詳細資訊，請參閱[在指令碼元件編輯器中設定指令碼元件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="21797-118">若要設定指令碼元件的指令碼語言，請在 [指令碼轉換編輯器] 的 [指令碼] 頁面上設定 **ScriptLanguage** 屬性。</span><span class="sxs-lookup"><span data-stu-id="21797-118">To set the script language for the Script component, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor**.</span></span>

> [!NOTE]
>  <span data-ttu-id="21797-119">若要為指令碼元件設定預設的指令碼語言，請使用 [選項] 對話方塊中 [一般] 頁面上的 [指令碼語言] 選項。</span><span class="sxs-lookup"><span data-stu-id="21797-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="21797-120">如需相關資訊，請參閱 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="21797-121">資料流程轉換元件有一個輸入，而且支援一或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-121">A data flow transformation component has one input, and supports one or more outputs.</span></span> <span data-ttu-id="21797-122">設定元件的輸入與輸出是您必須在中繼資料設計模式下完成的其中一個步驟，方法是在撰寫自訂指令碼之前先使用 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="21797-122">Configuring the input and outputs for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="21797-123">設定輸入資料行</span><span class="sxs-lookup"><span data-stu-id="21797-123">Configuring Input Columns</span></span>
 <span data-ttu-id="21797-124">轉換元件有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="21797-124">A transformation component has one input.</span></span>

 <span data-ttu-id="21797-125">在 [指令碼轉換編輯器] 的 [輸入資料行] 頁面上，資料行清單會從資料流程中的上游元件輸出顯示可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-125">On the **Input Columns** page of the **Script Transformation Editor,** the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="21797-126">選取要轉換或通過的資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="21797-127">將任何您要就地轉換的資料行標示成「讀取/寫入」。</span><span class="sxs-lookup"><span data-stu-id="21797-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="21797-128">如需 [指令碼轉換編輯器] 的 [輸入資料行] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入資料行頁面&#41;](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="21797-129">設定輸入、輸出及輸出資料行</span><span class="sxs-lookup"><span data-stu-id="21797-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="21797-130">轉換元件支援一或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="21797-131">在 [指令碼轉換編輯器] 的 [輸入及輸出] 頁面上，您可以看到已建立單一輸出，但是輸出沒有資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-131">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you can see that a single output has been created, but the output has no columns.</span></span> <span data-ttu-id="21797-132">在編輯器的此頁面上，您可能會需要或想要設定下列項目。</span><span class="sxs-lookup"><span data-stu-id="21797-132">On this page of the editor, you may need or want to configure the following items.</span></span>

-   <span data-ttu-id="21797-133">建立一或多個其他輸出，例如含有非預期值的資料列之模擬錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-133">Create one or more additional outputs, such as a simulated error output for rows that contain unexpected values.</span></span> <span data-ttu-id="21797-134">使用 [新增輸出]  和 [移除輸出]  按鈕管理同步轉換元件的輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-134">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your synchronous transformation component.</span></span> <span data-ttu-id="21797-135">所有的輸入資料列都會導向至所有可用的輸出，除非您指定想要將每個資料列重新導向至某個輸出或是另一個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-135">All input rows are directed to all available outputs unless you indicate that you intend to redirect each row to one output or the other.</span></span> <span data-ttu-id="21797-136">您為輸出上的 `ExclusionGroup` 屬性指定非零的整數值，以指出想要重新導向資料列。</span><span class="sxs-lookup"><span data-stu-id="21797-136">You indicate that you intend to redirect rows by specifying a non-zero integer value for the `ExclusionGroup` property on the outputs.</span></span> <span data-ttu-id="21797-137">在 `ExclusionGroup` 中輸入哪一個特定整數值來識別輸出並不重要，但是您必須為指定的輸出群組持續地使用相同的整數。</span><span class="sxs-lookup"><span data-stu-id="21797-137">The specific integer value entered in `ExclusionGroup` to identify the outputs is not significant, but you must use the same integer consistently for the specified group of outputs.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="21797-138">當您不想要輸出所有的資料列時，也可以使用具有單一輸出的非零 `ExclusionGroup` 屬性值。</span><span class="sxs-lookup"><span data-stu-id="21797-138">You can also use a non-zero `ExclusionGroup` property value with a single output when you do not want to output all rows.</span></span> <span data-ttu-id="21797-139">不過，在此情況下，您必須為要傳送至輸出的每個資料列，明確地呼叫 **DirectRowTo\<outputbuffer>** 方法。</span><span class="sxs-lookup"><span data-stu-id="21797-139">However, in this case,  you must explicitly call the **DirectRowTo\<outputbuffer>** method for each row that you want to send to the output.</span></span>

-   <span data-ttu-id="21797-140">指派更具描述性的名稱給輸入與輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-140">Assign a more descriptive name to the input and outputs.</span></span> <span data-ttu-id="21797-141">指令碼元件使用這些名稱來產生具類型的存取子屬性，您將使用這些屬性來參考指令碼中的輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="21797-142">保留資料行的原狀以進行同步轉換。</span><span class="sxs-lookup"><span data-stu-id="21797-142">Leave columns as is for synchronous transformations.</span></span> <span data-ttu-id="21797-143">一般而言，同步轉換不會將資料行加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="21797-143">Typically a synchronous transformation does not add columns to the data flow.</span></span> <span data-ttu-id="21797-144">資料會在緩衝區中就地修改，而緩衝區則會傳遞至資料流程中的下一個元件。</span><span class="sxs-lookup"><span data-stu-id="21797-144">Data is modified in place in the buffer, and the buffer is passed on to the next component in the data flow.</span></span> <span data-ttu-id="21797-145">如果是這樣的情況，您不必在轉換的輸出上明確地加入和設定輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-145">If this is the case, you do not have to add and configure output columns explicitly on the transformation's outputs.</span></span> <span data-ttu-id="21797-146">輸出會出現在編輯器中，但沒有任何明確定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-146">The outputs appear in the editor without any explicitly defined columns.</span></span>

-   <span data-ttu-id="21797-147">將新資料行加入資料列層級錯誤的模擬錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-147">Add new columns to simulated error outputs for row-level errors.</span></span> <span data-ttu-id="21797-148">通常在相同 `ExclusionGroup` 中的多個輸出都有相同的一組輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-148">Ordinarily multiple outputs in the same `ExclusionGroup` have the same set of output columns.</span></span> <span data-ttu-id="21797-149">然而，如果您正在建立模擬的錯誤輸出，可能會想要加入更多的資料行以包含錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="21797-149">However, if you are creating a simulated error output, you may want to add more columns to contain error information.</span></span> <span data-ttu-id="21797-150">如需資料流程引擎如何處理錯誤資料列的資訊，請參閱[使用資料流程元件中的錯誤輸出](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-150">For information about how the data flow engine processes error rows, see [Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md).</span></span> <span data-ttu-id="21797-151">不過，在指令碼元件中，您必須撰寫自已的程式碼，以適當的錯誤資訊填寫其他資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-151">Note that in the Script component you must write your own code to fill the additional columns with appropriate error information.</span></span> <span data-ttu-id="21797-152">如需詳細資訊，請參閱[模擬指令碼元件的錯誤輸出](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-152">For more information, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="21797-153">如需 [指令碼轉換編輯器] 之 [輸入及輸出] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入及輸出頁面&#41;](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-153">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="21797-154">加入變數</span><span class="sxs-lookup"><span data-stu-id="21797-154">Adding Variables</span></span>
 <span data-ttu-id="21797-155">如果您想要在腳本中使用現有的變數，您可以在 [ `ReadOnlyVariables` `ReadWriteVariables` **腳本轉換編輯器**] 的 [**腳本**] 頁面上，將它們加入和屬性欄位中。</span><span class="sxs-lookup"><span data-stu-id="21797-155">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="21797-156">當您在屬性欄位中加入多個變數時，請用逗號分隔變數名稱。</span><span class="sxs-lookup"><span data-stu-id="21797-156">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="21797-157">您也可以按一下和屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後選取 `ReadOnlyVariables` `ReadWriteVariables` [**選取變數**] 對話方塊中的變數，來選取多個變數。</span><span class="sxs-lookup"><span data-stu-id="21797-157">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="21797-158">如需如何利用指令碼元件使用變數的一般資訊，請參閱[在指令碼元件中使用變數](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-158">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="21797-159">如需 [指令碼轉換編輯器] 的 [指令碼] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;指令碼頁面&#41;](../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-159">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-synchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="21797-160">在程式碼設計模式中編寫同步轉換元件的指令碼</span><span class="sxs-lookup"><span data-stu-id="21797-160">Scripting a Synchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="21797-161">在您設定好元件的中繼資料之後，便可撰寫自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="21797-161">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="21797-162">在 [指令碼轉換編輯器]  的 [指令碼]  頁面上，按一下 [編輯指令碼]  來開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE 以新增自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="21797-162">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="21797-163">所使用的指令碼語言取決於您選取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 還是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作為 [指令碼] 頁面上 **ScriptLanguage** 屬性的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="21797-163">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="21797-164">如需使用指令碼元件所建立之各種元件都適用的重要資訊，請參閱[編碼和偵錯指令碼元件](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="21797-164">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="21797-165">了解自動產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="21797-165">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="21797-166">當您在建立和設定轉換元件之後開啟 VSTA IDE，可編輯的 `ScriptMain` 類別會出現在程式碼編輯器中，並具有 `ProcessInputRow` 方法的 Stub。</span><span class="sxs-lookup"><span data-stu-id="21797-166">When you open the VSTA IDE after you create and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="21797-167">`ScriptMain` 類別是您將撰寫自訂程式碼的地方，而 `ProcessInputRow` 則是轉換元件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="21797-167">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a transformation component.</span></span>

 <span data-ttu-id="21797-168">如果您在 VSTA 中開啟 [**專案管理器**] 視窗，您可以看到腳本元件也會產生唯讀 `BufferWrapper` 和 `ComponentWrapper` 專案專案。</span><span class="sxs-lookup"><span data-stu-id="21797-168">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="21797-169">`ScriptMain` 類別會繼承 `UserComponent` 專案項目中的 `ComponentWrapper` 類別。</span><span class="sxs-lookup"><span data-stu-id="21797-169">The `ScriptMain` class inherits from the `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="21797-170">在執行階段，資料流程引擎會叫用 `ProcessInput` 類別中的 `UserComponent` 方法，它會覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 父類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="21797-170">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="21797-171">`ProcessInput` 方法接著會在輸入緩衝區的資料列中執行迴圈，並為每個資料列呼叫一次 `ProcessInputRow` 方法。</span><span class="sxs-lookup"><span data-stu-id="21797-171">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="21797-172">撰寫您的自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="21797-172">Writing Your Custom Code</span></span>
 <span data-ttu-id="21797-173">具有同步輸出的轉換元件是所有資料流程元件中最容易撰寫的。</span><span class="sxs-lookup"><span data-stu-id="21797-173">A transformation component with synchronous outputs is the simplest of all data flow components to write.</span></span> <span data-ttu-id="21797-174">例如，在本主題稍後所顯示的單一輸出範例是由下列自訂程式碼所組成：</span><span class="sxs-lookup"><span data-stu-id="21797-174">For example, the single-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
```

```csharp
Row.City = (Row.City).ToUpper();

```

 <span data-ttu-id="21797-175">若要完成建立自訂同步轉換元件，可以使用覆寫的 `ProcessInputRow` 方法，轉換輸入緩衝區之每個資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="21797-175">To finish creating a custom synchronous transformation component, you use the overridden `ProcessInputRow` method to transform the data in each row of the input buffer.</span></span> <span data-ttu-id="21797-176">資料流程引擎會在變滿時將這個緩衝區傳遞到資料流程中的下一個元件。</span><span class="sxs-lookup"><span data-stu-id="21797-176">The data flow engine passes this buffer, when full, to the next component in the data flow.</span></span>

 <span data-ttu-id="21797-177">視您的需求而定，您也可能會想要在 `PreExecute` 與 `PostExecute` 方法 (可在 `ScriptMain` 類別中取得) 中撰寫指令碼，以執行初步或是最後的處理。</span><span class="sxs-lookup"><span data-stu-id="21797-177">Depending on your requirements, you may also want to write script in the `PreExecute` and `PostExecute` methods, available in the `ScriptMain` class, to perform preliminary or final processing.</span></span>

### <a name="working-with-multiple-outputs"></a><span data-ttu-id="21797-178">使用多個輸出</span><span class="sxs-lookup"><span data-stu-id="21797-178">Working with Multiple Outputs</span></span>
 <span data-ttu-id="21797-179">相較於之前討論的單一輸出狀況，將輸入資料列導向兩個或更多可能的輸出之一，並不需要更多的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="21797-179">Directing input rows to one of two or more possible outputs does not require much more custom code than the single-output scenario discussed earlier.</span></span> <span data-ttu-id="21797-180">例如，在本主題稍後所顯示的雙輸出範例是由下列自訂程式碼所組成：</span><span class="sxs-lookup"><span data-stu-id="21797-180">For example, the two-output example shown later in this topic consists of the following custom code:</span></span>

```vb
Row.City = UCase(Row.City)
If Row.City = "REDMOND" Then
    Row.DirectRowToMyRedmondAddresses()
Else
    Row.DirectRowToMyOtherAddresses()
End If
```

```csharp
Row.City = (Row.City).ToUpper();

if (Row.City=="REDMOND")
{
    Row.DirectRowToMyRedmondAddresses();
}
else
{
    Row.DirectRowToMyOtherAddresses();
}
```

 <span data-ttu-id="21797-181">在這個範例中，根據所設定的輸出名稱而定，指令碼元件會產生 **DirectRowTo\<OutputBufferX>** 方法。</span><span class="sxs-lookup"><span data-stu-id="21797-181">In this example, the Script component generates the **DirectRowTo\<OutputBufferX>** methods for you, based on the names of the outputs that you configured.</span></span> <span data-ttu-id="21797-182">您可以使用類似的程式碼將錯誤資料列導向模擬的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-182">You can use similar code to direct error rows to a simulated error output.</span></span>

## <a name="examples"></a><span data-ttu-id="21797-183">範例</span><span class="sxs-lookup"><span data-stu-id="21797-183">Examples</span></span>
 <span data-ttu-id="21797-184">以下範例示範在 `ScriptMain` 類別中所需的自訂程式碼，以建立同步轉換元件。</span><span class="sxs-lookup"><span data-stu-id="21797-184">The examples here demonstrate the custom code that is required in the `ScriptMain` class to create a synchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="21797-185">這些範例會使用**Person.Address** `AdventureWorks` 範例資料庫中的**intAddressID**和第四個數據行，也就是透過資料流程來傳遞第一個和第四個數據行，也就是和**Nvarchar (30) City**資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-185">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="21797-186">在本章節中的來源、轉換和目的地範例使用相同的資料。</span><span class="sxs-lookup"><span data-stu-id="21797-186">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="21797-187">每個範例都會記載其他必要條件與假設。</span><span class="sxs-lookup"><span data-stu-id="21797-187">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="single-output-synchronous-transformation-example"></a><span data-ttu-id="21797-188">單一輸出同步轉換範例</span><span class="sxs-lookup"><span data-stu-id="21797-188">Single Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="21797-189">此範例示範具有單一輸出的同步轉換元件。</span><span class="sxs-lookup"><span data-stu-id="21797-189">This example demonstrates a synchronous transformation component with a single output.</span></span> <span data-ttu-id="21797-190">此轉換會通過 **AddressID** 資料行，並將 **City** 資料行轉換為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="21797-190">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span>

 <span data-ttu-id="21797-191">如果您要執行這個範例程式碼，必須依下列方式設定封裝與元件：</span><span class="sxs-lookup"><span data-stu-id="21797-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="21797-192">將新指令碼元件加入資料流程設計師介面，並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="21797-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="21797-193">將來源的輸出或另一個轉換的輸出連接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的新轉換元件。</span><span class="sxs-lookup"><span data-stu-id="21797-193">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="21797-194">此輸出應提供範例資料庫之**Person. Address**資料表中的資料 `AdventureWorks` ，其中包含**AddressID**和**City**資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-194">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="21797-195">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="21797-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="21797-196">在 [輸入資料行]  頁面上，選取 [AddressID]  與 [City]  資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="21797-197">將 **City** 資料行標示為讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="21797-197">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="21797-198">在 [輸入及輸出]  頁面上，以更具描述性的名稱重新命名輸入與輸出；例如 **MyAddressInput** 和 **MyAddressOutput**。</span><span class="sxs-lookup"><span data-stu-id="21797-198">On the **Inputs and Outputs** page, rename the input and output with more descriptive names, such as **MyAddressInput** and **MyAddressOutput**.</span></span> <span data-ttu-id="21797-199">請注意，輸出的 `SynchronousInputID` 會對應至輸入的 `ID`。</span><span class="sxs-lookup"><span data-stu-id="21797-199">Notice that the `SynchronousInputID` of the output corresponds to the `ID` of the input.</span></span> <span data-ttu-id="21797-200">因此，您不必加入和設定輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-200">Therefore you do not have to add and configure output columns.</span></span>

5.  <span data-ttu-id="21797-201">在 [指令碼]  頁面上，按一下 [編輯指令碼]  ，並輸入以下指令碼。</span><span class="sxs-lookup"><span data-stu-id="21797-201">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="21797-202">然後關閉指令碼開發環境以及 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="21797-202">Then close the script development environment and the **Script Transformation Editor**.</span></span>

6.  <span data-ttu-id="21797-203">建立和設定需要 **AddressID** 和 **City** 資料行的目的地元件 (例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地)，或是在[使用指令碼元件建立目的地](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中所示範的範例目的地元件。</span><span class="sxs-lookup"><span data-stu-id="21797-203">Create and configure a destination component that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="21797-204">然後將轉換的輸出連接到目的地元件。</span><span class="sxs-lookup"><span data-stu-id="21797-204">Then connect the output of the transformation to the destination component.</span></span> <span data-ttu-id="21797-205">您可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料庫中執行下列 `AdventureWorks` 命令，以建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="21797-205">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

7.  <span data-ttu-id="21797-206">執行範例。</span><span class="sxs-lookup"><span data-stu-id="21797-206">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

    }

}
```

### <a name="two-output-synchronous-transformation-example"></a><span data-ttu-id="21797-207">雙輸出同步轉換範例</span><span class="sxs-lookup"><span data-stu-id="21797-207">Two-Output Synchronous Transformation Example</span></span>
 <span data-ttu-id="21797-208">此範例示範的同步轉換元件具有兩個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-208">This example demonstrates a synchronous transformation component with two outputs.</span></span> <span data-ttu-id="21797-209">此轉換會通過 **AddressID** 資料行，並將 **City** 資料行轉換為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="21797-209">This transformation passes through the **AddressID** column and converts the **City** column to uppercase.</span></span> <span data-ttu-id="21797-210">如果城市名稱是 Redmond，它會將資料列導向其中一個輸出，並將所有的其他資料列導向另一個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-210">If the city name is Redmond, it directs the row to one output; it directs all other rows to another output.</span></span>

 <span data-ttu-id="21797-211">如果您要執行這個範例程式碼，必須依下列方式設定封裝與元件：</span><span class="sxs-lookup"><span data-stu-id="21797-211">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="21797-212">將新指令碼元件加入資料流程設計師介面，並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="21797-212">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="21797-213">將來源的輸出或另一個轉換的輸出連接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的新轉換元件。</span><span class="sxs-lookup"><span data-stu-id="21797-213">Connect the output of a source or of another transformation to the new transformation component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="21797-214">這個輸出應該從範例資料庫的**Person. Address**資料表中提供資料 `AdventureWorks` ，其中至少包含**AddressID**和**City**資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-214">This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="21797-215">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="21797-215">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="21797-216">在 [輸入資料行]  頁面上，選取 [AddressID]  與 [City]  資料行。</span><span class="sxs-lookup"><span data-stu-id="21797-216">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span> <span data-ttu-id="21797-217">將 **City** 資料行標示為讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="21797-217">Mark the **City** column as Read/Write.</span></span>

4.  <span data-ttu-id="21797-218">在 [輸入及輸出]  頁面上，建立第二個輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-218">On the **Inputs and Outputs** page, create a second output.</span></span> <span data-ttu-id="21797-219">在加入新輸出之後，請確定將其 `SynchronousInputID` 設定為輸入的 `ID`。</span><span class="sxs-lookup"><span data-stu-id="21797-219">After you add the new output, make sure that you set its `SynchronousInputID` to the `ID` of the input.</span></span> <span data-ttu-id="21797-220">在預設會建立的第一個輸出上已經設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="21797-220">This property is already set on the first output, which is created by default.</span></span> <span data-ttu-id="21797-221">對於每個輸出，請將 `ExclusionGroup` 屬性設定為相同的非零值，以指出您將在兩個互斥輸出之間分割輸入資料列。</span><span class="sxs-lookup"><span data-stu-id="21797-221">For each output, set the `ExclusionGroup` property to the same non-zero value to indicate that you will split the input rows between two mutually exclusive outputs.</span></span> <span data-ttu-id="21797-222">您不必將任何輸出資料行加入輸出。</span><span class="sxs-lookup"><span data-stu-id="21797-222">You do not have to add any output columns to the outputs.</span></span>

5.  <span data-ttu-id="21797-223">使用更具描述性的名稱重新命名輸入與輸出，例如 **MyAddressInput**、**MyRedmondAddresses** 和 **MyOtherAddresses**。</span><span class="sxs-lookup"><span data-stu-id="21797-223">Rename the input and outputs with more descriptive names, such as **MyAddressInput**, **MyRedmondAddresses**, and **MyOtherAddresses**.</span></span>

6.  <span data-ttu-id="21797-224">在 [指令碼]  頁面上，按一下 [編輯指令碼]  ，並輸入以下指令碼。</span><span class="sxs-lookup"><span data-stu-id="21797-224">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="21797-225">然後關閉指令碼開發環境以及 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="21797-225">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="21797-226">建立和設定兩個需要 **AddressID** 和 **City** 資料行的目的地元件，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地、一般檔案目的地，或是在[使用指令碼元件建立目的地](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中所示範的範例目的地元件。</span><span class="sxs-lookup"><span data-stu-id="21797-226">Create and configure two destination components that expect the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, a Flat File destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="21797-227">然後將每個轉換輸出連接到其中一個目的地元件。</span><span class="sxs-lookup"><span data-stu-id="21797-227">Then connect each of the outputs of the transformation to one of the destination components.</span></span> <span data-ttu-id="21797-228">您可以在 `AdventureWorks` 資料庫中執行類似下列程式碼 (具有唯一的資料表名稱) 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令，以建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="21797-228">You can create destination tables by running a [!INCLUDE[tsql](../../includes/tsql-md.md)] command similar to the following (with unique table names) in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2](
        [AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL
    ```

8.  <span data-ttu-id="21797-229">執行範例。</span><span class="sxs-lookup"><span data-stu-id="21797-229">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        Row.City = UCase(Row.City)

        If Row.City = "REDMOND" Then
            Row.DirectRowToMyRedmondAddresses()
        Else
            Row.DirectRowToMyOtherAddresses()
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        Row.City = (Row.City).ToUpper();

        if (Row.City == "REDMOND")
        {
            Row.DirectRowToMyRedmondAddresses();
        }
        else
        {
            Row.DirectRowToMyOtherAddresses();
        }

    }
}
```

<span data-ttu-id="21797-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **掌握 Integration Services 的最新狀態**</span><span class="sxs-lookup"><span data-stu-id="21797-230">|![](./media/creating-a-synchronous-transformation-with-the-script-component/dts-16.gif)  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="21797-231">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="21797-231">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/msconame-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="21797-232">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="21797-232">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="21797-233">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="21797-233">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="21797-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21797-234">See Also</span></span>
 <span data-ttu-id="21797-235">[瞭解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)[使用腳本元件建立異步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)[使用同步輸出開發自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="21797-235">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating an Asynchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)</span></span>


