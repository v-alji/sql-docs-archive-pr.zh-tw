---
title: 指令碼元件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponentdetails.f1
helpviewer_keywords:
- Script transformation
- scripts [Integration Services], transformations
- Script component [Integration Services], about Script component
- Script component [Integration Services]
ms.assetid: 131c2d0c-2e33-4785-94af-ada5c049821e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af8e500e399b0f69a7e34c9e2e01c74d83256107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710774"
---
# <a name="script-component"></a><span data-ttu-id="e2c39-102">指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e2c39-102">Script Component</span></span>
  <span data-ttu-id="e2c39-103">指令碼元件可裝載指令碼，並讓封裝包含及執行自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-103">The Script component hosts script and enables a package to include and run custom script code.</span></span> <span data-ttu-id="e2c39-104">您可在封裝中使用指令碼元件以達到下列目的：</span><span class="sxs-lookup"><span data-stu-id="e2c39-104">You can use the Script component in packages for the following purposes:</span></span>  
  
-   <span data-ttu-id="e2c39-105">套用多個轉換至資料，而不使用資料流程中的多個轉換。</span><span class="sxs-lookup"><span data-stu-id="e2c39-105">Apply multiple transformations to data instead of using multiple transformations in the data flow.</span></span> <span data-ttu-id="e2c39-106">例如，指令碼可以加總兩個資料行中的值，然後計算總和的平均。</span><span class="sxs-lookup"><span data-stu-id="e2c39-106">For example, a script can add the values in two columns and then calculate the average of the sum.</span></span>  
  
-   <span data-ttu-id="e2c39-107">存取現有 .NET 組件中的商務規則。</span><span class="sxs-lookup"><span data-stu-id="e2c39-107">Access business rules in an existing .NET assembly.</span></span> <span data-ttu-id="e2c39-108">例如，指令碼可以套用商務規則，以指定在 `Income` 資料行中有效的值範圍。</span><span class="sxs-lookup"><span data-stu-id="e2c39-108">For example, a script can apply a business rule that specifies the range of values that are valid in an `Income` column.</span></span>  
  
-   <span data-ttu-id="e2c39-109">除了 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 運算式文法所提供的函數和運算子外，也可以使用自訂公式和函數。</span><span class="sxs-lookup"><span data-stu-id="e2c39-109">Use custom formulas and functions in addition to the functions and operators that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expression grammar provides.</span></span> <span data-ttu-id="e2c39-110">例如，使用 LUHN 公式驗證信用卡號碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-110">For example, validate credit card numbers that use the LUHN formula.</span></span>  
  
-   <span data-ttu-id="e2c39-111">驗證資料行資料並略過包含無效資料的記錄。</span><span class="sxs-lookup"><span data-stu-id="e2c39-111">Validate column data and skip records that contain invalid data.</span></span> <span data-ttu-id="e2c39-112">例如，指令碼可評估合理的郵資金額，並略過金額過高或過低的記錄。</span><span class="sxs-lookup"><span data-stu-id="e2c39-112">For example, a script can assess the reasonableness of a postage amount and skip records with extremely high or low amounts.</span></span>  
  
 <span data-ttu-id="e2c39-113">指令碼元件提供簡單快速的方式，用來將自訂函數包含在資料流程中。</span><span class="sxs-lookup"><span data-stu-id="e2c39-113">The Script component provides an easy and quick way to include custom functions in a data flow.</span></span> <span data-ttu-id="e2c39-114">不過，如果您計劃在多個封裝中重複使用指令碼，應該考慮以程式設計自訂元件，而不要使用指令碼元件。</span><span class="sxs-lookup"><span data-stu-id="e2c39-114">However, if you plan to reuse the script code in multiple packages, you should consider programming a custom component instead of using the Script component.</span></span> <span data-ttu-id="e2c39-115">如需詳細資訊，請參閱 [開發自訂資料流程元件](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c39-115">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2c39-116">如果指令碼元件包含指令碼，而該指令碼嘗試讀取 NULL 的資料行值，則當您執行封裝時，此指令碼元件就會失敗。</span><span class="sxs-lookup"><span data-stu-id="e2c39-116">If the Script component contains a script that tries to read the value of a column that is NULL, the Script component fails when you run the package.</span></span> <span data-ttu-id="e2c39-117">我們建議您讓您的指令碼使用 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> 方法來判斷資料行是否為 NULL，然後再嘗試讀取資料行值。</span><span class="sxs-lookup"><span data-stu-id="e2c39-117">We recommend that your script use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer.IsNull%2A> method to determine whether the column is NULL before trying to read the column value.</span></span>  
  
 <span data-ttu-id="e2c39-118">指令碼元件可當做來源、轉換或目的地使用。</span><span class="sxs-lookup"><span data-stu-id="e2c39-118">The Script component can be used as a source, a transformation, or a destination.</span></span> <span data-ttu-id="e2c39-119">此元件支援一個輸入和多個輸出。</span><span class="sxs-lookup"><span data-stu-id="e2c39-119">This component supports one input and multiple outputs.</span></span> <span data-ttu-id="e2c39-120">視元件的使用方式而定，可支援輸入、輸出或兩者。</span><span class="sxs-lookup"><span data-stu-id="e2c39-120">Depending on how the component is used, it supports either an input or outputs or both.</span></span> <span data-ttu-id="e2c39-121">指令碼是由輸入或輸出中的每個資料列所叫用。</span><span class="sxs-lookup"><span data-stu-id="e2c39-121">The script is invoked by every row in the input or output.</span></span>  
  
-   <span data-ttu-id="e2c39-122">如果當做來源使用，指令碼元件可支援多個輸出。</span><span class="sxs-lookup"><span data-stu-id="e2c39-122">If used as a source, the Script component supports multiple outputs.</span></span>  
  
-   <span data-ttu-id="e2c39-123">如果當做轉換使用，指令碼元件可支援一個輸入和多個輸出。</span><span class="sxs-lookup"><span data-stu-id="e2c39-123">If used as a transformation, the Script component supports one input and multiple outputs.</span></span>  
  
-   <span data-ttu-id="e2c39-124">如果當做目的地使用，指令碼元件可支援一個輸入。</span><span class="sxs-lookup"><span data-stu-id="e2c39-124">If used as a destination, the Script component supports one input.</span></span>  
  
 <span data-ttu-id="e2c39-125">指令碼元件不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="e2c39-125">The Script component does not support error outputs.</span></span>  
  
 <span data-ttu-id="e2c39-126">確定指令碼元件是適用於您封裝的選擇之後，您必須設定輸入和輸出、開發該元件使用的指令碼，以及設定元件本身。</span><span class="sxs-lookup"><span data-stu-id="e2c39-126">After you decide that the Script component is the appropriate choice for your package, you have to configure the inputs and outputs, develop the script that the component uses, and configure the component itself.</span></span>  
  
## <a name="understanding-the-script-component-modes"></a><span data-ttu-id="e2c39-127">了解指令碼元件模式</span><span class="sxs-lookup"><span data-stu-id="e2c39-127">Understanding the Script Component Modes</span></span>  
 <span data-ttu-id="e2c39-128">在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計工具」中，指令碼元件有兩個模式：中繼資料設計模式與程式碼設計模式。</span><span class="sxs-lookup"><span data-stu-id="e2c39-128">In the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, the Script component has two modes: metadata-design mode and code-design mode.</span></span> <span data-ttu-id="e2c39-129">在中繼資料設計模式中，您可以加入和修改指令碼元件輸入和輸出，但是不能編寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-129">In metadata-design mode, you can add and modify the Script component inputs and outputs, but you cannot write code.</span></span> <span data-ttu-id="e2c39-130">設定好所有輸入和輸出後，您可以切換到程式碼設計模式編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-130">After all the inputs and outputs are configured, you switch to code-design mode to write the script.</span></span> <span data-ttu-id="e2c39-131">指令碼元件會自動從輸入和輸出的中繼資料產生基底程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-131">The Script component automatically generates base code from the metadata of the inputs and outputs.</span></span> <span data-ttu-id="e2c39-132">如果您在指令碼元件產生基底程式碼後變更中繼資料，您的程式碼可能無法再編譯，因為更新的基底程式碼可能與您的程式碼不相容。</span><span class="sxs-lookup"><span data-stu-id="e2c39-132">If you change the metadata after the Script component generates the base code, your code may no longer compile because the updated base code may be incompatible with your code.</span></span>  
  
## <a name="writing-the-script-that-the-component-uses"></a><span data-ttu-id="e2c39-133">撰寫元件使用的指令碼</span><span class="sxs-lookup"><span data-stu-id="e2c39-133">Writing the Script that the Component Uses</span></span>  
 <span data-ttu-id="e2c39-134">指令碼元件使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 當作撰寫指令碼的環境。</span><span class="sxs-lookup"><span data-stu-id="e2c39-134">The Script component uses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts.</span></span> <span data-ttu-id="e2c39-135">您可以從 **[指令碼轉換編輯器]** 存取 VSTA。</span><span class="sxs-lookup"><span data-stu-id="e2c39-135">You access VSTA from the **Script Transformation Editor**.</span></span> <span data-ttu-id="e2c39-136">如需詳細資訊，請參閱 [指令碼轉換編輯器 &#40;指令碼頁面&#41;](../../script-transformation-editor-script-page.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c39-136">For more information, see [Script Transformation Editor &#40;Script Page&#41;](../../script-transformation-editor-script-page.md).</span></span>  
  
 <span data-ttu-id="e2c39-137">指令碼元件提供 VSTA 專案，其中包含自動產生的類別，該類別名為 ScriptMain 且代表元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e2c39-137">The Script component provides a VSTA project that includes an auto-generated class, named ScriptMain, that represents the component metadata.</span></span> <span data-ttu-id="e2c39-138">例如，如果指令碼元件當做具有三個輸出的轉換使用，則 ScriptMain 會包含每個輸出的方法。</span><span class="sxs-lookup"><span data-stu-id="e2c39-138">For example, if the Script component is used as a transformation that has three outputs, ScriptMain includes a method for each output.</span></span> <span data-ttu-id="e2c39-139">ScriptMain 是指令碼的進入點。</span><span class="sxs-lookup"><span data-stu-id="e2c39-139">ScriptMain is the entry point to the script.</span></span>  
  
 <span data-ttu-id="e2c39-140">VSTA 包含 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 環境的所有標準功能，例如色彩編碼的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 編輯器、IntelliSense 和「物件瀏覽器」。</span><span class="sxs-lookup"><span data-stu-id="e2c39-140">VSTA includes all the standard features of the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] editor, IntelliSense, and Object Browser.</span></span> <span data-ttu-id="e2c39-141">指令碼元件所使用的指令碼會儲存在封裝定義中，</span><span class="sxs-lookup"><span data-stu-id="e2c39-141">The script that the Script component uses is stored in the package definition.</span></span> <span data-ttu-id="e2c39-142">當您要設計封裝時，指令碼會暫時寫入專案檔。</span><span class="sxs-lookup"><span data-stu-id="e2c39-142">When you are designing the package, the script code is temporarily written to a project file.</span></span>  
  
 <span data-ttu-id="e2c39-143">VSTA 支援 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 和 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 程式語言。</span><span class="sxs-lookup"><span data-stu-id="e2c39-143">VSTA supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic programming languages.</span></span>  
  
 <span data-ttu-id="e2c39-144">如需有關如何以程式設計方式編寫指令碼元件的詳細資訊，請參閱＜ [以指令碼元件來擴充資料流程](script-component.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e2c39-144">For information about how to program the Script component, see [Extending the Data Flow with the Script Component](script-component.md).</span></span> <span data-ttu-id="e2c39-145">如需有關如何將指令碼元件設為來源、轉換或目的地的特定資訊，請參閱＜ [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e2c39-145">For more specific information about how to configure the Script component as a source, transformation, or destination, see [Developing Specific Types of Script Components](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span> <span data-ttu-id="e2c39-146">如需其他範例 (例如示範如何使用指令碼元件的 ODBC 目的地)，請參閱＜ [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e2c39-146">For additional examples such as an ODBC destination that demonstrate the use of the Script component, see [Additional Script Component Examples](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2c39-147">不像在舊版中可以指出是否已經先行編譯指令碼，所有指令碼在 [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 和更新的版本中都會先行編譯。</span><span class="sxs-lookup"><span data-stu-id="e2c39-147">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="e2c39-148">指令碼經過先行編譯後，在執行階段不會載入語言引擎，因此封裝的執行速度會更快。</span><span class="sxs-lookup"><span data-stu-id="e2c39-148">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="e2c39-149">不過，先行編譯的二進位檔案會使用大量的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="e2c39-149">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-component"></a><span data-ttu-id="e2c39-150">設定指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e2c39-150">Configuring the Script Component</span></span>  
 <span data-ttu-id="e2c39-151">您可以利用下列方式設定指令碼元件：</span><span class="sxs-lookup"><span data-stu-id="e2c39-151">You can configure the Script component in the following ways:</span></span>  
  
-   <span data-ttu-id="e2c39-152">選取要參考的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="e2c39-152">Select the input columns to reference.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2c39-153">當您使用「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計工具」時，僅能設定一個輸入。</span><span class="sxs-lookup"><span data-stu-id="e2c39-153">You can configure only one input when you use the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
-   <span data-ttu-id="e2c39-154">提供元件執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="e2c39-154">Provide the script that the component runs.</span></span>  
  
-   <span data-ttu-id="e2c39-155">指定指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="e2c39-155">Specify the script language.</span></span>  
  
-   <span data-ttu-id="e2c39-156">提供唯讀和讀取/寫入變數的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="e2c39-156">Provide comma-separated lists of read-only and read/write variables.</span></span>  
  
-   <span data-ttu-id="e2c39-157">加入更多輸出，並加入指令碼指派的目標輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="e2c39-157">Add more outputs, and add output columns to which the script assigns.</span></span>  
  
 <span data-ttu-id="e2c39-158">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e2c39-158">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-component-in-the-designer"></a><span data-ttu-id="e2c39-159">在設計工具中設定指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e2c39-159">Configuring the Script Component in the Designer</span></span>  
 <span data-ttu-id="e2c39-160">如需有關可以在 **[指令碼轉換編輯器]** 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e2c39-160">For more information about the properties that you can set in the **Script Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e2c39-161">指令碼轉換編輯器 &#40;輸入資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c39-161">Script Transformation Editor &#40;Input Columns Page&#41;</span></span>](../../script-transformation-editor-input-columns-page.md)  
  
-   [<span data-ttu-id="e2c39-162">指令碼轉換編輯器 &#40;輸入及輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c39-162">Script Transformation Editor &#40;Inputs and Outputs Page&#41;</span></span>](../../script-transformation-editor-inputs-and-outputs-page.md)  
  
-   [<span data-ttu-id="e2c39-163">指令碼轉換編輯器 &#40;指令碼頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c39-163">Script Transformation Editor &#40;Script Page&#41;</span></span>](../../script-transformation-editor-script-page.md)  
  
-   [<span data-ttu-id="e2c39-164">指令碼轉換編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="e2c39-164">Script Transformation Editor &#40;Connection Managers Page&#41;</span></span>](../../script-transformation-editor-connection-managers-page.md)  
  
 <span data-ttu-id="e2c39-165">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="e2c39-165">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e2c39-166">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="e2c39-166">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
### <a name="configuring-the-script-component-programmatically"></a><span data-ttu-id="e2c39-167">以程式設計的方式設定指令碼元件</span><span class="sxs-lookup"><span data-stu-id="e2c39-167">Configuring the Script Component Programmatically</span></span>  
 <span data-ttu-id="e2c39-168">如需有關可以在 **[屬性]** 視窗中或以程式設計的方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e2c39-168">For more information about the properties that you can set in the **Properties** window or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e2c39-169">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e2c39-169">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="e2c39-170">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="e2c39-170">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="e2c39-171">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e2c39-171">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e2c39-172">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="e2c39-172">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="e2c39-173">相關內容</span><span class="sxs-lookup"><span data-stu-id="e2c39-173">Related Content</span></span>  
 [<span data-ttu-id="e2c39-174">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="e2c39-174">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
 [<span data-ttu-id="e2c39-175">以指令碼元件來擴充資料流程</span><span class="sxs-lookup"><span data-stu-id="e2c39-175">Extending the Data Flow with the Script Component</span></span>](script-component.md)  
  
  
