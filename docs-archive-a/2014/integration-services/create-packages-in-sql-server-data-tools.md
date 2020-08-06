---
title: 在 SQL Server Data Tools 中建立封裝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594608"
---
# <a name="create-packages-in-sql-server-data-tools"></a><span data-ttu-id="8d227-102">在 SQL Server 資料工具中建立封裝</span><span class="sxs-lookup"><span data-stu-id="8d227-102">Create Packages in SQL Server Data Tools</span></span>
  <span data-ttu-id="8d227-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 設計師在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 中建立的封裝將儲存到檔案系統。</span><span class="sxs-lookup"><span data-stu-id="8d227-103">The packages that you create in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer are saved to the file system.</span></span> <span data-ttu-id="8d227-104">若要將封裝儲存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或封裝存放區，您必須儲存該封裝的複本。</span><span class="sxs-lookup"><span data-stu-id="8d227-104">To save a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store, you need to save a copy of the package.</span></span> <span data-ttu-id="8d227-105">如需詳細資訊，請參閱 [儲存封裝的複本](../../2014/integration-services/save-a-copy-of-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="8d227-105">For more information, see [Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md).</span></span>  
  
 <span data-ttu-id="8d227-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，您可以使用下列其中一個方法來建立新的封裝：</span><span class="sxs-lookup"><span data-stu-id="8d227-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can create a new package by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="8d227-107">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所包含的封裝範本。</span><span class="sxs-lookup"><span data-stu-id="8d227-107">Use the package template that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes.</span></span>  
  
-   <span data-ttu-id="8d227-108">使用自訂範本</span><span class="sxs-lookup"><span data-stu-id="8d227-108">Use a custom template</span></span>  
  
     <span data-ttu-id="8d227-109">若要使用自訂封裝做為建立新封裝的範本，您只需將自訂封裝複製到 DataTransformationItems 資料夾即可。</span><span class="sxs-lookup"><span data-stu-id="8d227-109">To use custom packages as templates for creating new packages, you simply copy them to the DataTransformationItems folder.</span></span> <span data-ttu-id="8d227-110">依預設，這個資料夾位於 C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject。</span><span class="sxs-lookup"><span data-stu-id="8d227-110">By default, this folder is in C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
-   <span data-ttu-id="8d227-111">複製現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-111">Copy an existing package.</span></span>  
  
     <span data-ttu-id="8d227-112">如果現有的封裝包含您想重複使用的功能，您可以從其他封裝複製及貼上物件，以加快建立控制流程和新封裝內之資料流程的速度。</span><span class="sxs-lookup"><span data-stu-id="8d227-112">If existing packages include functionality that you want to reuse, you can build the control flow and data flows in the new package more quickly by copying and pasting objects from other packages.</span></span> <span data-ttu-id="8d227-113">如需在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中使用複製及貼上功能的詳細資訊，請參閱 [重複使用封裝物件](reuse-of-package-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="8d227-113">For more information about using copy and paste in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Reuse of Package Objects](reuse-of-package-objects.md).</span></span>  
  
     <span data-ttu-id="8d227-114">如果您透過複製現有封裝或使用自訂封裝做為範本的方式來建立新封裝，將一併複製現有封裝的名稱和 GUID。</span><span class="sxs-lookup"><span data-stu-id="8d227-114">If you create a new package by copying an existing package or by using a custom package as a template, the name and the GUID of the existing package are copied as well.</span></span> <span data-ttu-id="8d227-115">您應該更新這個新封裝的名稱和 GUID，以協助區分新封裝與其複製來源封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-115">You should update the name and the GUID of the new package to help differentiate it from the package from which it was copied.</span></span> <span data-ttu-id="8d227-116">例如，如果封裝具有相同的 GUID，在識別記錄資料所屬的封裝時就會發生困難。</span><span class="sxs-lookup"><span data-stu-id="8d227-116">For example, if packages have the same GUID, it is more difficult to identify the package to which log data belongs.</span></span> <span data-ttu-id="8d227-117">您可以使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [屬性] 視窗，重新產生 `ID` 屬性中的 GUID 並且更新 `Name` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8d227-117">You can regenerate the GUID in the `ID` property and update the value of the `Name` property by using the Properties window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8d227-118">如需詳細資訊，請參閱 [設定封裝屬性](set-package-properties.md) 和 [dtutil 公用程式](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="8d227-118">For more information, see [Set Package Properties](set-package-properties.md) and [dtutil Utility](dtutil-utility.md).</span></span>  
  
-   <span data-ttu-id="8d227-119">使用您指定為範本的自訂封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-119">Use a custom package that you have designated as a template.</span></span>  
  
-   <span data-ttu-id="8d227-120">執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯入和匯出精靈</span><span class="sxs-lookup"><span data-stu-id="8d227-120">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard</span></span>  
  
     <span data-ttu-id="8d227-121">[ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯入和匯出精靈] 會建立一個完整封裝來進行簡單的匯入或匯出。</span><span class="sxs-lookup"><span data-stu-id="8d227-121">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard creates a complete package for a simple import or export.</span></span> <span data-ttu-id="8d227-122">此精靈會設定連接、來源和目的地，並加入所需的任何資料轉換，好讓您立即執行匯入或匯出。</span><span class="sxs-lookup"><span data-stu-id="8d227-122">This wizard configures the connections, source, and destination, and adds any data transformations that are required to let you run the import or export immediately.</span></span> <span data-ttu-id="8d227-123">您可以選擇儲存封裝以供日後再次執行，或是在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中精簡及增強封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-123">You can optionally save the package to run it again later, or to refine and enhance the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="8d227-124">但是，如果您儲存封裝，您必須將封裝加入現有的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，然後才可以在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中變更封裝或執行封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-124">However, if you save the package, you must add the package to an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project before you can change the package or run the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="8d227-125">下列程序將描述如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中建立或刪除封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-125">The following procedures describe how to create or delete a package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8d227-126">如需示範如何使用預設封裝範本建立基本封裝的影片，請參閱 [建立基本封裝 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=131023)。</span><span class="sxs-lookup"><span data-stu-id="8d227-126">For a video that demonstrates how to create a basic package using the default package template, see [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023).</span></span>  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a><span data-ttu-id="8d227-127">若要在 SQL Server Data Tools 中使用封裝範本來建立封裝</span><span class="sxs-lookup"><span data-stu-id="8d227-127">To create a package in SQL Server Data Tools using the Package Template</span></span>  
  
1.  <span data-ttu-id="8d227-128">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟您要在其中建立封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="8d227-128">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="8d227-129">在方案總管中，以滑鼠右鍵按一下 [SSIS 封裝]\*\*\*\* 資料夾，然後按一下 [新增 SSIS 封裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8d227-129">In Solution Explorer, right-click the **SSIS Packages** folder, and then click **New SSIS Package**.</span></span>  
  
3.  <span data-ttu-id="8d227-130">(選擇性) 將控制流程、資料流程工作和事件處理常式加入封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-130">Optionally, add control flow, data flow tasks, and event handlers to the package.</span></span> <span data-ttu-id="8d227-131">如需詳細資訊，請參閱[控制流程](control-flow/control-flow.md)、[資料流程](data-flow/data-flow.md)和 [Integration Services &#40;SSIS&#41; 事件處理常式](integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="8d227-131">For more information, see [Control Flow](control-flow/control-flow.md), [Data Flow](data-flow/data-flow.md), and [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md).</span></span>  
  
4.  <span data-ttu-id="8d227-132">在 **[檔案]** 功能表上按一下 **[儲存選取項目]** 以儲存新封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-132">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8d227-133">您可以儲存空白封裝。</span><span class="sxs-lookup"><span data-stu-id="8d227-133">You can save an empty package.</span></span>  
  
  
