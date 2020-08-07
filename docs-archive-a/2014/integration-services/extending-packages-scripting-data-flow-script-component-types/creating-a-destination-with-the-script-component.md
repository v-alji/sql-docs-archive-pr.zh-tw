---
title: 使用指令碼元件建立目的地 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], destination components
- destinations [Integration Services], components
- input columns [Integration Services]
ms.assetid: 214e22e8-7e7d-4876-b690-c138e5721b81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1245dde111b24d1c37e2c5550d236c97126ee725
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597960"
---
# <a name="creating-a-destination-with-the-script-component"></a><span data-ttu-id="419be-102">以指令碼元件建立目的地</span><span class="sxs-lookup"><span data-stu-id="419be-102">Creating a Destination with the Script Component</span></span>
  <span data-ttu-id="419be-103">您可以在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的資料流程中使用目的地元件，以便將從上游來源和轉換收到的資料儲存至資料來源。</span><span class="sxs-lookup"><span data-stu-id="419be-103">You use a destination component in the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to save data received from upstream sources and transformations to a data source.</span></span> <span data-ttu-id="419be-104">通常，目的地元件會透過現有的連接管理員連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="419be-104">Ordinarily the destination component connects to the data source through an existing connection manager.</span></span>

 <span data-ttu-id="419be-105">如需腳本元件的總覽，請參閱 [使用腳本元件擴充資料流程] (.。/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span><span class="sxs-lookup"><span data-stu-id="419be-105">For an overview of the Script component, see [Extending the Data Flow with the Script Component](../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md.</span></span>

 <span data-ttu-id="419be-106">指令碼元件以及它為您產生的基礎結構程式碼，可大幅簡化開發自訂資料流程元件的程序。</span><span class="sxs-lookup"><span data-stu-id="419be-106">The Script component and the infrastructure code that it generates for you simplify significantly the process of developing a custom data flow component.</span></span> <span data-ttu-id="419be-107">不過，若要了解指令碼元件運作方式，建議您詳細閱讀[開發自訂資料流程元件](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)一節中開發自訂資料流程元件的步驟，尤其是[開發自訂目的地元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-107">However, to understand how the Script component works, you may find it useful to read through the steps for developing a custom data flow components in the [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) section, and especially [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md).</span></span>

## <a name="getting-started-with-a-destination-component"></a><span data-ttu-id="419be-108">開始使用目的地元件</span><span class="sxs-lookup"><span data-stu-id="419be-108">Getting Started with a Destination Component</span></span>
 <span data-ttu-id="419be-109">當您將指令碼元件新增至 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具的 [資料流程] 索引標籤時，就會開啟 [選取指令碼元件類型]  對話方塊，並提示您選取 [來源]  、[目的地]  或 [轉換]  指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-109">When you add a Script component to the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the **Select Script Component Type** dialog box opens and prompts you to select a **Source**, **Destination**, or **Transformation** script.</span></span> <span data-ttu-id="419be-110">在這個對話方塊中，請選取 [目的地]  。</span><span class="sxs-lookup"><span data-stu-id="419be-110">In this dialog box, select **Destination**.</span></span>

 <span data-ttu-id="419be-111">接著，請將轉換的輸出連接至 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的目的地元件。</span><span class="sxs-lookup"><span data-stu-id="419be-111">Next, connect the output of a transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="419be-112">進行測試時，您不需要任何轉換，就可以直接將來源連接至目的地。</span><span class="sxs-lookup"><span data-stu-id="419be-112">For testing, you can connect a source directly to a destination without any transformations.</span></span>

## <a name="configuring-a-destination-component-in-metadata-design-mode"></a><span data-ttu-id="419be-113">在中繼資料設計模式中設定目的地元件</span><span class="sxs-lookup"><span data-stu-id="419be-113">Configuring a Destination Component in Metadata-Design Mode</span></span>
 <span data-ttu-id="419be-114">在選取選項以建立目的地元件之後，您可以使用 [指令碼轉換編輯器]  來設定元件。</span><span class="sxs-lookup"><span data-stu-id="419be-114">After you select the option to create a destination component, you configure the component by using the **Script Transformation Editor**.</span></span> <span data-ttu-id="419be-115">如需詳細資訊，請參閱[在指令碼元件編輯器中設定指令碼元件](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-115">For more information, see [Configuring the Script Component in the Script Component Editor](../extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).</span></span>

 <span data-ttu-id="419be-116">若要選取指令碼目的地將使用的指令碼語言，請在 [指令碼轉換編輯器]  對話方塊的 [指令碼]  頁面上，設定 **ScriptLanguage** 屬性。</span><span class="sxs-lookup"><span data-stu-id="419be-116">To select the script language that the Script destination will use, you set the **ScriptLanguage** property on the **Script** page of the **Script Transformation Editor** dialog box.</span></span>

> [!NOTE]
>  <span data-ttu-id="419be-117">若要為指令碼元件設定預設的指令碼語言，請使用 [選項]  對話方塊中 [一般]  頁面上的 [指令碼語言]  選項。</span><span class="sxs-lookup"><span data-stu-id="419be-117">To set the default scripting language for the Script component, use the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="419be-118">如需相關資訊，請參閱 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-118">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>

 <span data-ttu-id="419be-119">資料流程目的地元件有一個輸入，但是沒有任何輸出。</span><span class="sxs-lookup"><span data-stu-id="419be-119">A data flow destination component has one input and no outputs.</span></span> <span data-ttu-id="419be-120">設定元件的輸入是您必須在中繼資料設計模式下完成的其中一個步驟，方法是在撰寫自訂指令碼之前先使用 [指令碼轉換編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="419be-120">Configuring the input for the component is one of the steps that you must complete in metadata design mode, by using the **Script Transformation Editor**, before you write your custom script.</span></span>

### <a name="adding-connection-managers"></a><span data-ttu-id="419be-121">加入連接管理員</span><span class="sxs-lookup"><span data-stu-id="419be-121">Adding Connection Managers</span></span>
 <span data-ttu-id="419be-122">通常，目的地元件會使用現有的連接管理員來連接至它用來儲存資料流程之資料的資料來源。</span><span class="sxs-lookup"><span data-stu-id="419be-122">Ordinarily a destination component uses an existing connection manager to connect to the data source to which it saves data from the data flow.</span></span> <span data-ttu-id="419be-123">在 [指令碼轉換編輯器]  的 [連線管理員]  頁面上，按一下 [新增]  新增適當的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="419be-123">On the **Connection Managers** page of the **Script Transformation Editor**, click **Add** to add the appropriate connection manager.</span></span>

 <span data-ttu-id="419be-124">不過，連接管理員只是一種便利的單位，用以封裝和儲存連接至特定類型的資料來源所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="419be-124">However, a connection manager is just a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="419be-125">您必須撰寫自己的自訂程式碼來載入或儲存資料，以及 (可能的話) 開啟和關閉資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="419be-125">You must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span>

 <span data-ttu-id="419be-126">如需如何利用指令碼元件以使用連線管理員的一般資訊，請參閱[在指令碼元件中連線至資料來源](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-126">For general information about how to use connection managers with the Script component, see [Connecting to Data Sources in the Script Component](../extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md).</span></span>

 <span data-ttu-id="419be-127">如需 [指令碼轉換編輯器]  之 [連線管理員]  頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;連線管理員頁面&#41;](../script-transformation-editor-connection-managers-page.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-127">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Connection Managers Page&#41;](../script-transformation-editor-connection-managers-page.md).</span></span>

### <a name="configuring-inputs-and-input-columns"></a><span data-ttu-id="419be-128">設定輸入和輸入資料行</span><span class="sxs-lookup"><span data-stu-id="419be-128">Configuring Inputs and Input Columns</span></span>
 <span data-ttu-id="419be-129">目的地元件有一個輸入，但是沒有任何輸出。</span><span class="sxs-lookup"><span data-stu-id="419be-129">A destination component has one input and no outputs.</span></span>

 <span data-ttu-id="419be-130">在 [指令碼轉換編輯器]  的 [輸入資料行]  頁面上，資料行清單會從資料流程中的上游元件輸出顯示可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-130">On the **Input Columns** page of the **Script Transformation Editor**, the column list shows the available columns from the output of the upstream component in the data flow.</span></span> <span data-ttu-id="419be-131">請選取您想要儲存的資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-131">Select the columns that you want to save.</span></span>

 <span data-ttu-id="419be-132">如需 [指令碼轉換編輯器]  的 [輸入資料行]  頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入資料行頁面&#41;](../script-transformation-editor-input-columns-page.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-132">For more information about the **Input Columns** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Input Columns Page&#41;](../script-transformation-editor-input-columns-page.md).</span></span>

 <span data-ttu-id="419be-133">[指令碼轉換編輯器]  的 [輸入及輸出]  頁面會顯示您可以重新命名的單一輸入。</span><span class="sxs-lookup"><span data-stu-id="419be-133">The **Inputs and Outputs** page of the **Script Transformation Editor** shows a single input, which you can rename.</span></span> <span data-ttu-id="419be-134">您將使用在自動產生程式碼中建立的存取子屬性，依據指令碼中的名稱來參考輸入。</span><span class="sxs-lookup"><span data-stu-id="419be-134">You will refer to the input by its name in your script by using the accessor property created in the auto-generated code.</span></span>

 <span data-ttu-id="419be-135">如需 [指令碼轉換編輯器]  之 [輸入及輸出]  頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;輸入及輸出頁面&#41;](../script-transformation-editor-inputs-and-outputs-page.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-135">For more information about the **Inputs and Outputs** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../script-transformation-editor-inputs-and-outputs-page.md).</span></span>

### <a name="adding-variables"></a><span data-ttu-id="419be-136">加入變數</span><span class="sxs-lookup"><span data-stu-id="419be-136">Adding Variables</span></span>
 <span data-ttu-id="419be-137">如果您想要在腳本中使用現有的變數，您可以在 [ `ReadOnlyVariables` `ReadWriteVariables` **腳本轉換編輯器**] 的 [**腳本**] 頁面上，將它們加入和屬性欄位中。</span><span class="sxs-lookup"><span data-stu-id="419be-137">If you want to use existing variables in your script, you can add them in the `ReadOnlyVariables` and `ReadWriteVariables` property fields on the **Script** page of the **Script Transformation Editor**.</span></span>

 <span data-ttu-id="419be-138">當您在屬性欄位中加入多個變數時，請用逗號分隔變數名稱。</span><span class="sxs-lookup"><span data-stu-id="419be-138">When you add multiple variables in the property fields, separate the variable names by commas.</span></span> <span data-ttu-id="419be-139">您也可以按一下和屬性欄位旁邊的省略號 (**...**) ] 按鈕，然後選取 `ReadOnlyVariables` `ReadWriteVariables` [**選取變數**] 對話方塊中的變數，來選取多個變數。</span><span class="sxs-lookup"><span data-stu-id="419be-139">You can also select multiple variables by clicking the ellipsis (**...**) button next to the `ReadOnlyVariables` and `ReadWriteVariables` property fields, and then selecting the variables in the **Select variables** dialog box.</span></span>

 <span data-ttu-id="419be-140">如需如何利用指令碼元件使用變數的一般資訊，請參閱[在指令碼元件中使用變數](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-140">For general information about how to use variables with the Script component, see [Using Variables in the Script Component](../extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md).</span></span>

 <span data-ttu-id="419be-141">如需 [指令碼轉換編輯器]  的 [指令碼]  頁面的詳細資訊，請參閱[指令碼轉換編輯器 &#40;指令碼頁面&#41;](../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-141">For more information about the **Script** page of the **Script Transformation Editor**, see [Script Transformation Editor &#40;Script Page&#41;](../script-transformation-editor-script-page.md).</span></span>

## <a name="scripting-a-destination-component-in-code-design-mode"></a><span data-ttu-id="419be-142">在程式碼設計模式中編寫目的地元件的指令碼</span><span class="sxs-lookup"><span data-stu-id="419be-142">Scripting a Destination Component in Code-Design Mode</span></span>
 <span data-ttu-id="419be-143">在您設定好元件的中繼資料之後，便可撰寫自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-143">After you have configured the metadata for your component, you can write your custom script.</span></span> <span data-ttu-id="419be-144">在 [指令碼轉換編輯器]  的 [指令碼]  頁面上，按一下 [編輯指令碼]  來開啟 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE 以新增自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-144">In the **Script Transformation Editor**, on the **Script** page, click **Edit Script** to open the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE where you can add your custom script.</span></span> <span data-ttu-id="419be-145">所使用的指令碼語言取決於您選取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 還是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 作為 [指令碼]  頁面上 **ScriptLanguage** 屬性的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="419be-145">The scripting language that you use depends on whether you selected [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# as the script language for the **ScriptLanguage** property on the **Script** page.</span></span>

 <span data-ttu-id="419be-146">如需使用指令碼元件所建立之各種元件都適用的重要資訊，請參閱[編碼和偵錯指令碼元件](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="419be-146">For important information that applies to all kinds of components created by using the Script component, see [Coding and Debugging the Script Component](../extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).</span></span>

### <a name="understanding-the-auto-generated-code"></a><span data-ttu-id="419be-147">了解自動產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="419be-147">Understanding the Auto-generated Code</span></span>
 <span data-ttu-id="419be-148">當您在建立和設定目的地元件之後開啟 VSTA IDE 時，可編輯的 `ScriptMain` 類別會出現在程式碼編輯器中，並具有 `ProcessInputRow` 方法的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="419be-148">When you open the VSTA IDE after you create and configuring a destination component, the editable `ScriptMain` class appears in the code editor with a stub for the `ProcessInputRow` method.</span></span> <span data-ttu-id="419be-149">`ScriptMain` 類別是您將撰寫自訂程式碼的地方，而 `ProcessInputRow` 則是目的地元件中最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="419be-149">The `ScriptMain` class is where you will write your custom code, and `ProcessInputRow` is the most important method in a destination component.</span></span>

 <span data-ttu-id="419be-150">如果您在 VSTA 中開啟 [**專案管理器**] 視窗，您可以看到腳本元件也會產生唯讀 `BufferWrapper` 和 `ComponentWrapper` 專案專案。</span><span class="sxs-lookup"><span data-stu-id="419be-150">If you open the **Project Explorer** window in VSTA, you can see that the Script component has also generated read-only `BufferWrapper` and `ComponentWrapper` project items.</span></span> <span data-ttu-id="419be-151">`ScriptMain` 類別會繼承 `UserComponent` 專案項目中的 `ComponentWrapper` 類別。</span><span class="sxs-lookup"><span data-stu-id="419be-151">The `ScriptMain` class inherits from `UserComponent` class in the `ComponentWrapper` project item.</span></span>

 <span data-ttu-id="419be-152">在執行階段，資料流程引擎會叫用 `ProcessInput` 類別中的 `UserComponent` 方法，它會覆寫 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> 父類別的 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 方法。</span><span class="sxs-lookup"><span data-stu-id="419be-152">At run time, the data flow engine invokes the `ProcessInput` method in the `UserComponent` class, which overrides the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ProcessInput%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> parent class.</span></span> <span data-ttu-id="419be-153">`ProcessInput` 方法接著會在輸入緩衝區的資料列中執行迴圈，並為每個資料列呼叫一次 `ProcessInputRow` 方法。</span><span class="sxs-lookup"><span data-stu-id="419be-153">The `ProcessInput` method in turn loops through the rows in the input buffer and calls the `ProcessInputRow` method one time for each row.</span></span>

### <a name="writing-your-custom-code"></a><span data-ttu-id="419be-154">撰寫您的自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="419be-154">Writing Your Custom Code</span></span>
 <span data-ttu-id="419be-155">為了完成建立自訂目的地元件，您可能會想要以 `ScriptMain` 類別中提供的下列方法來撰寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-155">To finish creating a custom destination component, you may want to write script in the following methods available in the `ScriptMain` class.</span></span>

1.  <span data-ttu-id="419be-156">覆寫 `AcquireConnections` 方法以連接至外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="419be-156">Override the `AcquireConnections` method to connect to the external data source.</span></span> <span data-ttu-id="419be-157">從連接管理員擷取連接物件，或是必要的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="419be-157">Extract the connection object, or the required connection information, from the connection manager.</span></span>

2.  <span data-ttu-id="419be-158">覆寫 `PreExecute` 方法以準備儲存資料。</span><span class="sxs-lookup"><span data-stu-id="419be-158">Override the `PreExecute` method to prepare to save the data.</span></span> <span data-ttu-id="419be-159">例如，您可能會想要在這個方法中建立並設定 `SqlCommand` 及其參數。</span><span class="sxs-lookup"><span data-stu-id="419be-159">For example, you may want to create and configure a `SqlCommand` and its parameters in this method.</span></span>

3.  <span data-ttu-id="419be-160">使用覆寫的 `ProcessInputRow` 方法，將每個輸入資料列複製到外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="419be-160">Use the overridden `ProcessInputRow` method to copy each input row to the external data source.</span></span> <span data-ttu-id="419be-161">例如，若為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目的地，您可以將資料行值複製到 `SqlCommand` 的參數中，然後針對每個資料列執行此命令一次。</span><span class="sxs-lookup"><span data-stu-id="419be-161">For example, for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] destination, you can copy the column values into the parameters of a `SqlCommand` and execute the command one time for each row.</span></span> <span data-ttu-id="419be-162">若為一般檔案目的地，您可以將每個資料列的值寫入 `StreamWriter`，並以資料行分隔符號隔開這些值。</span><span class="sxs-lookup"><span data-stu-id="419be-162">For a flat file destination, you can write the values for each column to a `StreamWriter`, separating the values by the column delimiter.</span></span>

4.  <span data-ttu-id="419be-163">覆寫 `PostExecute` 方法以中斷外部資料來源的連接 (若有需要的話)，以及執行任何其他所需的清除作業。</span><span class="sxs-lookup"><span data-stu-id="419be-163">Override the `PostExecute` method to disconnect from the external data source, if required, and to perform any other required cleanup.</span></span>

## <a name="examples"></a><span data-ttu-id="419be-164">範例</span><span class="sxs-lookup"><span data-stu-id="419be-164">Examples</span></span>
 <span data-ttu-id="419be-165">下列範例將示範在 `ScriptMain` 類別中所需的程式碼，以建立目的地元件。</span><span class="sxs-lookup"><span data-stu-id="419be-165">The examples that follow demonstrate code that is required in the `ScriptMain` class to create a destination component.</span></span>

> [!NOTE]
>  <span data-ttu-id="419be-166">這些範例會使用範例資料庫中的「 **Person** 」資料表， `AdventureWorks` 並透過資料流程傳遞第一個和第四個數據行，也就是**int \* AddressID**\* 和**Nvarchar (30) City**資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-166">These examples use the **Person.Address** table in the `AdventureWorks` sample database and pass its first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, through the data flow.</span></span> <span data-ttu-id="419be-167">在本章節中的來源、轉換和目的地範例使用相同的資料。</span><span class="sxs-lookup"><span data-stu-id="419be-167">The same data is used in the source, transformation, and destination samples in this section.</span></span> <span data-ttu-id="419be-168">每個範例都會記載其他必要條件與假設。</span><span class="sxs-lookup"><span data-stu-id="419be-168">Additional prerequisites and assumptions are documented for each example.</span></span>

### <a name="adonet-destination-example"></a><span data-ttu-id="419be-169">ADO.NET 目的地範例</span><span class="sxs-lookup"><span data-stu-id="419be-169">ADO.NET Destination Example</span></span>
 <span data-ttu-id="419be-170">這個範例會示範一個目的地元件，它使用現有的 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員，將資料流程的資料儲存至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="419be-170">This example demonstrates a destination component that uses an existing [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to save data from the data flow into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="419be-171">如果您要執行這個範例程式碼，必須依下列方式設定封裝與元件：</span><span class="sxs-lookup"><span data-stu-id="419be-171">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="419be-172">建立一個 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連接管理員，以使用 `SqlClient` 提供者連接到 `AdventureWorks` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="419be-172">Create an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager that uses the `SqlClient` provider to connect to the `AdventureWorks` database.</span></span>

2.  <span data-ttu-id="419be-173">在 `AdventureWorks` 資料庫中執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令，以便建立目的地資料表：</span><span class="sxs-lookup"><span data-stu-id="419be-173">Create a destination table by running the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command in the `AdventureWorks` database:</span></span>

    ```
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,
        [City] [nvarchar](30) NOT NULL)
    ```

3.  <span data-ttu-id="419be-174">將新的指令碼元件加入至資料流程設計師介面，並將它設定為目的地。</span><span class="sxs-lookup"><span data-stu-id="419be-174">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

4.  <span data-ttu-id="419be-175">將上游來源或轉換的輸出連接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的目的地元件</span><span class="sxs-lookup"><span data-stu-id="419be-175">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="419be-176"> (您可以直接將來源連接到目的地，而不需要任何轉換。 ) 此輸出應提供範例資料庫之**Person. Address**資料表的資料 `AdventureWorks` ，其中至少包含**AddressID**和**City**資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-176">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database that contains at least the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="419be-177">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="419be-177">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="419be-178">在 [輸入資料行]  頁面上，選取 **AddressID** 和 **City** 輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-178">On the **Input Columns** page, select the **AddressID** and **City** input columns.</span></span>

6.  <span data-ttu-id="419be-179">在 [輸入及輸出]  頁面上，以更具描述性的名稱重新命名輸入，例如 **MyAddressInput**。</span><span class="sxs-lookup"><span data-stu-id="419be-179">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>

7.  <span data-ttu-id="419be-180">在 [連線管理員]  頁面上，使用名稱 (例如 **MyADONETConnectionManager**) 來新增或建立 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="419be-180">On the **Connection Managers** page, add or create the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager with a name such as **MyADONETConnectionManager**.</span></span>

8.  <span data-ttu-id="419be-181">在 [指令碼]  頁面上，按一下 [編輯指令碼]  ，並輸入以下指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-181">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="419be-182">然後關閉指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="419be-182">Then close the script development environment.</span></span>

9. <span data-ttu-id="419be-183">關閉 [指令碼轉換編輯器]  並執行該範例。</span><span class="sxs-lookup"><span data-stu-id="419be-183">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.Data.SqlClient
...
Public Class ScriptMain
    Inherits UserComponent

    Dim connMgr As IDTSConnectionManager100
    Dim sqlConn As SqlConnection
    Dim sqlCmd As SqlCommand
    Dim sqlParam As SqlParameter

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        connMgr = Me.Connections.MyADONETConnectionManager
        sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)

    End Sub

    Public Overrides Sub PreExecute()

        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _
            "VALUES(@addressid, @city)", sqlConn)
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)
        sqlCmd.Parameters.Add(sqlParam)
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)
        sqlCmd.Parameters.Add(sqlParam)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)
        With sqlCmd
            .Parameters("@addressid").Value = Row.AddressID
            .Parameters("@city").Value = Row.City
            .ExecuteNonQuery()
        End With
    End Sub

    Public Overrides Sub ReleaseConnections()

        connMgr.ReleaseConnection(sqlConn)

    End Sub

End Class
```

```csharp
using System.Data.SqlClient;
public class ScriptMain:
    UserComponent

{
    IDTSConnectionManager100 connMgr;
    SqlConnection sqlConn;
    SqlCommand sqlCmd;
    SqlParameter sqlParam;

    public override void AcquireConnections(object Transaction)
    {

        connMgr = this.Connections.MyADONETConnectionManager;
        sqlConn = (SqlConnection)connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " +
            "VALUES(@addressid, @city)", sqlConn);
        sqlParam = new SqlParameter("@addressid", SqlDbType.Int);
        sqlCmd.Parameters.Add(sqlParam);
        sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);
        sqlCmd.Parameters.Add(sqlParam);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {
        {
            sqlCmd.Parameters["@addressid"].Value = Row.AddressID;
            sqlCmd.Parameters["@city"].Value = Row.City;
            sqlCmd.ExecuteNonQuery();
        }
    }

    public override void ReleaseConnections()
    {

        connMgr.ReleaseConnection(sqlConn);

    }

}
```

### <a name="flat-file-destination-example"></a><span data-ttu-id="419be-184">一般檔案目的地範例</span><span class="sxs-lookup"><span data-stu-id="419be-184">Flat File Destination Example</span></span>
 <span data-ttu-id="419be-185">這個範例會示範一個目的地元件，它使用現有的一般檔案連接管理員，將資料流程的資料儲存至一般檔案。</span><span class="sxs-lookup"><span data-stu-id="419be-185">This example demonstrates a destination component that uses an existing Flat File connection manager to save data from the data flow to a flat file.</span></span>

 <span data-ttu-id="419be-186">如果您要執行這個範例程式碼，必須依下列方式設定封裝與元件：</span><span class="sxs-lookup"><span data-stu-id="419be-186">If you want to run this sample code, you must configure the package and the component as follows:</span></span>

1.  <span data-ttu-id="419be-187">建立連接至目的地檔案的一般檔案連接管理員。</span><span class="sxs-lookup"><span data-stu-id="419be-187">Create a Flat File connection manager that connects to a destination file.</span></span> <span data-ttu-id="419be-188">此檔案不需要存在，因為目的地元件會建立此檔案。</span><span class="sxs-lookup"><span data-stu-id="419be-188">The file does not have to exist; the destination component will create it.</span></span> <span data-ttu-id="419be-189">將目的地檔案設定為包含 **AddressID** 和 **City** 資料行的逗號分隔檔案。</span><span class="sxs-lookup"><span data-stu-id="419be-189">Configure the destination file as a comma-delimited file that contains the **AddressID** and **City** columns.</span></span>

2.  <span data-ttu-id="419be-190">將新的指令碼元件加入至資料流程設計師介面，並將它設定為目的地。</span><span class="sxs-lookup"><span data-stu-id="419be-190">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>

3.  <span data-ttu-id="419be-191">將上游來源或轉換的輸出連接到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中的目的地元件</span><span class="sxs-lookup"><span data-stu-id="419be-191">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="419be-192"> (您可以直接將來源連接到目的地，而不需要任何轉換。 ) 此輸出應提供範例資料庫之**Person. Address**資料表的資料 `AdventureWorks` ，而且應該至少包含**AddressID**和**City**資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-192">(You can connect a source directly to a destination without any transformations.) This output should provide data from the **Person.Address** table of the `AdventureWorks` sample database, and should contain at least the **AddressID** and **City** columns.</span></span>

4.  <span data-ttu-id="419be-193">開啟**指令碼轉換編輯器**。</span><span class="sxs-lookup"><span data-stu-id="419be-193">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="419be-194">在 [輸入資料行]  頁面上，選取 [AddressID]  與 [City]  資料行。</span><span class="sxs-lookup"><span data-stu-id="419be-194">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>

5.  <span data-ttu-id="419be-195">在 [輸入及輸出]  頁面上，以更具描述性的名稱重新命名輸入，例如 **MyAddressInput**。</span><span class="sxs-lookup"><span data-stu-id="419be-195">On the **Inputs and Outputs** page, rename the input with a more descriptive name, such as **MyAddressInput**.</span></span>

6.  <span data-ttu-id="419be-196">在 [連線管理員]  頁面上，使用描述性的名稱 (例如 **MyFlatFileDestConnectionManager**) 來新增或建立一般檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="419be-196">On the **Connection Managers** page, add or create the Flat File connection manager with a descriptive name such as **MyFlatFileDestConnectionManager**.</span></span>

7.  <span data-ttu-id="419be-197">在 [指令碼]  頁面上，按一下 [編輯指令碼]  ，並輸入以下指令碼。</span><span class="sxs-lookup"><span data-stu-id="419be-197">On the **Script** page, click **Edit Script** and enter the script that follows.</span></span> <span data-ttu-id="419be-198">然後關閉指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="419be-198">Then close the script development environment.</span></span>

8.  <span data-ttu-id="419be-199">關閉 [指令碼轉換編輯器]  並執行該範例。</span><span class="sxs-lookup"><span data-stu-id="419be-199">Close the **Script Transformation Editor** and run the sample.</span></span>

```vb
Imports System.IO
...
Public Class ScriptMain
    Inherits UserComponent

    Dim copiedAddressFile As String
    Private textWriter As StreamWriter
    Private columnDelimiter As String = ","

    Public Overrides Sub AcquireConnections(ByVal Transaction As Object)

        Dim connMgr As IDTSConnectionManager100 = _
            Me.Connections.MyFlatFileDestConnectionManager
        copiedAddressFile = CType(connMgr.AcquireConnection(Nothing), String)

    End Sub

    Public Overrides Sub PreExecute()

        textWriter = New StreamWriter(copiedAddressFile, False)

    End Sub

    Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)

        With textWriter
            If Not Row.AddressID_IsNull Then
                .Write(Row.AddressID)
            End If
            .Write(columnDelimiter)
            If Not Row.City_IsNull Then
                .Write(Row.City)
            End If
            .WriteLine()
        End With

    End Sub

    Public Overrides Sub PostExecute()

        textWriter.Close()

    End Sub

End Class
```

```csharp
using System.IO;
public class ScriptMain:
    UserComponent

{
    string copiedAddressFile;
    private StreamWriter textWriter;
    private string columnDelimiter = ",";

    public override void AcquireConnections(object Transaction)
    {

        IDTSConnectionManager100 connMgr = this.Connections.MyFlatFileDestConnectionManager;
        copiedAddressFile = (string) connMgr.AcquireConnection(null);

    }

    public override void PreExecute()
    {

        textWriter = new StreamWriter(copiedAddressFile, false);

    }

    public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)
    {

        {
            if (!Row.AddressID_IsNull)
            {
                textWriter.Write(Row.AddressID);
            }
            textWriter.Write(columnDelimiter);
            if (!Row.City_IsNull)
            {
                textWriter.Write(Row.City);
            }
            textWriter.WriteLine();
        }

    }

    public override void PostExecute()
    {

        textWriter.Close();

    }

}
```

<span data-ttu-id="419be-200">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="419be-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="419be-201">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="419be-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="419be-202">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="419be-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="419be-203">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="419be-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="419be-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="419be-204">See Also</span></span>
 <span data-ttu-id="419be-205">[使用腳本元件建立來源](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)[開發自訂目的地元件](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span><span class="sxs-lookup"><span data-stu-id="419be-205">[Creating a Source with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) [Developing a Custom Destination Component](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)</span></span>


