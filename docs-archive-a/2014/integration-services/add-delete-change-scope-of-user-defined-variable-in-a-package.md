---
title: 加入、刪除、變更封裝中使用者定義變數的範圍 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a7e5980fc7f730c69ef886e4e80760cfbdc9e4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595254"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a><span data-ttu-id="cb111-102">加入、刪除、變更封裝中使用者定義變數的範圍</span><span class="sxs-lookup"><span data-stu-id="cb111-102">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>
  <span data-ttu-id="cb111-103">這些程序描述如何使用 [變數]\*\*\*\* 視窗，在封裝中加入、刪除及變更使用者定義變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="cb111-103">These procedures describe how to add, delete, and change the scope of a user-defined variable in a package by using the **Variables** window.</span></span>  
  
 <span data-ttu-id="cb111-104">如需變數範圍的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="cb111-104">For more information about variable scope, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="cb111-105">也提供了讓系統資訊在執行階段可用的系統變數，而且可以在封裝和事件處理常式等容器中使用。</span><span class="sxs-lookup"><span data-stu-id="cb111-105">also provides system variables that make system information available at run time and can be used in containers such as packages and event handlers.</span></span> <span data-ttu-id="cb111-106">您無法刪除系統變數。</span><span class="sxs-lookup"><span data-stu-id="cb111-106">You cannot delete system variables.</span></span>  
  
### <a name="to-add-a-variable"></a><span data-ttu-id="cb111-107">加入變數</span><span class="sxs-lookup"><span data-stu-id="cb111-107">To add a variable</span></span>  
  
1.  <span data-ttu-id="cb111-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟您要使用的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="cb111-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="cb111-109">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="cb111-109">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cb111-110">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，若要定義變數的範圍，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="cb111-110">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="cb111-111">若要將範圍設為封裝，請按一下 [控制流程]  索引標籤之設計介面上的任意位置。</span><span class="sxs-lookup"><span data-stu-id="cb111-111">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="cb111-112">若要將範圍設為事件處理常式，在 [事件處理常式]\*\*\*\* 索引標籤的設計介面上，選取可執行檔和事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="cb111-112">To set the scope to an event handler, select an executable and an event handler on the design surface of the **Event Handler** tab.</span></span>  
  
    -   <span data-ttu-id="cb111-113">若要將範圍設為工作或容器，在 [控制流程]\*\*\*\* 索引標籤或 [事件處理常式]\*\*\*\* 索引標籤的設計介面上，按一下工作或容器。</span><span class="sxs-lookup"><span data-stu-id="cb111-113">To set the scope to a task or container, on the design surface of the **Control Flow** tab or the **Event Handler** tab, click a task or container.</span></span>  
  
4.  <span data-ttu-id="cb111-114">在 **[SSIS]** 功能表上，按一下 **變數**。</span><span class="sxs-lookup"><span data-stu-id="cb111-114">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cb111-115">您可以將 View.Variables 命令對應到您在 [選項]\*\*\*\* 對話方塊的 [鍵盤]\*\*\*\* 頁面中所選擇的組合鍵，以選擇性地顯示 [變數]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="cb111-115">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
5.  <span data-ttu-id="cb111-116">在 [**變數**] 視窗中，按一下 [**加入變數**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="cb111-116">In the **Variables** window, click the **Add Variable** icon.</span></span> <span data-ttu-id="cb111-117">新變數便會加入清單。</span><span class="sxs-lookup"><span data-stu-id="cb111-117">The new variable is added to the list.</span></span>  
  
6.  <span data-ttu-id="cb111-118">選擇性地按一下**方格選項**圖示，在 [變數方格選項]\*\*\*\* 對話方塊中選取要顯示的其他資料行，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb111-118">Optionally, click the **Grid Options** icon, select additional columns to show in the **Variables Grid Options** dialog box, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="cb111-119">選擇性地設定變數屬性。</span><span class="sxs-lookup"><span data-stu-id="cb111-119">Optionally, set the variable properties.</span></span> <span data-ttu-id="cb111-120">如需詳細資訊，請參閱 [設定使用者定義變數的屬性](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)定義。</span><span class="sxs-lookup"><span data-stu-id="cb111-120">For more information, see [Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).</span></span>  
  
8.  <span data-ttu-id="cb111-121">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="cb111-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-variable"></a><span data-ttu-id="cb111-122">刪除變數</span><span class="sxs-lookup"><span data-stu-id="cb111-122">To delete a variable</span></span>  
  
1.  <span data-ttu-id="cb111-123">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="cb111-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="cb111-124">在 [方案總管] 中，以滑鼠右鍵按一下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="cb111-124">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cb111-125">在 **[SSIS]** 功能表上，按一下 **變數**。</span><span class="sxs-lookup"><span data-stu-id="cb111-125">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cb111-126">您可以將 View.Variables 命令對應到您在 [選項]\*\*\*\* 對話方塊的 [鍵盤]\*\*\*\* 頁面中所選擇的組合鍵，以選擇性地顯示 [變數]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="cb111-126">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="cb111-127">選取要刪除的變數，然後按一下 [刪除變數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb111-127">Select the variable to delete, and then click **Delete Variable**.</span></span>  
  
     <span data-ttu-id="cb111-128">如果您在 [變數] 視窗中看不到變數，請按一下 [**方格選項**]，然後選取 [**顯示所有範圍的變數**]。</span><span class="sxs-lookup"><span data-stu-id="cb111-128">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="cb111-129">如果 [確認刪除變數]\*\*\*\* 對話方塊開啟，按一下 [是]\*\*\*\* 確認。</span><span class="sxs-lookup"><span data-stu-id="cb111-129">If the **Confirm Deletion of Variables** dialog box opens, click **Yes** to confirm.</span></span>  
  
6.  <span data-ttu-id="cb111-130">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="cb111-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-change-the-scope-of-a-variable"></a><span data-ttu-id="cb111-131">變更變數的範圍</span><span class="sxs-lookup"><span data-stu-id="cb111-131">To change the scope of a variable</span></span>  
  
1.  <span data-ttu-id="cb111-132">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="cb111-132">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="cb111-133">在 [方案總管] 中，以滑鼠右鍵按一下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="cb111-133">In Solution Explorer, right-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="cb111-134">在 **[SSIS]** 功能表上，按一下 **變數**。</span><span class="sxs-lookup"><span data-stu-id="cb111-134">On the **SSIS** menu, click **Variables**.</span></span> <span data-ttu-id="cb111-135">您可以將 View.Variables 命令對應到您在 [選項]\*\*\*\* 對話方塊的 [鍵盤]\*\*\*\* 頁面中所選擇的組合鍵，以選擇性地顯示 [變數]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="cb111-135">You can optionally display the **Variables** window by mapping the View.Variables command to a key combination of your choosing on the **Keyboard** page of the **Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="cb111-136">選取變數，然後按一下 [移動變數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb111-136">Select the variable and then click **Move Variable**.</span></span>  
  
     <span data-ttu-id="cb111-137">如果您在 [變數] 視窗中看不到變數，請按一下 [**方格選項**]，然後選取 [**顯示所有範圍的變數**]。</span><span class="sxs-lookup"><span data-stu-id="cb111-137">If you don't see the variable in the Variables window, click **Grid Options** and then select **Show variables of all scopes**.</span></span>  
  
5.  <span data-ttu-id="cb111-138">在 [選取新的範圍]\*\*\*\* 對話方塊中，選取封裝或容器、工作或是封裝中的事件處理常式，以變更變數範圍。</span><span class="sxs-lookup"><span data-stu-id="cb111-138">In the **Select New Scope** dialog box, select the package or a container, task, or event handler in the package, to change the variable scope.</span></span>  
  
6.  <span data-ttu-id="cb111-139">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="cb111-139">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb111-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb111-140">See Also</span></span>  
 <span data-ttu-id="cb111-141">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cb111-141">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="cb111-142">[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="cb111-142">[Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="cb111-143">[設定使用者定義變數的屬性](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span><span class="sxs-lookup"><span data-stu-id="cb111-143">[Set the Properties of a User-Defined Variable](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md) </span></span>  
 [<span data-ttu-id="cb111-144">在子封裝中使用變數和參數的值</span><span class="sxs-lookup"><span data-stu-id="cb111-144">Use the Values of Variables and Parameters in a Child Package</span></span>](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
