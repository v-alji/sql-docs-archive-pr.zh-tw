---
title: 建立參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.parameterwindow.f1
ms.assetid: cd5d675b-dd5d-49cc-8b1f-dc717a973f99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a26ae08c08a32b0593be8c9a2777b7cfe9c884fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592791"
---
# <a name="create-parameters"></a><span data-ttu-id="dfa9b-102">Create Parameters</span><span class="sxs-lookup"><span data-stu-id="dfa9b-102">Create Parameters</span></span>
  <span data-ttu-id="dfa9b-103">您可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 來建立專案參數和封裝參數。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-103">You use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create project parameters and package parameters.</span></span> <span data-ttu-id="dfa9b-104">下列程序會提供建立封裝/專案參數的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-104">The following procedures provide step-by-step instructions for creating package/project parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dfa9b-105">如果要將使用舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 建立的專案轉換為專案部署模型，可以使用 **[Integration Services 專案轉換精靈]** ，根據組態建立參數。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-105">If you are converting a project that you created using an earlier version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] to the project deployment model, you can use the **Integration Services Project Conversion Wizard** to create parameters based on configurations.</span></span> <span data-ttu-id="dfa9b-106">如需詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-106">For more information, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
### <a name="to-create-package-parameters"></a><span data-ttu-id="dfa9b-107">若要建立封裝參數</span><span class="sxs-lookup"><span data-stu-id="dfa9b-107">To create package parameters</span></span>  
  
1.  <span data-ttu-id="dfa9b-108">開啟 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中的封裝，然後按一下 SSIS 設計師中的 **[參數]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-108">Open the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], and then click the **Parameters** tab in the SSIS Designer.</span></span>  
  
     <span data-ttu-id="dfa9b-109">![套件的 [參數] 索引標籤](media/denali-package-parameters.gif "套件的 [參數] 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="dfa9b-109">![Package Parameters Tab](media/denali-package-parameters.gif "Package Parameters Tab")</span></span>  
  
2.  <span data-ttu-id="dfa9b-110">按一下工具列上的 **[加入參數]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-110">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="dfa9b-111">![新增工具列按鈕](media/denali-parameter-add.gif "新增工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="dfa9b-111">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
3.  <span data-ttu-id="dfa9b-112">在清單本身或 **[屬性]** 視窗中，輸入 **[名稱]**、 **[資料類型]**、 **[值]**、 **[區分]** 以及 **[必要]** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-112">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties in the list itself or in the **Properties** window.</span></span> <span data-ttu-id="dfa9b-113">下表描述這些屬性。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-113">The following table describes these properties.</span></span>  
  
    |<span data-ttu-id="dfa9b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="dfa9b-114">Property</span></span>|<span data-ttu-id="dfa9b-115">描述</span><span class="sxs-lookup"><span data-stu-id="dfa9b-115">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="dfa9b-116">名稱</span><span class="sxs-lookup"><span data-stu-id="dfa9b-116">Name</span></span>|<span data-ttu-id="dfa9b-117">參數名稱。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-117">The name of the parameter.</span></span>|  
    |<span data-ttu-id="dfa9b-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="dfa9b-118">Data type</span></span>|<span data-ttu-id="dfa9b-119">參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-119">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="dfa9b-120">預設值</span><span class="sxs-lookup"><span data-stu-id="dfa9b-120">Default value</span></span>|<span data-ttu-id="dfa9b-121">在設計時指派的參數預設值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-121">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="dfa9b-122">這也稱為設計預設值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-122">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="dfa9b-123">敏感</span><span class="sxs-lookup"><span data-stu-id="dfa9b-123">Sensitive</span></span>|<span data-ttu-id="dfa9b-124">敏感性參數值會在目錄中加密，以 Transact-SQL 或 SQL Server Management Studio 來檢視時，會顯示為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-124">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="dfa9b-125">必要</span><span class="sxs-lookup"><span data-stu-id="dfa9b-125">Required</span></span>|<span data-ttu-id="dfa9b-126">必須先指定一個值 (非設計預設值)，封裝才能執行。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-126">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="dfa9b-127">描述</span><span class="sxs-lookup"><span data-stu-id="dfa9b-127">Description</span></span>|<span data-ttu-id="dfa9b-128">為方便維護，使用參數的描述。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-128">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="dfa9b-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，於 Visual Studio 的 [屬性] 視窗中設定參數描述 (已在適用的參數視窗中選取參數)。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="dfa9b-130">當您將專案部署至目錄時，會再多幾個屬性與專案相關聯。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-130">When you deploy a project to the catalog, several more properties become associated with the project.</span></span> <span data-ttu-id="dfa9b-131">若要查看目錄中所有參數的所有屬性，請使用 [catalog.object_parameters &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) 檢視。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-131">To see all properties for all parameters in the catalog, use the [catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) view.</span></span>  
  
4.  <span data-ttu-id="dfa9b-132">儲存專案以儲存參數的變更。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-132">Save the project to save changes to parameters.</span></span> <span data-ttu-id="dfa9b-133">參數值會儲存在專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-133">Parameter values are stored in the project file.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="dfa9b-134">您可以在清單中就地編輯，也可以使用 [屬性]\*\*\*\* 視窗來修改參數屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-134">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="dfa9b-135">您可以使用 [刪除] **(X)** 工具列按鈕來刪除參數。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-135">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="dfa9b-136">您可以使用最後一個工具列按鈕，為僅在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中執行包時使用的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-136">Using the last toolbar button, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dfa9b-137">如果您在沒有開啟 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中專案的情況下重新開啟封裝檔案，[參數]\*\*\*\* 索引標籤將會是空的，而且遭到停用。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-137">If you re-open the package file without opening the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the **Parameters** tab will be empty and disabled.</span></span>  
  
### <a name="to-create-project-parameters"></a><span data-ttu-id="dfa9b-138">若要建立專案參數</span><span class="sxs-lookup"><span data-stu-id="dfa9b-138">To create project parameters</span></span>  
  
1.  <span data-ttu-id="dfa9b-139">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-139">Open the project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="dfa9b-140">以滑鼠右鍵按一下方案總管中的 **Project.params**，然後按一下 [開啟]\*\*\*\* \(或) 按兩下 **Project.params** 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-140">Right-click **Project.params** in Solution Explorer, and then click **Open** (OR) double-click **Project.params** to open it.</span></span>  
  
     <span data-ttu-id="dfa9b-141">![專案參數視窗](media/denali-project-parameters.gif "專案參數視窗")</span><span class="sxs-lookup"><span data-stu-id="dfa9b-141">![Project Parameters Window](media/denali-project-parameters.gif "Project Parameters Window")</span></span>  
  
3.  <span data-ttu-id="dfa9b-142">按一下工具列上的 **[加入參數]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-142">Click the **Add Parameter** button on the toolbar.</span></span>  
  
     <span data-ttu-id="dfa9b-143">![新增工具列按鈕](media/denali-parameter-add.gif "新增工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="dfa9b-143">![Add Toolbar Button](media/denali-parameter-add.gif "Add Toolbar Button")</span></span>  
  
4.  <span data-ttu-id="dfa9b-144">輸入 **[名稱]**、 **[資料類型]**、 **[值]**、 **[區分]** 以及 **[必要]** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-144">Enter values for the **Name**, **Data Type**, **Value**, **Sensitive**, and **Required** properties.</span></span>  
  
    |<span data-ttu-id="dfa9b-145">屬性</span><span class="sxs-lookup"><span data-stu-id="dfa9b-145">Property</span></span>|<span data-ttu-id="dfa9b-146">描述</span><span class="sxs-lookup"><span data-stu-id="dfa9b-146">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="dfa9b-147">名稱</span><span class="sxs-lookup"><span data-stu-id="dfa9b-147">Name</span></span>|<span data-ttu-id="dfa9b-148">參數名稱。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-148">The name of the parameter.</span></span>|  
    |<span data-ttu-id="dfa9b-149">資料類型</span><span class="sxs-lookup"><span data-stu-id="dfa9b-149">Data type</span></span>|<span data-ttu-id="dfa9b-150">參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-150">The data type of the parameter.</span></span>|  
    |<span data-ttu-id="dfa9b-151">預設值</span><span class="sxs-lookup"><span data-stu-id="dfa9b-151">Default value</span></span>|<span data-ttu-id="dfa9b-152">在設計時指派的參數預設值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-152">The default value for the parameter assigned at design time.</span></span> <span data-ttu-id="dfa9b-153">這也稱為設計預設值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-153">This is also known as the design default.</span></span>|  
    |<span data-ttu-id="dfa9b-154">敏感</span><span class="sxs-lookup"><span data-stu-id="dfa9b-154">Sensitive</span></span>|<span data-ttu-id="dfa9b-155">敏感性參數值會在目錄中加密，以 Transact-SQL 或 SQL Server Management Studio 來檢視時，會顯示為 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-155">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>|  
    |<span data-ttu-id="dfa9b-156">必要</span><span class="sxs-lookup"><span data-stu-id="dfa9b-156">Required</span></span>|<span data-ttu-id="dfa9b-157">必須先指定一個值 (非設計預設值)，封裝才能執行。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-157">Requires that a value, other than the design default, is specified before the package can execute.</span></span>|  
    |<span data-ttu-id="dfa9b-158">描述</span><span class="sxs-lookup"><span data-stu-id="dfa9b-158">Description</span></span>|<span data-ttu-id="dfa9b-159">為方便維護，使用參數的描述。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-159">For maintainability, the description of the parameter.</span></span> <span data-ttu-id="dfa9b-160">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，於 Visual Studio 的 [屬性] 視窗中設定參數描述 (已在適用的參數視窗中選取參數)。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-160">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], set the parameter description in the Visual Studio Properties window when the parameter is selected in the applicable parameters window.</span></span>|  
  
5.  <span data-ttu-id="dfa9b-161">儲存專案以儲存參數的變更。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-161">Save the project to save changes to parameters.</span></span> <span data-ttu-id="dfa9b-162">參數值儲存在專案檔案的組態中。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-162">Parameter values are stored in configurations in the project file.</span></span> <span data-ttu-id="dfa9b-163">儲存專案檔案即可將參數值的任何變更認可到磁碟。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-163">Save the project file to commit to disk any changes in the parameter values.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="dfa9b-164">您可以在清單中就地編輯，也可以使用 [屬性]\*\*\*\* 視窗來修改參數屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-164">You can in-place edit in the list or use the **Properties** window to modify the values of parameter properties.</span></span> <span data-ttu-id="dfa9b-165">您可以使用 [刪除] **(X)** 工具列按鈕來刪除參數。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-165">You can delete a parameter by using the **Delete (X)** toolbar button.</span></span> <span data-ttu-id="dfa9b-166">使用最後一個工具列按鈕開啟 **[管理參數值]** 對話方塊，針對僅在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中執行封裝時使用的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="dfa9b-166">Using the last toolbar button to open the **Manage Parameter Values** dialog box, you can specify a value for a parameter that is used only when you execute the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa9b-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfa9b-167">See Also</span></span>  
 [<span data-ttu-id="dfa9b-168">Integration Services &#40;SSIS&#41; 參數</span><span class="sxs-lookup"><span data-stu-id="dfa9b-168">Integration Services &#40;SSIS&#41; Parameters</span></span>](integration-services-ssis-package-and-project-parameters.md)  
  
  
