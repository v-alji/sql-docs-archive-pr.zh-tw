---
title: 在子封裝中使用變數和參數的值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28561db91e5e924d8b25f9c7be7a4a51c6c315ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597905"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a><span data-ttu-id="2a0b0-102">在子封裝中使用變數和參數的值</span><span class="sxs-lookup"><span data-stu-id="2a0b0-102">Use the Values of Variables and Parameters in a Child Package</span></span>
  <span data-ttu-id="2a0b0-103">此程序描述如何建立使用父變數組態類型的封裝組態。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-103">This procedure describes how to create a package configuration that uses the parent variable configuration type.</span></span> <span data-ttu-id="2a0b0-104">此組態類型可讓從父封裝執行的子封裝存取父變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-104">This configuration type enables a child package that is run from a parent package to access a variable in the parent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a0b0-105">您也可以設定 [執行封裝工作] 將父封裝變數或參數 (或專案參數) 對應到子封裝參數，以將值傳遞到子封裝。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-105">You can also pass values to a child package by configuring the Execute Package Task to map parent package variables or parameters, or project parameters, to child package parameters.</span></span> <span data-ttu-id="2a0b0-106">如需詳細資訊，請參閱 [執行封裝工作](control-flow/execute-package-task.md)。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-106">For more information, see [Execute Package Task](control-flow/execute-package-task.md).</span></span>  
  
 <span data-ttu-id="2a0b0-107">在子封裝中建立封裝組態之前，並不需要在父封裝中建立變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-107">It is not necessary to create the variable in the parent package before you create the package configuration in the child package.</span></span> <span data-ttu-id="2a0b0-108">您可以隨時將變數加入父封裝中，但是必須使用封裝組態中父變數的確切名稱。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-108">You can add the variable to the parent package at any time, but you must use the exact name of the parent variable in the package configuration.</span></span> <span data-ttu-id="2a0b0-109">不過，在可以更新組態的子封裝中必須包含現有的變數，您才可以建立父變數組態。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-109">However, before you can create a parent variable configuration, there must be an existing variable in the child package that the configuration can update.</span></span> <span data-ttu-id="2a0b0-110">如需加入和設定變數的詳細資訊，請參閱 [加入、刪除、變更封裝中使用者定義變數的範圍](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-110">For more information about adding and configuring variables, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
 <span data-ttu-id="2a0b0-111">父變數組態使用之父封裝中變數的範圍可以設定為「執行封裝」工作、擁有該工作的容器，或是封裝。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-111">The scope of the variable in the parent package that is used in a parent variable configuration can be set to the Execute Package task, to the container that has the task, or to the package.</span></span> <span data-ttu-id="2a0b0-112">如果封裝中定義了多個名稱相同的變數，則會使用最接近「執行封裝」工作範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-112">If multiple variables with the same name are defined in a package, the variable that is closest in scope to the Execute Package task is used.</span></span> <span data-ttu-id="2a0b0-113">最接近「執行封裝」工作的範圍就是工作本身。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-113">The closest scope to the Execute Package task is the task itself.</span></span>  
  
### <a name="to-add-a-variable-to-a-parent-package"></a><span data-ttu-id="2a0b0-114">若要將變數加入父封裝</span><span class="sxs-lookup"><span data-stu-id="2a0b0-114">To add a variable to a parent package</span></span>  
  
1.  <span data-ttu-id="2a0b0-115">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要加入用來傳遞到子封裝之變數的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a variable to pass to a child package.</span></span>  
  
2.  <span data-ttu-id="2a0b0-116">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2a0b0-117">在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，若要定義變數的範圍，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="2a0b0-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to define the scope of the variable, do one of the following:</span></span>  
  
    -   <span data-ttu-id="2a0b0-118">若要將範圍設為封裝，請按一下 [控制流程]  索引標籤之設計介面上的任意位置。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-118">To set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
    -   <span data-ttu-id="2a0b0-119">若要將範圍設定為「執行封裝」工作的父容器，請按一下該容器。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-119">To set the scope to a parent container of the Execute Package task, click the container.</span></span>  
  
    -   <span data-ttu-id="2a0b0-120">若要將範圍設定為「執行封裝」，請按一下該工作。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-120">To set the scope to the Execute Package task, click the task.</span></span>  
  
4.  <span data-ttu-id="2a0b0-121">加入及設定變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-121">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a0b0-122">選取與變數所要儲存之資料相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-122">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="2a0b0-123">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-123">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-variable-to-a-child-package"></a><span data-ttu-id="2a0b0-124">若要將變數加入子封裝</span><span class="sxs-lookup"><span data-stu-id="2a0b0-124">To add a variable to a child package</span></span>  
  
1.  <span data-ttu-id="2a0b0-125">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要加入父變數組態之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-125">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add a parent variable configuration.</span></span>  
  
2.  <span data-ttu-id="2a0b0-126">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="2a0b0-127">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，若要將範圍設定為封裝，請按一下 [控制流程]  索引標籤之設計介面上的任意位置。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-127">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, to set the scope to the package, click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="2a0b0-128">加入及設定變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-128">Add and configure a variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2a0b0-129">選取與變數所要儲存之資料相容的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-129">Select a data type that is compatible with the data that the variable will store.</span></span>  
  
5.  <span data-ttu-id="2a0b0-130">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-130">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a><span data-ttu-id="2a0b0-131">若要將父封裝組態加入子封裝</span><span class="sxs-lookup"><span data-stu-id="2a0b0-131">To add a parent package configuration to a child package</span></span>  
  
1.  <span data-ttu-id="2a0b0-132">如果子封裝尚未開啟，請在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中開啟它。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-132">If it is not already open, open the child package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="2a0b0-133">按一下 [控制流程]\*\*\*\* 索引標籤之設計介面中的任意位置。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-133">Click anywhere on the design surface of the **Control Flow** tab.</span></span>  
  
3.  <span data-ttu-id="2a0b0-134">在 [SSIS]  功能表上，按一下 [封裝組態]  。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-134">On the **SSIS** menu, click **Package Configurations**.</span></span>  
  
4.  <span data-ttu-id="2a0b0-135">在 [封裝組態組合管理]\*\*\*\* 對話方塊中，選取 [啟用封裝組態]\*\*\*\*，然後按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-135">In the **Package Configuration Organizer** dialog box, select **Enable package configuration**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="2a0b0-136">在 [套件設定向導] 的 [歡迎使用] 頁面上，按 **[下一步]。**</span><span class="sxs-lookup"><span data-stu-id="2a0b0-136">On the welcome page of the Package Configuration Wizard, click **Next.**</span></span>  
  
6.  <span data-ttu-id="2a0b0-137">在 [選取組態類型] 頁面的 [組態類型]\*\*\*\* 清單中，選取 [父封裝變數]\*\*\*\*，然後執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="2a0b0-137">On the Select Configuration Type page, in the **Configuration type** list, select **Parent package variable** and do one of the following:</span></span>  
  
    -   <span data-ttu-id="2a0b0-138">選取 [直接指定組態設定]\*\*\*\*，然後在 [父變數]\*\*\*\* 方塊中，提供組態中所要使用之父封裝的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-138">Select **Specify configuration settings directly**, and then in the **Parent variable** box, provide the name of the variable in the parent package to use in the configuration.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="2a0b0-139">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-139">Variable names are case sensitive.</span></span>  
  
    -   <span data-ttu-id="2a0b0-140">選取 [組態位置儲存在環境變數中]\*\*\*\*，然後在 [環境變數清單]\*\*\*\* 中選取包含變數名稱的環境變數。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-140">Select or **Configuration location is stored in an environment variable,** and then in the **Environment variable list**, select the environmentvariable that contains the name of the variable.</span></span>  
  
7.  <span data-ttu-id="2a0b0-141">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-141">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="2a0b0-142">在 [選取目標屬性] 頁面上，依序展開 [變數]\*\*\*\* 節點及要設定之變數的 [屬性]\*\*\*\* 節點，然後按一下組態所要設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-142">On the Select Target Property page, expand the **Variable** node, and expand the **Properties** node of the variable to configure, and then click the property to be set by the configuration.</span></span>  
  
9. <span data-ttu-id="2a0b0-143">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-143">Click **Next**.</span></span>  
  
10. <span data-ttu-id="2a0b0-144">(選擇性) 在 [正在完成精靈] 頁面上，修改組態的預設名稱並檢閱組態資訊。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-144">On the Completing the Wizard page, optionally, modify the default name of the configuration and review the configuration information.</span></span>  
  
11. <span data-ttu-id="2a0b0-145">按一下 [完成]\*\*\*\* 以完成精靈，並返回 [封裝組態組合管理]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-145">Click **Finish** to complete the wizard and return to the **Package Configuration Organizer** dialog box.</span></span>  
  
12. <span data-ttu-id="2a0b0-146">在 [封裝組態組合管理]\*\*\*\* 對話方塊中，[組態]\*\*\*\* 方塊會列出新的組態。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-146">In the **Package Configuration Organizer** dialog box, the **Configuration** box lists the new configuration.</span></span>  
  
13. <span data-ttu-id="2a0b0-147">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="2a0b0-147">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0b0-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a0b0-148">See Also</span></span>  
 <span data-ttu-id="2a0b0-149">[套件設定](../../2014/integration-services/package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="2a0b0-149">[Package Configurations](../../2014/integration-services/package-configurations.md) </span></span>  
 <span data-ttu-id="2a0b0-150">[建立套件設定](../../2014/integration-services/create-package-configurations.md) </span><span class="sxs-lookup"><span data-stu-id="2a0b0-150">[Create Package Configurations](../../2014/integration-services/create-package-configurations.md) </span></span>  
 <span data-ttu-id="2a0b0-151">[Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="2a0b0-151">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="2a0b0-152">在封裝中使用變數</span><span class="sxs-lookup"><span data-stu-id="2a0b0-152">Use Variables in Packages</span></span>](../../2014/integration-services/use-variables-in-packages.md)  
  
  
