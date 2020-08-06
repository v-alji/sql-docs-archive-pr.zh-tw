---
title: 變數視窗 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.variables.f1
helpviewer_keywords:
- Variables Window dialog box
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffd6da67386291c14ebf588da9a1cf8f399214b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597899"
---
# <a name="variables-window"></a><span data-ttu-id="8c35c-102">變數視窗</span><span class="sxs-lookup"><span data-stu-id="8c35c-102">Variables Window</span></span>
  <span data-ttu-id="8c35c-103">使用 [變數]  視窗，即可建立和修改使用者定義的變數，並檢視系統變數。</span><span class="sxs-lookup"><span data-stu-id="8c35c-103">Use the **Variables** window to create and modify user-defined variables and view system variables.</span></span>  
  
 <span data-ttu-id="8c35c-104">依預設，[變數] 視窗位於 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中 [SSIS 設計師] 的 [連線管理員] 區域下方。</span><span class="sxs-lookup"><span data-stu-id="8c35c-104">By default, the **Variables** window is located below the **Connection Managers** area in the SSIS Designer, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8c35c-105">如果您未看見 [變數] 視窗，請按一下 [SSIS] 功能表上的 [變數] 來顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="8c35c-105">If you don't see the **Variables** window, click **Variables** on the **SSIS** menu to display the window.</span></span>  
  
 <span data-ttu-id="8c35c-106">您可以將 View.Variables 命令對應到您在 [選項] 對話方塊的 [鍵盤] 頁面中所選擇的組合鍵，以選擇性地顯示 [變數] 視窗。</span><span class="sxs-lookup"><span data-stu-id="8c35c-106">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c35c-107">`Name` 和 `Namespace` 屬性的值必須以 Unicode Standard 2.0 中定義的字母字元或底線 (_) 為開頭。</span><span class="sxs-lookup"><span data-stu-id="8c35c-107">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="8c35c-108">後續的字元可以是 Unicode Standard 2.0 中定義的字母或數字，或是底線 (\_)。</span><span class="sxs-lookup"><span data-stu-id="8c35c-108">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c35c-109">選項。</span><span class="sxs-lookup"><span data-stu-id="8c35c-109">Options</span></span>  
 <span data-ttu-id="8c35c-110">**新增變數**</span><span class="sxs-lookup"><span data-stu-id="8c35c-110">**Add Variable**</span></span>  
 <span data-ttu-id="8c35c-111">加入使用者自訂變數。</span><span class="sxs-lookup"><span data-stu-id="8c35c-111">Add a user-defined variable.</span></span>  
  
 <span data-ttu-id="8c35c-112">**移動變數**</span><span class="sxs-lookup"><span data-stu-id="8c35c-112">**Move Variable**</span></span>  
 <span data-ttu-id="8c35c-113">按一下清單中的變數，然後按一下 [移動變數]  以變更變數範圍。</span><span class="sxs-lookup"><span data-stu-id="8c35c-113">Click a variable in the list, and then click **Move Variable** to change the variable scope.</span></span> <span data-ttu-id="8c35c-114">在 [選取新的範圍]  對話方塊中，選取封裝或容器、工作或是封裝中的事件處理常式，以變更變數範圍。</span><span class="sxs-lookup"><span data-stu-id="8c35c-114">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
 <span data-ttu-id="8c35c-115">如需變數範圍的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="8c35c-115">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="8c35c-116">**刪除變數**</span><span class="sxs-lookup"><span data-stu-id="8c35c-116">**Delete Variable**</span></span>  
 <span data-ttu-id="8c35c-117">從清單中選取變數，然後按一下 [刪除變數]  。</span><span class="sxs-lookup"><span data-stu-id="8c35c-117">Select a variable from the list, and then click **Delete Variable**.</span></span>  
  
 <span data-ttu-id="8c35c-118">**方格選項**</span><span class="sxs-lookup"><span data-stu-id="8c35c-118">**Grid Options**</span></span>  
 <span data-ttu-id="8c35c-119">按一下以開啟 [變數方格選項]  對話方塊，在其中您可以變更資料行選取範圍以及將篩選套用到 [變數]  視窗。</span><span class="sxs-lookup"><span data-stu-id="8c35c-119">Click to open the **Variable Grid Options** dialog box where you can change the column selection and apply filters to the **Variables** window.</span></span> <span data-ttu-id="8c35c-120">如需詳細資訊，請參閱 [變數方格選項](../../2014/integration-services/variable-grid-options.md)。</span><span class="sxs-lookup"><span data-stu-id="8c35c-120">For more information, see [Variable Grid Options](../../2014/integration-services/variable-grid-options.md).</span></span>  
  
 `Name`  
 <span data-ttu-id="8c35c-121">檢視變數名稱。</span><span class="sxs-lookup"><span data-stu-id="8c35c-121">View the variable name.</span></span> <span data-ttu-id="8c35c-122">您可以更新使用者定義變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c35c-122">You can update the name for user-defined variables.</span></span>  
  
 <span data-ttu-id="8c35c-123">**範圍**</span><span class="sxs-lookup"><span data-stu-id="8c35c-123">**Scope**</span></span>  
 <span data-ttu-id="8c35c-124">檢視變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="8c35c-124">View the scope of the variable.</span></span> <span data-ttu-id="8c35c-125">變數會具有整個封裝的範圍，或是容器或工作的範圍。</span><span class="sxs-lookup"><span data-stu-id="8c35c-125">A variable has either the scope of the entire package, or the scope of a container or task.</span></span> <span data-ttu-id="8c35c-126">變數的範圍必須足夠，讓需要讀取或設定其值的任何其他工作或元件都看得到該變數。</span><span class="sxs-lookup"><span data-stu-id="8c35c-126">The scope of the variable must be sufficient so that the variable is visible to any other tasks or components that need to read or set its value.</span></span>  
  
 <span data-ttu-id="8c35c-127">您可以透過按一下變數，然後按一下 [變數]\*\*\*\* 視窗中的 [移動變數]\*\*\*\* 來變更範圍。</span><span class="sxs-lookup"><span data-stu-id="8c35c-127">You can change the scope by clicking the variable and then clicking **Move Variable** in the **Variables** window.</span></span>  
  
 <span data-ttu-id="8c35c-128">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="8c35c-128">**Data Type**</span></span>  
 <span data-ttu-id="8c35c-129">檢視變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8c35c-129">View the data type of the variable.</span></span> <span data-ttu-id="8c35c-130">您可以從使用者定義變數的清單中選取資料類型。</span><span class="sxs-lookup"><span data-stu-id="8c35c-130">You can select a data type from the list for user-defined variables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c35c-131">若您將運算式指派給變數，則無法變更資料類型。</span><span class="sxs-lookup"><span data-stu-id="8c35c-131">If you assign an expression to the variable, you cannot change the data type.</span></span>  
  
 <span data-ttu-id="8c35c-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="8c35c-132">**Value**</span></span>  
 <span data-ttu-id="8c35c-133">檢視變數值。</span><span class="sxs-lookup"><span data-stu-id="8c35c-133">View the variable value.</span></span> <span data-ttu-id="8c35c-134">您可以更新使用者定義變數的值。</span><span class="sxs-lookup"><span data-stu-id="8c35c-134">You can update the value for user-defined variables.</span></span> <span data-ttu-id="8c35c-135">此值可以是常值或運算式，而且此值可以是多行字串。</span><span class="sxs-lookup"><span data-stu-id="8c35c-135">This value can be a literal or an expression, and the value can be a multi-line string.</span></span> <span data-ttu-id="8c35c-136">若要將運算式指派給變數，請按一下 [變數]\*\*\*\* 視窗中 [運算式]\*\*\*\* 資料行旁邊的省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="8c35c-136">To assign an expression to the variable, click the ellipse button that is next to the **Expression** column in the **Variables** window.</span></span>  
  
 `Namespace`  
 <span data-ttu-id="8c35c-137">檢視命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="8c35c-137">View the namespace name.</span></span> <span data-ttu-id="8c35c-138">使用者自訂變數一開始是在**使用者**命名空間中建立，但是您可以變更欄位中的命名空間名稱 `Namespace` 。</span><span class="sxs-lookup"><span data-stu-id="8c35c-138">User-defined variables are initially created in the **User** namespace, but you can change the namespace name in the `Namespace` field.</span></span> <span data-ttu-id="8c35c-139">若要顯示此資料行，請按一下 [方格選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c35c-139">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="8c35c-140">**引發變更事件**</span><span class="sxs-lookup"><span data-stu-id="8c35c-140">**Raise Change Event**</span></span>  
 <span data-ttu-id="8c35c-141">指出某個值變更時，是否要引發 `OnVariableValueChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="8c35c-141">Indicate whether to raise the `OnVariableValueChanged` event when a value changes.</span></span> <span data-ttu-id="8c35c-142">您可以更新使用者定義及系統變數的值。</span><span class="sxs-lookup"><span data-stu-id="8c35c-142">You can update the value for user-defined and system variables.</span></span> <span data-ttu-id="8c35c-143">依預設，[變數]\*\*\*\* 視窗不會列出此資料行。</span><span class="sxs-lookup"><span data-stu-id="8c35c-143">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="8c35c-144">若要顯示此資料行，請按一下 [方格選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c35c-144">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="8c35c-145">**說明**</span><span class="sxs-lookup"><span data-stu-id="8c35c-145">**Description**</span></span>  
 <span data-ttu-id="8c35c-146">檢視變數描述。</span><span class="sxs-lookup"><span data-stu-id="8c35c-146">View the variable description.</span></span> <span data-ttu-id="8c35c-147">您可以變更使用者定義變數的描述。</span><span class="sxs-lookup"><span data-stu-id="8c35c-147">You can change the description for user-defined variables.</span></span> <span data-ttu-id="8c35c-148">依預設，[變數]\*\*\*\* 視窗不會列出此資料行。</span><span class="sxs-lookup"><span data-stu-id="8c35c-148">By default, the **Variables** window does not list this column.</span></span> <span data-ttu-id="8c35c-149">若要顯示此資料行，請按一下 [方格選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c35c-149">To display this column, click **Grid Options**.</span></span>  
  
 <span data-ttu-id="8c35c-150">**運算式**</span><span class="sxs-lookup"><span data-stu-id="8c35c-150">**Expression**</span></span>  
 <span data-ttu-id="8c35c-151">檢視指派給變數的運算式。</span><span class="sxs-lookup"><span data-stu-id="8c35c-151">View the expression assigned to the variable.</span></span> <span data-ttu-id="8c35c-152">若要指派運算式，請按一下省略符號按鈕。</span><span class="sxs-lookup"><span data-stu-id="8c35c-152">To assign an expression, click the ellipse button.</span></span>  
  
 <span data-ttu-id="8c35c-153">若您將運算式指派給變數，變數旁邊會顯示特殊圖示標記。</span><span class="sxs-lookup"><span data-stu-id="8c35c-153">If you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="8c35c-154">此特殊圖示標記也會顯示在已經設定運算式的連接管理員及工作旁邊。</span><span class="sxs-lookup"><span data-stu-id="8c35c-154">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c35c-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c35c-155">See Also</span></span>  
 <span data-ttu-id="8c35c-156">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="8c35c-156">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="8c35c-157">[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="8c35c-157">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="8c35c-158">[Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="8c35c-158">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="8c35c-159">產生套件執行的傾印檔案</span><span class="sxs-lookup"><span data-stu-id="8c35c-159">Generating Dump Files for Package Execution</span></span>](troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
