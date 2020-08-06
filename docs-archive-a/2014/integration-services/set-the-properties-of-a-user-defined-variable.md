---
title: 設定使用者定義變數的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf53be469e3d377f7efb379f78e85e31b26767b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709737"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a><span data-ttu-id="e93e0-102">設定使用者定義變數的屬性</span><span class="sxs-lookup"><span data-stu-id="e93e0-102">Set the Properties of a User-Defined Variable</span></span>
  <span data-ttu-id="e93e0-103">若要在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中設定使用者定義變數的屬性，您可以使用下列其中一項功能：</span><span class="sxs-lookup"><span data-stu-id="e93e0-103">To set the properties of a user-defined variable in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can use one of the following features:</span></span>  
  
-   <span data-ttu-id="e93e0-104">[變數] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e93e0-104">Variables window.</span></span>  
  
-   <span data-ttu-id="e93e0-105">[屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e93e0-105">Properties window.</span></span> <span data-ttu-id="e93e0-106">[屬性]\*\*\*\* 視窗會列出屬性，以供您設定 [變數]\*\*\*\* 視窗中無法使用的變數：Description、EvaluateAsExpression、Expression、ReadOnly、ValueType 和 IncludeInDebugDump。</span><span class="sxs-lookup"><span data-stu-id="e93e0-106">The **Properties** window lists properties for configuring variables that are not available in the **Variables** window: Description, EvaluateAsExpression, Expression, ReadOnly, ValueType, and IncludeInDebugDump.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e93e0-107">也提供一組無法更新屬性的系統變數，但屬性 RaiseChangedEvent 除外。</span><span class="sxs-lookup"><span data-stu-id="e93e0-107">also provides a set of system variables whose properties cannot be updated, with the exception of the RaiseChangedEvent property.</span></span>  
  
 <span data-ttu-id="e93e0-108">**設定變數上的運算式**</span><span class="sxs-lookup"><span data-stu-id="e93e0-108">**Setting Expressions on Variables**</span></span>  
  
 <span data-ttu-id="e93e0-109">當您使用 [屬性]\*\*\*\* 視窗設定使用者定義變數的運算式時：</span><span class="sxs-lookup"><span data-stu-id="e93e0-109">When you use the **Properties** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="e93e0-110">變數的值可以由 Value 或 Expression 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="e93e0-110">The value of a variable can be set by the Value or the Expression property.</span></span> <span data-ttu-id="e93e0-111">根據預設，EvaluateAsExpression 屬性會設定為 `False` ，而變數的值會由 value 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="e93e0-111">By default, the EvaluateAsExpression property is set to `False` and the value of the variable is set by the Value property.</span></span> <span data-ttu-id="e93e0-112">若要使用運算式來設定值，您必須先將 EvaluateAsExpression 設定為 `True` ，然後在 expression 屬性中提供運算式。</span><span class="sxs-lookup"><span data-stu-id="e93e0-112">To use an expression to set the value, you must first set EvaluateAsExpression to `True`, and then provide an expression in the Expression property.</span></span> <span data-ttu-id="e93e0-113">Value 屬性會自動設為運算式的評估結果。</span><span class="sxs-lookup"><span data-stu-id="e93e0-113">The Value property is automatically set to the evaluation result of the expression.</span></span>  
  
-   <span data-ttu-id="e93e0-114">ValueType 屬性包含 Value 屬性中之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e93e0-114">The ValueType property contains the data type of the value in the Value property.</span></span> <span data-ttu-id="e93e0-115">運算式設定 Value 之後，ValueType 就會自動更新為與運算式之評估結果相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e93e0-115">When Value is set by an expression, ValueType is automatically updated to a data type that is compatible with the evaluation result of the expression.</span></span> <span data-ttu-id="e93e0-116">例如，如果 Value 包含0且 ValueType 屬性包含**Int32** ，然後您將 Expression 設為 GETDATE ( # A1，Value 就會包含目前的日期和時間，且 ValueType 會設定為 `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="e93e0-116">For example, if Value contains 0 and ValueType property contains **Int32** and you then set Expression to GETDATE(), Value contains the current date and time and ValueType is set to `DateTime`.</span></span>  
  
-   <span data-ttu-id="e93e0-117">透過變數的 [屬性]\*\*\*\* 視窗，可以存取 [運算式產生器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e93e0-117">The **Properties** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="e93e0-118">您可使用此工具建立、驗證和評估運算式。</span><span class="sxs-lookup"><span data-stu-id="e93e0-118">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="e93e0-119">如需詳細資訊，請參閱[運算式產生器](expressions/expression-builder.md)和 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e93e0-119">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="e93e0-120">當您使用 [變數]\*\*\*\* 視窗設定使用者定義變數的運算式時：</span><span class="sxs-lookup"><span data-stu-id="e93e0-120">When you use the **Variables** window to set expressions on a user-defined variable:</span></span>  
  
-   <span data-ttu-id="e93e0-121">若要使用運算式設定變數值，請先確認變數資料類型是否與運算式的評估結果相容，然後在 `Expression` [**變數**] 視窗的資料行中提供運算式。</span><span class="sxs-lookup"><span data-stu-id="e93e0-121">To use an expression to set the variable value, first confirm that the variable data type is compatible with the evaluation result of the expression and then provide an expression in the `Expression` column of the **Variables** window.</span></span> <span data-ttu-id="e93e0-122">[**屬性**] 視窗中的 [EvaluateAsExpression] 屬性會自動設為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="e93e0-122">The EvaluateAsExpression property in the **Properties** window is automatically set to `True`.</span></span>  
  
-   <span data-ttu-id="e93e0-123">當您將運算式指派給變數時，會在變數旁邊顯示特殊圖示標記。</span><span class="sxs-lookup"><span data-stu-id="e93e0-123">When you assign an expression to a variable, a special icon marker displays next to the variable.</span></span> <span data-ttu-id="e93e0-124">此特殊圖示標記也會顯示在已經設定運算式的連接管理員及工作旁邊。</span><span class="sxs-lookup"><span data-stu-id="e93e0-124">This special icon marker also displays next to connection managers and tasks that have expressions set on them.</span></span>  
  
-   <span data-ttu-id="e93e0-125">透過變數的 [變數]\*\*\*\* 視窗，可以存取 [運算式產生器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e93e0-125">The **Variables** window for the variable provides access to the **Expression Builder** dialog box.</span></span> <span data-ttu-id="e93e0-126">您可使用此工具建立、驗證和評估運算式。</span><span class="sxs-lookup"><span data-stu-id="e93e0-126">You can use this tool to build, validate, and evaluate expressions.</span></span> <span data-ttu-id="e93e0-127">如需詳細資訊，請參閱[運算式產生器](expressions/expression-builder.md)和 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e93e0-127">For more information, see [Expression Builder](expressions/expression-builder.md) and [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="e93e0-128">在 [**變數**] 和 [**屬性**] 視窗中，如果您將運算式指派給變數，並將 `EvaluateAsExpression` 設定為 `True` ，則無法變更變數資料類型。</span><span class="sxs-lookup"><span data-stu-id="e93e0-128">In both the **Variables** and **Properties** window, if you assign an expression to the variable, and `EvaluateAsExpression` is set to `True`, you cannot change the variable data type.</span></span>  
  
 <span data-ttu-id="e93e0-129">**設定命名空間及名稱屬性**</span><span class="sxs-lookup"><span data-stu-id="e93e0-129">**Setting the Namespace and Name Properties**</span></span>  
  
 <span data-ttu-id="e93e0-130">`Name` 和 `Namespace` 屬性的值必須以 Unicode Standard 2.0 中定義的字母字元或底線 (_) 為開頭。</span><span class="sxs-lookup"><span data-stu-id="e93e0-130">The values of the `Name` and `Namespace` properties must begin with an alphabetic character letter as defined by the Unicode Standard 2.0, or an underscore (_).</span></span> <span data-ttu-id="e93e0-131">後續的字元可以是 Unicode Standard 2.0 中定義的字母或數字，或是底線 (\_)。</span><span class="sxs-lookup"><span data-stu-id="e93e0-131">Subsequent characters can be letters or numbers as defined in the Unicode Standard 2.0, or the underscore (\_).</span></span>  
  
## <a name="using-the-variables-window-to-set-properties"></a><span data-ttu-id="e93e0-132">使用變數視窗來設定屬性</span><span class="sxs-lookup"><span data-stu-id="e93e0-132">Using the Variables Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a><span data-ttu-id="e93e0-133">使用變數視窗來設定變數的屬性</span><span class="sxs-lookup"><span data-stu-id="e93e0-133">To set the properties of a variable by using the Variables window</span></span>  
  
1.  <span data-ttu-id="e93e0-134">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="e93e0-134">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e93e0-135">在 [方案總管] 中，以滑鼠右鍵按一下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="e93e0-135">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e93e0-136">在 **[SSIS]** 功能表上，按一下 **變數**。</span><span class="sxs-lookup"><span data-stu-id="e93e0-136">On the **SSIS** menu, click **Variables**.</span></span>  
  
     <span data-ttu-id="e93e0-137">您可以將 View.Variables 命令對應到您在 [選項]\*\*\*\* 對話方塊的 [鍵盤]\*\*\*\* 頁面中所選擇的組合鍵，以選擇性地顯示 [變數]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="e93e0-137">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="e93e0-138">選擇性地在 [變數]\*\*\*\* 視窗中按一下 [方格選項]\*\*\*\*，然後選取要在 [變數]\*\*\*\* 視窗中顯示的資料行，並選取要套用到此變數清單的篩選。</span><span class="sxs-lookup"><span data-stu-id="e93e0-138">Optionally, in the **Variables** window click **Grid Options**, and then select the columns to appear in the **Variables** window and select the filters to apply to the list of variables.</span></span>  
  
5.  <span data-ttu-id="e93e0-139">選取清單中的變數，然後更新 [資料類型]、[] `Name` 、[ **Data Type** `Value` `Namespace` **引發變更事件**]、[**描述**] 和 [資料 `Expression` 行] 中的值。</span><span class="sxs-lookup"><span data-stu-id="e93e0-139">Select the variable in the list, and then update values in the `Name`, **Data Type**, `Value`, `Namespace`, **Raise Change Event**, **Description,** and `Expression` columns.</span></span>  
  
6.  <span data-ttu-id="e93e0-140">選擇清單中的變數，然後按一下 [移動變數]\*\*\*\* 以變更範圍。</span><span class="sxs-lookup"><span data-stu-id="e93e0-140">Select the variable in the list, and then click **Move Variable** to change the scope.</span></span>  
  
7.  <span data-ttu-id="e93e0-141">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="e93e0-141">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="using-the-properties-window-to-set-properties"></a><span data-ttu-id="e93e0-142">使用屬性視窗來設定屬性</span><span class="sxs-lookup"><span data-stu-id="e93e0-142">Using the Properties Window to Set Properties</span></span>  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a><span data-ttu-id="e93e0-143">使用屬性視窗來設定變數的屬性</span><span class="sxs-lookup"><span data-stu-id="e93e0-143">To set the properties of a variable by using the Properties window</span></span>  
  
1.  <span data-ttu-id="e93e0-144">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="e93e0-144">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="e93e0-145">在 [方案總管] 中，以滑鼠右鍵按一下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="e93e0-145">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="e93e0-146">在 [檢視]  功能表上，按一下 [屬性視窗]  。</span><span class="sxs-lookup"><span data-stu-id="e93e0-146">On the **View** menu, click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="e93e0-147">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 [封裝總管]\*\*\*\* 索引標籤，並展開 [封裝] 節點。</span><span class="sxs-lookup"><span data-stu-id="e93e0-147">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Package Explorer** tab and expand the Package node.</span></span>  
  
5.  <span data-ttu-id="e93e0-148">若要修改具有封裝範圍的變數，請展開 [變數] 節點；否則，展開 [事件處理常式] 或 [可執行檔] 節點，直到找到包含想要修改之變數的 [變數] 節點為止。</span><span class="sxs-lookup"><span data-stu-id="e93e0-148">To modify variables with package scope, expand the Variables node; otherwise, expand the Event Handlers or Executables nodes until you locate the Variables node that contains the variable that you want to modify.</span></span>  
  
6.  <span data-ttu-id="e93e0-149">按一下想要修改其屬性的變數。</span><span class="sxs-lookup"><span data-stu-id="e93e0-149">Click the variable whose properties you want to modify.</span></span>  
  
7.  <span data-ttu-id="e93e0-150">在 [屬性]\*\*\*\* 視窗中，更新讀取/寫入變數屬性。</span><span class="sxs-lookup"><span data-stu-id="e93e0-150">In the **Properties** window, update the read/write variable properties.</span></span> <span data-ttu-id="e93e0-151">有些使用者自訂變數的屬性為讀取/唯讀。</span><span class="sxs-lookup"><span data-stu-id="e93e0-151">Some properties are read/read only for user-defined variables.</span></span>  
  
     <span data-ttu-id="e93e0-152">如需屬性的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="e93e0-152">For more information about the properties, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
8.  <span data-ttu-id="e93e0-153">若要儲存已更新的封裝，請按一下 [檔案]  功能表上的 [儲存選取項目]  。</span><span class="sxs-lookup"><span data-stu-id="e93e0-153">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93e0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e93e0-154">See Also</span></span>  
 <span data-ttu-id="e93e0-155">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e93e0-155">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="e93e0-156">[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="e93e0-156">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 [<span data-ttu-id="e93e0-157">加入、刪除、變更封裝中使用者定義變數的範圍</span><span class="sxs-lookup"><span data-stu-id="e93e0-157">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
