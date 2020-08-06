---
title: 使用指令碼元件建立非同步轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- asynchronous outputs [Integration Services]
- transformation components [Integration Services]
- Script component [Integration Services], transformation components
ms.assetid: 0d814404-21e4-4a68-894c-96fa47ab25ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 465c4a597b4a18d7bd956116cd5d7640a5393958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596775"
---
# <a name="creating-an-asynchronous-transformation-with-the-script-component"></a><span data-ttu-id="2cdaa-102">使用指令碼元件建立非同步轉換</span><span class="sxs-lookup"><span data-stu-id="2cdaa-102">Creating an Asynchronous Transformation with the Script Component</span></span>
  <span data-ttu-id="2cdaa-103">您在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的資料流程中使用轉換元件，以修改及分析從來源傳遞到目的地的資料。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-103">You use a transformation component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to modify and analyze data as it passes from source to destination.</span></span> <span data-ttu-id="2cdaa-104">具有同步輸出的轉換會處理通過該元件的每個輸入資料列。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-104">A transformation with synchronous outputs processes each input row as it passes through the component.</span></span> <span data-ttu-id="2cdaa-105">具有非同步輸出的轉換可能會等候完成其處理作業，直到轉換作業收到所有輸入資料列為止，或者轉換作業可能會在收到所有輸入資料列以前先輸出某些資料列。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-105">A transformation with asynchronous outputs may wait to complete its processing until the transformation has received all input rows, or the transformation may output certain rows before it has received all input rows.</span></span> <span data-ttu-id="2cdaa-106">本主題將討論非同步轉換。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-106">This topic discusses an asynchronous transformation.</span></span> <span data-ttu-id="2cdaa-107">如果您的處理需要同步轉換，請參閱[使用指令碼元件建立同步轉換](../data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-107">If your processing requires a synchronous transformation, see [Creating a Synchronous Transformation with the Script Component](../data-flow/transformations/script-component.md).</span></span> <span data-ttu-id="2cdaa-108">如需同步與非同步元件之間差異的詳細資訊，請參閱[了解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-108">For more information about the differences between synchronous and asynchronous components, see [Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md).</span></span>

 <span data-ttu-id="2cdaa-109">如需指令碼元件的概觀，請參閱[使用指令碼元件擴充資料流程](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-109">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).</span></span>

 <span data-ttu-id="2cdaa-110">指令碼元件以及它為您產生的基礎結構程式碼，可簡化開發自訂資料流程元件的程序。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-110">The Script component and the infrastructure code that it generates for you simplify the process of developing a custom data flow component.</span></span> <span data-ttu-id="2cdaa-111">不過，若要了解指令碼元件運作方式，請參閱[開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)一節中有關開發自訂資料流程元件所必須遵循的步驟，尤其是[開發具有同步輸出的自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)，可能會非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-111">However, to understand how the Script component works, you may find it useful to read through the steps that you must follow in developing a custom data flow component in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Transformation Component with Synchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md).</span></span>

## <a name="getting-started-with-an-asynchronous-transformation-component"></a><span data-ttu-id="2cdaa-112">開始使用非同步轉換元件</span><span class="sxs-lookup"><span data-stu-id="2cdaa-112">Getting Started with an Asynchronous Transformation Component</span></span>
 <span data-ttu-id="2cdaa-113">當您將指令碼元件新增至 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具的 [資料流程] 索引標籤時，就會開啟 [選取指令碼元件類型]  對話方塊，提示您將此元件預先設定為來源、轉換或目的地。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-113">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box appears, prompting you to preconfigure the component as a source, transformation, or destination.</span></span> <span data-ttu-id="2cdaa-114">在這個對話方塊中，選取 [轉換]  。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-114">In this dialog box, select **Transformation**.</span></span>

## <a name="configuring-an-asynchronous-transformation-component-in-metadata-design-mode"></a><span data-ttu-id="2cdaa-115">在中繼資料設計模式中設定非同步轉換元件</span><span class="sxs-lookup"><span data-stu-id="2cdaa-115">Configuring an Asynchronous Transformation Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="2cdaa-116">在您選取可建立轉換元件的選項之後，請使用 [指令碼轉換編輯器]  來設定元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-116">After you select the option to create a transformation component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="2cdaa-117">如需詳細資訊，請參閱[在指令碼元件編輯器中設定指令碼元件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-117">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="2cdaa-118">若要選取指令碼元件將要使用的指令碼語言，請在 [指令碼轉換編輯器] 對話方塊的 [指令碼] 頁面上設定 [ScriptLanguage] 屬性。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-118">To select the script language that the Script component will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="2cdaa-119">若要為指令碼元件設定預設的指令碼語言，請使用 [選項] 對話方塊中 [一般] 頁面上的 [指令碼語言] 選項。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-119">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="2cdaa-120">如需相關資訊，請參閱 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-120">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="2cdaa-121">資料流程轉換元件有一個輸入，而且支援一或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-121">A data flow transformation component has one input and supports one or more outputs.</span></span> <span data-ttu-id="2cdaa-122">設定元件的輸入與輸出是您必須在中繼資料設計模式下完成的其中一個步驟，方法是在撰寫自訂指令碼之前先使用 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-122">Configuring the input and outputs of your component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="configuring-input-columns"></a><span data-ttu-id="2cdaa-123">設定輸入資料行</span><span class="sxs-lookup"><span data-stu-id="2cdaa-123">Configuring Input Columns</span></span>
 <span data-ttu-id="2cdaa-124">使用指令碼元件建立的轉換元件具有單一輸入。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-124">A transformation component created by using the Script component has a single input.</span></span>

 <span data-ttu-id="2cdaa-125">在 [指令碼轉換編輯器] 的 [輸入資料行] 頁面上，資料行清單會從資料流程中的上游元件輸出顯示可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-125">On the **Input Columns** page of the **Script Transformation Editor**, the columns list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="2cdaa-126">選取要轉換或通過的資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-126">Select the columns that you want to transform or pass through.</span></span> <span data-ttu-id="2cdaa-127">將任何您要就地轉換的資料行標示成「讀取/寫入」。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-127">Mark any columns that you want to transform in place as Read/Write.</span></span>

 <span data-ttu-id="2cdaa-128">如需 [指令碼轉換編輯器] 的 [輸入資料行] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入資料行頁面&#41;](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-128">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

### <a name="configuring-inputs-outputs-and-output-columns"></a><span data-ttu-id="2cdaa-129">設定輸入、輸出及輸出資料行</span><span class="sxs-lookup"><span data-stu-id="2cdaa-129">Configuring Inputs, Outputs, and Output Columns</span></span>
 <span data-ttu-id="2cdaa-130">轉換元件支援一或多個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-130">A transformation component supports one or more outputs.</span></span>

 <span data-ttu-id="2cdaa-131">通常具有非同步輸出的轉換有兩個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-131">Frequently a transformation with asynchronous outputs has two outputs.</span></span> <span data-ttu-id="2cdaa-132">例如，當您計算位於特定城市的位址數時，您可能會想要將此位址資料傳遞給某個輸出，而將彙總的結果傳送給另一個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-132">For example, when you count the number of addresses located in a specific city, you may want to pass the address data through to one output, while sending the result of the aggregation to another output.</span></span> <span data-ttu-id="2cdaa-133">彙總輸出也需要新的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-133">The aggregation output also requires a new output column.</span></span>

 <span data-ttu-id="2cdaa-134">在 [指令碼轉換編輯器] 的 [輸入及輸出] 頁面上，您會看到預設已建立單一輸出，但是尚未建立輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-134">On the **Inputs and Outputs** page of the **Script Transformation Editor**, you see that a single output has been created by default, but no output columns have been created.</span></span> <span data-ttu-id="2cdaa-135">在編輯器的這個頁面上，您可設定下列項目：</span><span class="sxs-lookup"><span data-stu-id="2cdaa-135">On this page of the editor, you can configure the following items:</span></span>

-   <span data-ttu-id="2cdaa-136">您可能會想要建立一或多個其他輸出，例如彙總結果的輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-136">You may want to create one or more additional outputs, such as an output for the result of an aggregation.</span></span> <span data-ttu-id="2cdaa-137">使用 [新增輸出]  和 [移除輸出]  按鈕管理非同步轉換元件的輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-137">Use the **Add Output** and **Remove Output** buttons to manage the outputs of your asynchronous transformation component.</span></span> <span data-ttu-id="2cdaa-138">將每一個輸出的 `SynchronousInputID` 屬性設定為零來指示，輸出不會只是通過上游元件中的資料，或是在現有的資料列和資料行中就地轉換它。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-138">Set the `SynchronousInputID` property of each output to zero to indicate that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns.</span></span> <span data-ttu-id="2cdaa-139">這項設定會讓輸出與輸入不同步。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-139">It is this setting that makes the outputs asynchronous to the input.</span></span>

-   <span data-ttu-id="2cdaa-140">您可能會想要將易記名稱指派給輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-140">You may want to assign a friendly name to the input and outputs.</span></span> <span data-ttu-id="2cdaa-141">指令碼元件使用這些名稱來產生具類型的存取子屬性，您將使用這些屬性來參考指令碼中的輸入和輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-141">The Script component uses these names to generate the typed accessor properties that you will use to refer to the input and outputs in your script.</span></span>

-   <span data-ttu-id="2cdaa-142">一般而言，非同步轉換會將資料行加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-142">Frequently an asynchronous transformation adds columns to the data flow.</span></span> <span data-ttu-id="2cdaa-143">當輸出的 `SynchronousInputID` 屬性設定為零來指示輸出不會只是通過上游元件中的資料，或是在現有的資料列和資料行中就地轉換它時，您必須明確地在輸出上加入及設定輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-143">When the `SynchronousInputID` property of an output is zero, indicating that the output does not simply pass through data from an upstream component or transform it in place in the existing rows and columns, you must add and configure output columns explicitly on the output.</span></span> <span data-ttu-id="2cdaa-144">輸出資料行不需要與其對應的輸入資料行同名。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-144">Output columns do not have to have the same names as the input columns to which they are mapped.</span></span>

-   <span data-ttu-id="2cdaa-145">您可能會想要加入更多的資料行來包含其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-145">You may want to add more columns to contain additional information.</span></span> <span data-ttu-id="2cdaa-146">您必須撰寫自己的程式碼，才能用資料填滿其他資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-146">You must write your own code to fill the additional columns with data.</span></span> <span data-ttu-id="2cdaa-147">如需重新產生標準錯誤輸出之行為的資訊，請參閱[模擬指令碼元件的錯誤輸出](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-147">For information about reproducing the behavior of a standard error output, see [Simulating an Error Output for the Script Component](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md).</span></span>

 <span data-ttu-id="2cdaa-148">如需 [指令碼轉換編輯器] 之 [輸入及輸出] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入及輸出頁面&#41;](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-148">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="2cdaa-149">加入變數</span><span class="sxs-lookup"><span data-stu-id="2cdaa-149">Adding Variables</span></span>
 <span data-ttu-id="2cdaa-150">如果有任何要在指令碼中使用其值的現有變數，則可以在 [指令碼轉換編輯器] 的 [指令碼] 頁面上，將它們新增至 ReadOnlyVariables 和 ReadWriteVariables 屬性欄位中。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-150">If there are any existing variables whose values you want to use in your script, you can add them in the ReadOnlyVariables and ReadWriteVariables property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="2cdaa-151">當您在屬性欄位中加入多個變數時，請用逗號分隔變數名稱。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-151">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="2cdaa-152">您也可以按一下和屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後選取 `ReadOnlyVariables` `ReadWriteVariables` [**選取變數**] 對話方塊中的變數，來選取多個變數。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-152">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="2cdaa-153">如需如何利用指令碼元件使用變數的一般資訊，請參閱[在指令碼元件中使用變數](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-153">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="2cdaa-154">如需 [指令碼轉換編輯器] 的 [指令碼] 頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;指令碼頁面&#41;](../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-154">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-an-asynchronous-transformation-component-in-code-design-mode"></a><span data-ttu-id="2cdaa-155">在程式碼設計模式中編寫非同步轉換元件的指令碼</span><span class="sxs-lookup"><span data-stu-id="2cdaa-155">Scripting an Asynchronous Transformation Component in Code-Design Mode</span></span>
 <span data-ttu-id="2cdaa-156">在您設定好元件的所有中繼資料之後，便可撰寫自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-156">After you have configured all the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="2cdaa-157">在 [指令碼轉換編輯器]  的 [指令碼]  頁面上，按一下 [編輯指令碼]  來開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE 以新增自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-157">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="2cdaa-158">所使用的指令碼語言取決於您選取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 還是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作為 [指令碼] 頁面上 **ScriptLanguage** 屬性的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-158">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="2cdaa-159">如需使用指令碼元件所建立之各種元件都適用的重要資訊，請參閱[編碼和偵錯指令碼元件](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-159">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="2cdaa-160">了解自動產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="2cdaa-160">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="2cdaa-161">當您在建立和設定轉換元件之後開啟 VSTA IDE 時，可編輯的 `ScriptMain` 類別會出現在程式碼編輯器中，並具有 ProcessInputRow 和 CreateNewOutputRows 方法的 stub。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-161">When you open the VSTA IDE after creating and configuring a transformation component, the editable `ScriptMain` class appears in the code editor with stubs for the ProcessInputRow and the CreateNewOutputRows methods.</span></span> <span data-ttu-id="2cdaa-162">ScriptMain 類別是您將撰寫自訂程式碼的地方，而 ProcessInputRow 則是轉換元件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-162">The ScriptMain class is where you will write your custom code, and ProcessInputRow is the most important method in a transformation component.</span></span> <span data-ttu-id="2cdaa-163">`CreateNewOutputRows` 方法通常比較常在來源元件中使用，這就像非同步轉換，因為兩個元件都必須建立自己的輸出資料列。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-163">The `CreateNewOutputRows` method is more typically used in a source component, which is like an asynchronous transformation in that both components must create their own output rows.</span></span>

 <span data-ttu-id="2cdaa-164">如果您開啟 [VSTA**專案瀏覽器**] 視窗，您可以看到腳本元件也會產生唯讀 `BufferWrapper` 和專案專案 `ComponentWrapper` 。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-164">If you open the VSTA **Project Explorer** window, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="2cdaa-165">ScriptMain 類別繼承自專案專案中的 UserComponent 類別 `ComponentWrapper` 。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-165">The ScriptMain class inherits from the UserComponent class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="2cdaa-166">在執行時間，資料流程引擎會呼叫類別中的 PrimeOutput 方法 `UserComponent` ，它會覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> 父類別的方法 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-166">At run time, the data flow engine calls the PrimeOutput method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost.PrimeOutput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="2cdaa-167">PrimeOutput 方法接著會呼叫 CreateNewOutputRows 方法。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-167">The PrimeOutput method in turn calls the CreateNewOutputRows method.</span></span>

 <span data-ttu-id="2cdaa-168">接下來，資料流程引擎會叫用 UserComponent 類別中的 ProcessInput 方法，它會覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 父類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-168">Next, the data flow engine invokes the ProcessInput method in the UserComponent class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="2cdaa-169">ProcessInput 方法接著會在輸入緩衝區的資料列中執行迴圈，並為每個資料列呼叫一次 ProcessInputRow 方法。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-169">The ProcessInput method in turn loops through the rows in the input buffer and calls the ProcessInputRow method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="2cdaa-170">撰寫您的自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="2cdaa-170">Writing Your Custom Code</span></span>
 <span data-ttu-id="2cdaa-171">若要完成自訂非同步轉換元件的建立，您必須使用覆寫的 ProcessInputRow 方法來處理輸入緩衝區之每個資料列中的資料。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-171">To finish creating a custom asynchronous transformation component, you must use the overridden ProcessInputRow method to process the data in each row of the input buffer.</span></span> <span data-ttu-id="2cdaa-172">因為輸出與輸入不同步，所以您必須將資料列明確寫入輸出中。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-172">Because the outputs are not synchronous to the input, you must explicitly write rows of data to the outputs.</span></span>

 <span data-ttu-id="2cdaa-173">在非同步轉換中，您可以使用 AddRow 方法，從 ProcessInputRow 或 ProcessInput 方法適當地將資料列新增至輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-173">In an asynchronous transformation, you can use the AddRow method to add rows to the output as appropriate from within the ProcessInputRow or ProcessInput methods.</span></span> <span data-ttu-id="2cdaa-174">您不需要使用 CreateNewOutputRows 方法。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-174">You do not have to use the CreateNewOutputRows method.</span></span> <span data-ttu-id="2cdaa-175">如果您要將單一結果資料列 (如彙總結果) 寫入特定輸出，您可以事先使用 CreateNewOutputRows 方法建立輸出資料列，然後在處理所有輸入資料列之後填入它的值。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-175">If you are writing a single row of results, such as aggregation results, to a particular output, you can create the output row beforehand by using the CreateNewOutputRows method, and fill in its values later after processing all input rows.</span></span> <span data-ttu-id="2cdaa-176">不過，在 CreateNewOutputRows 方法中建立多個資料列並不實用，因為指令碼元件只能讓您在輸入或輸出中使用目前的資料列。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-176">However it is not useful to create multiple rows in the CreateNewOutputRows method, because the Script component only lets you use the current row in an input or output.</span></span> <span data-ttu-id="2cdaa-177">在沒有輸入資料列要處理的來源元件中，CreateNewOutputRows 方法比較重要。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-177">The CreateNewOutputRows method is more important in a source component where there are no input rows to process.</span></span>

 <span data-ttu-id="2cdaa-178">您可能也會想要覆寫 ProcessInput 方法本身，好讓您在輸入緩衝區內執行迴圈及針對每一個資料列呼叫 ProcessInputRow 之前或之後，可以執行其他初步或最終處理。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-178">You may also want to override the ProcessInput method itself, so that you can do additional preliminary or final processing before or after you loop through the input buffer and call ProcessInputRow for each row.</span></span> <span data-ttu-id="2cdaa-179">例如，本主題的其中一個程式碼範例會覆寫 ProcessInput，以計算特定城市的位址數目，做為 ProcessInputRow 迴圈的資料列 `.` 。此範例會在處理完所有資料列之後，將摘要值寫入第二個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-179">For example, one of the code examples in this topic overrides ProcessInput to count the number of addresses in a specific city as ProcessInputRow loops through rows`.` The example writes the summary value to the second output after all rows have been processed.</span></span> <span data-ttu-id="2cdaa-180">此範例會完成 ProcessInput 中的輸出，因為呼叫 PostExecute 時輸出緩衝區將不再可用。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-180">The example completes the output in ProcessInput because the output buffers are no longer available when PostExecute is called.</span></span>

 <span data-ttu-id="2cdaa-181">視您的需求而定，您也可能會想要在 PreExecute 和 PostExecute 方法 (可在 ScriptMain 類別中取得) 中撰寫指令碼，以執行任何初步或最終處理。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-181">Depending on your requirements, you may also want to write script in the PreExecute and PostExecute methods available in the ScriptMain class to perform any preliminary or final processing.</span></span>

> [!NOTE]
>  <span data-ttu-id="2cdaa-182">如果您從頭開始來開發自訂資料流程元件，則覆寫 PrimeOutput 方法來快取輸出緩衝區的參考，好讓您可以在之後將資料列新增至緩衝區是很重要的事情。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-182">If you were developing a custom data flow component from scratch, it would be important to override the PrimeOutput method to cache references to the output buffers so that you could add rows of data to the buffers later.</span></span> <span data-ttu-id="2cdaa-183">在指令碼元件中，這不是必要的，因為您已經在 `BufferWrapper` 專案項目中自動產生代表每一個輸出緩衝區的類別。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-183">In the Script component, this is not necessary because you have an automatically generated class representing each output buffer in the `BufferWrapper` project item.</span></span>

## <a name="example"></a><span data-ttu-id="2cdaa-184">範例</span><span class="sxs-lookup"><span data-stu-id="2cdaa-184">Example</span></span>
 <span data-ttu-id="2cdaa-185">此範例示範在 ScriptMain 類別中所需的自訂程式碼，以建立非同步轉換元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-185">This example demonstrates the custom code that is required in the ScriptMain class to create an asynchronous transformation component.</span></span>

> [!NOTE]
>  <span data-ttu-id="2cdaa-186">這些範例使用 **AdventureWorks** 範例資料庫中的 **Person.Address** 資料表，並透過資料流程傳遞其第一個和第四個資料行：**intAddressID** 和 **nvarchar(30)City** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-186">These examples use the **Person.Address** table in the **AdventureWorks** sample database and pass its first and fourth columns, the **intAddressID** and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="2cdaa-187">在本章節中的來源、轉換和目的地範例使用相同的資料。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-187">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="2cdaa-188">每個範例都會記載其他必要條件與假設。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-188">Additional prerequisites and assumptions are documented for each example.</span></span>

 <span data-ttu-id="2cdaa-189">此範例示範具有兩個輸出的非同步轉換元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-189">This example demonstrates an asynchronous transformation component with two outputs.</span></span> <span data-ttu-id="2cdaa-190">此轉換會通過 **AddressID** 和 **City** 資料行傳遞給一個輸出，而它會計算位於特定城市 (美國華盛頓州 Redmond 城市) 的地址數目，然後將產生的值輸出給第二個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-190">This transformation passes through the **AddressID** and **City** columns to one output, while it counts the number of addresses located in a specific city (Redmond, Washington, U.S.A.), and then outputs the resulting value to a second output.</span></span>

 <span data-ttu-id="2cdaa-191">如果您要執行這個範例程式碼，必須依下列方式設定封裝與元件：</span><span class="sxs-lookup"><span data-stu-id="2cdaa-191">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="2cdaa-192">將新指令碼元件加入資料流程設計師介面，並將它設定為轉換。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-192">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span>

2.  <span data-ttu-id="2cdaa-193">將來源的輸出或另一個轉換的輸出連接到設計師中的新轉換元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-193">Connect the output of a source or of another transformation to the new transformation component in the designer.</span></span> <span data-ttu-id="2cdaa-194">這個輸出應該從 **AdventureWorks** 範例資料庫的 **Person.Address** 資料表中提供資料，這個資料表至少包含 **AddressID** 和 **City** 資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-194">This output should provide data from the **Person.Address** table of the **AdventureWorks** sample database that contains at least the **AddressID** and **City** columns.</span></span>

3.  <span data-ttu-id="2cdaa-195">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-195">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="2cdaa-196">在 [輸入資料行]  頁面上，選取 [AddressID]  與 [City]  資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-196">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="2cdaa-197">在 [輸入及輸出]\*\*\*\* 頁面上，於第一個輸出新增和設定 **AddressID** 和 **City** 輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-197">On the **Inputs and Outputs** page, add and configure the **AddressID** and **City** output columns on the first output.</span></span> <span data-ttu-id="2cdaa-198">加入第二個輸出，然後在第二個輸出上加入摘要值的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-198">Add a second output, and add an output column for the summary value on the second output.</span></span> <span data-ttu-id="2cdaa-199">將第一個輸出的 SynchronousInputID 屬性設定為 0，因為這個範例會將每一個輸入資料列明確地複製到第一個輸出。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-199">Set the SynchronousInputID property of the first output to 0, because this example copies each input row explicitly to the first output.</span></span> <span data-ttu-id="2cdaa-200">新建立之輸出的 SynchronousInputID 屬性已經設定為 0。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-200">The SynchronousInputID property of the newly-created output is already set to 0.</span></span>

5.  <span data-ttu-id="2cdaa-201">重新命名輸入、輸出和新的輸出資料行，為它們提供更具描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-201">Rename the input, the outputs, and the new output column to give them more descriptive names.</span></span> <span data-ttu-id="2cdaa-202">此範例使用 **MyAddressInput** 作為輸入的名稱、使用 **MyAddressOutput** 和 **MySummaryOutput** 作為輸出，並使用 **MyRedmondCount** 作為第二個輸出的輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-202">The example uses **MyAddressInput** as the name of the input, **MyAddressOutput** and **MySummaryOutput** for the outputs, and **MyRedmondCount** for the output column on the second output.</span></span>

6.  <span data-ttu-id="2cdaa-203">在 [指令碼]  頁面上，按一下 [編輯指令碼]  ，並輸入以下指令碼。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-203">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="2cdaa-204">然後關閉指令碼開發環境以及 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-204">Then close the script development environment and the **Script Transformation Editor**.</span></span>

7.  <span data-ttu-id="2cdaa-205">針對第一個輸出建立及設定需要 **AddressID** 和 **City** 資料行的目的地元件，例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地，或是在[使用指令碼元件建立目的地](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)中所示範的範例目的地元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-205">Create and configure a destination component for the first output that expects the **AddressID** and **City** columns, such as a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, or the sample destination component demonstrated in [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md), .</span></span> <span data-ttu-id="2cdaa-206">然後將轉換的第一個輸出 **MyAddressOutput** 連線至目的地元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-206">Then connect the first output of the transformation, **MyAddressOutput**, to the destination component.</span></span> <span data-ttu-id="2cdaa-207">您可以在 **AdventureWorks** 資料庫中執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令，以建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="2cdaa-207">You can create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the **AdventureWorks** database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

8.  <span data-ttu-id="2cdaa-208">為第二個輸出建立及設定另一個目的地元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-208">Create and configure another destination component for the second output.</span></span> <span data-ttu-id="2cdaa-209">然後將轉換的第二個輸出 **MySummaryOutput** 連線至目的地元件。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-209">Then connect the second output of the transformation, **MySummaryOutput**, to the destination component.</span></span> <span data-ttu-id="2cdaa-210">因為第二個輸出會寫入具有單一值的單一資料列，所以您可以輕鬆地使用一般檔案連接管理員來設定目的地，此管理員會連接到具有單一資料行的新檔案。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-210">Because the second output writes a single row with a single value, you can easily configure a destination with a Flat File connection manager that connects to a new file that has a single column.</span></span> <span data-ttu-id="2cdaa-211">在此範例中，這個目的地資料行命名為 **MyRedmondCount**。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-211">In the example, this destination column is named **MyRedmondCount**.</span></span>

9. <span data-ttu-id="2cdaa-212">執行範例。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-212">Run the sample.</span></span>

```vb
Public Class ScriptMain
    Inherits UserComponent

    Private myRedmondAddressCount As Integer

    Public Overrides Sub CreateNewOutputRows()

        MySummaryOutputBuffer.AddRow()

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInput(ByVal Buffer As MyAddressInputBuffer)

        While Buffer.NextRow()
            MyAddressInput_ProcessInputRow(Buffer)
        End While

        If Buffer.EndOfRowset Then
            MyAddressOutputBuffer.SetEndOfRowset()
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount
            MySummaryOutputBuffer.SetEndOfRowset()
        End If

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With MyAddressOutputBuffer
            .AddRow()
            .AddressID = Row.AddressID
            .City = Row.City
        End With

        If Row.City.ToUpper = "REDMOND" Then
            myRedmondAddressCount += 1
        End If

    End Sub

End Class
```

```csharp
public class ScriptMain:
    UserComponent

{
    private int myRedmondAddressCount;

    public override void CreateNewOutputRows()
    {

        MySummaryOutputBuffer.AddRow();

    }

    public override void MyAddressInput_ProcessInput(MyAddressInputBuffer Buffer)
    {

        while (Buffer.NextRow())
        {
            MyAddressInput_ProcessInputRow(Buffer);
        }

        if (Buffer.EndOfRowset())
        {
            MyAddressOutputBuffer.SetEndOfRowset();
            MySummaryOutputBuffer.MyRedmondCount = myRedmondAddressCount;
            MySummaryOutputBuffer.SetEndOfRowset();
        }

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            MyAddressOutputBuffer.AddRow();
            MyAddressOutputBuffer.AddressID = Row.AddressID;
            MyAddressOutputBuffer.City = Row.City;
        }

        if (Row.City.ToUpper() == "REDMOND")
        {
            myRedmondAddressCount += 1;
        }

    }

}

```

<span data-ttu-id="2cdaa-213">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="2cdaa-213">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2cdaa-214">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="2cdaa-214">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2cdaa-215">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="2cdaa-215">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2cdaa-216">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="2cdaa-216">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cdaa-217">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cdaa-217">See Also</span></span>
 <span data-ttu-id="2cdaa-218">[瞭解同步和非同步轉換](../understanding-synchronous-and-asynchronous-transformations.md)[使用腳本元件建立同步轉換](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)[使用非同步輸出開發自訂轉換元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span><span class="sxs-lookup"><span data-stu-id="2cdaa-218">[Understanding Synchronous and Asynchronous Transformations](../understanding-synchronous-and-asynchronous-transformations.md) [Creating a Synchronous Transformation with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) [Developing a Custom Transformation Component with Asynchronous Outputs](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)</span></span>


