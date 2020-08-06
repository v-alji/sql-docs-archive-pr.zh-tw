---
title: 進程對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.processdialog.f1
ms.assetid: c065248c-9001-4f0c-928f-9c59eccb618b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 369c121713894bba9b2ce6c40aa2869de49eaa72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708721"
---
# <a name="process-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="8c4b9-102">處理對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="8c4b9-102">Process Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8c4b9-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [處理]\*\*\*\* 對話方塊，即可處理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-103">Use the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to process [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="8c4b9-104">您可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中依下列方式顯示 [處理]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="8c4b9-104">You can display the **Process** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] by:</span></span>  
  
-   <span data-ttu-id="8c4b9-105">以滑鼠右鍵按一下方案總管\*\*\*\* 中的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案、Cube、維度或採礦結構，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-105">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, cube, dimension, or mining structure in **Solution Explorer** and selecting **Process**.</span></span>  
  
-   <span data-ttu-id="8c4b9-106">從 [Cube 設計師]\*\*\*\* 的每個頁面、[維度設計師]\*\*\*\* 的每個頁面或 [資料採礦模型設計師]\*\*\*\* 的 [採礦結構]\*\*\*\* 和 [採礦模型]\*\*\*\* 頁面上的工具列，選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-106">Selecting **Process** from the toolbar on every page of **Cube Designer**, every page of **Dimension Designer**, or the **Mining Structure** and **Mining Models** pages of **Data Mining Model Designer**.</span></span>  
  
-   <span data-ttu-id="8c4b9-107">以滑鼠右鍵按一下 [資料採礦模型設計師]\*\*\*\* 之 [採礦模型]\*\*\*\* 頁面中的採礦模型，然後選取 [處理採礦結構和所有模型]\*\*\*\* 或 [處理模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-107">Right-clicking a mining model in the **Mining Models** page of **Data Mining Model Designer** and selecting **Process Mining Structure and All Models** or **Process Model**.</span></span>  
  
 <span data-ttu-id="8c4b9-108">您可以在 [SQL Server Management Studio]\*\*\*\* 中依下列方式顯示 [處理]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="8c4b9-108">You can display the **Process** dialog box in **SQL Server Management Studio** by:</span></span>  
  
-   <span data-ttu-id="8c4b9-109">以滑鼠右鍵按一下物件總管\*\*\*\* 中的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫、Cube、量值群組、資料分割、維度、採礦結構或採礦模型，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-109">Right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, cube, measure group, partition, dimension, mining structure, or mining model in **Object Explorer** and selecting **Process**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c4b9-110">選項</span><span class="sxs-lookup"><span data-stu-id="8c4b9-110">Options</span></span>  
 <span data-ttu-id="8c4b9-111">**物件清單**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-111">**Object list**</span></span>  
 <span data-ttu-id="8c4b9-112">選取要處理的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件，以及要套用的處理選項和設定。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-112">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects to be processed and the processing options and settings to be applied.</span></span> <span data-ttu-id="8c4b9-113">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="8c4b9-113">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="8c4b9-114">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-114">**Object Name**</span></span>  
 <span data-ttu-id="8c4b9-115">顯示要處理的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-115">Displays the name of the object to be processed.</span></span> <span data-ttu-id="8c4b9-116">名稱左邊的圖示會指出物件類型。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-116">The icon to the left of the name indicates the object type.</span></span>  
  
 <span data-ttu-id="8c4b9-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-117">**Type**</span></span>  
 <span data-ttu-id="8c4b9-118">顯示要處理的物件類型。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-118">Displays the type of the object to be processed.</span></span>  
  
 <span data-ttu-id="8c4b9-119">**處理選項**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-119">**Process Options**</span></span>  
 <span data-ttu-id="8c4b9-120">選取在選取之物件上要執行的處理類型。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-120">Select the type of processing to perform on the selected object.</span></span> <span data-ttu-id="8c4b9-121">如需可用處理選項的詳細資訊，請參閱多[維度模型物件處理](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-121">For more information about available processing options, see [Multidimensional Model Object Processing](multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8c4b9-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-122">**Settings**</span></span>  
 <span data-ttu-id="8c4b9-123">在 Cube、量值群組或資料分割的 [處理選項]\*\*\*\* 中選擇 [處理累加]\*\*\*\* 時，會顯示 [設定]\*\*\*\* 超連結。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-123">Displays the **Configure** hyperlink when you choose **Process Incremental** in **Process Options** for cubes, measure groups, or partitions.</span></span> <span data-ttu-id="8c4b9-124">按一下 [設定]\*\*\*\* 即可啟動 [累加式更新]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-124">Click **Configure** to launch the **Incremental Update** dialog box.</span></span> <span data-ttu-id="8c4b9-125">如需 [累加式更新]\*\*\*\* 對話方塊的詳細資訊，請參閱[累加式更新對話方塊 &#40;Analysis Services - 多維度資料&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-125">For more information about the **Incremental Update** dialog box, see [Incremental Update Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](incremental-update-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="8c4b9-126">**移除**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-126">**Remove**</span></span>  
 <span data-ttu-id="8c4b9-127">按一下即可從 [物件清單]\*\*\*\* 中移除選取的項目。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-127">Click to remove the selected items from **Object list**.</span></span>  
  
 <span data-ttu-id="8c4b9-128">**影響分析**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-128">**Impact Analysis**</span></span>  
 <span data-ttu-id="8c4b9-129">按一下即可開啟 [影響分析]\*\*\*\* 對話方塊，並顯示受到處理工作影響的物件。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-129">Click to open the **Impact Analysis** dialog box and display the objects that will be affected by the processing task.</span></span> <span data-ttu-id="8c4b9-130">如需 [影響分析]\*\*\*\* 對話方塊的詳細資訊，請參閱[影響分析對話方塊 &#40;Analysis Services - 多維度資料&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-130">For more information about the **Impact Analysis** dialog box, see [Impact Analysis Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](impact-analysis-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c4b9-131">當選取 [變更設定]\*\*\*\* 對話方塊中的 [處理受影響的物件]\*\*\*\* 選項時，就會停用此選項。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-131">This option is disabled when the **Process affected objects** option is selected in the **Change Settings** dialog box.</span></span>  
  
 <span data-ttu-id="8c4b9-132">**變更設定**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-132">**Change Settings**</span></span>  
 <span data-ttu-id="8c4b9-133">按一下即可開啟 [變更設定]\*\*\*\* 對話方塊，以變更會影響所選取物件之處理方式的設定，包括批次處理設定、回寫設定以及維度索引鍵錯誤設定。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-133">Click to open the **Change Settings** dialog box and change the settings that govern processing of the selected objects, including batch processing settings, writeback settings, and dimension key error settings.</span></span> <span data-ttu-id="8c4b9-134">如需 [變更設定]\*\*\*\* 對話方塊的詳細資訊，請參閱[變更設定對話方塊 &#40;Analysis Services - 多維度資料&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-134">For more information about the **Change Settings** dialog box, see [Change Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](change-settings-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="8c4b9-135">**執行**</span><span class="sxs-lookup"><span data-stu-id="8c4b9-135">**Run**</span></span>  
 <span data-ttu-id="8c4b9-136">按一下即可處理物件。</span><span class="sxs-lookup"><span data-stu-id="8c4b9-136">Click to process the objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4b9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c4b9-137">See Also</span></span>  
 <span data-ttu-id="8c4b9-138">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="8c4b9-138">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="8c4b9-139">[[處理進度] 對話方塊 &#40;Analysis Services-多維度資料&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)</span><span class="sxs-lookup"><span data-stu-id="8c4b9-139">[Process Progress Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](process-progress-dialog-box-analysis-services-multidimensional-data.md)</span></span>  
  
  
