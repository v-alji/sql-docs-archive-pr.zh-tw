---
title: 警告 (資料庫設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf635460187fe56f4811de5090cada002ea8ca3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594193"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="b7578-102">警告 (資料庫設計工具) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="b7578-102">Warnings (Database Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b7578-103">使用 [警告]\*\*\*\* 索引標籤，即可檢視和解除全域規則，以及檢視和重新啟用已解除警告的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7578-103">Use the **Warnings** tab to view and dismiss rules globally, and to view and re-enable specific instances of dismissed warnings.</span></span> <span data-ttu-id="b7578-104">**[警告]** 索引標籤會顯示兩個方格： **[設計警告規則]** 和 **[已解除的警告]**。</span><span class="sxs-lookup"><span data-stu-id="b7578-104">The **Warnings** tab displays two grids: **Design Warning Rules** and **Dismissed Warnings**.</span></span>  
  
 <span data-ttu-id="b7578-105">**顯示警告索引標籤**</span><span class="sxs-lookup"><span data-stu-id="b7578-105">**To display the Warnings tab**</span></span>  
  
1.  <span data-ttu-id="b7578-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中開啟 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="b7578-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="b7578-107">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案、按一下 [編輯資料庫]\*\*\*\*，然後按一下 [警告]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7578-107">In **Solution Explorer**, right-click the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, click **Edit Database**, and then click the **Warnings** tab.</span></span>  
  
## <a name="design-warning-rules-grid"></a><span data-ttu-id="b7578-108">設計警告規則方格</span><span class="sxs-lookup"><span data-stu-id="b7578-108">Design Warning Rules Grid</span></span>  
 <span data-ttu-id="b7578-109">**[設計警告規則]** 方格會顯示所有設計警告規則。</span><span class="sxs-lookup"><span data-stu-id="b7578-109">The **Design Warning Rules** grid displays all the design warning rules.</span></span> <span data-ttu-id="b7578-110">此外，這個方格也會控制哪些規則會針對資料庫啟用。</span><span class="sxs-lookup"><span data-stu-id="b7578-110">This grid also controls which rules are enabled for the database.</span></span> <span data-ttu-id="b7578-111">若要啟用或停用警告規則，請選取或清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b7578-111">To enable or disable a warning rule, select or clear its check box.</span></span>  
  
 <span data-ttu-id="b7578-112">**[設計警告規則]** 方格具有下列資料行：</span><span class="sxs-lookup"><span data-stu-id="b7578-112">The **Design Warning Rules** grid has the following columns:</span></span>  
  
 <span data-ttu-id="b7578-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="b7578-113">**Description**</span></span>  
 <span data-ttu-id="b7578-114">顯示規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7578-114">Displays the name of the rule.</span></span> <span data-ttu-id="b7578-115">規則會依類別分組。</span><span class="sxs-lookup"><span data-stu-id="b7578-115">Rules are grouped by category.</span></span>  
  
 <span data-ttu-id="b7578-116">**重要性**</span><span class="sxs-lookup"><span data-stu-id="b7578-116">**Importance**</span></span>  
 <span data-ttu-id="b7578-117">顯示指派給規則的重要性。</span><span class="sxs-lookup"><span data-stu-id="b7578-117">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="b7578-118">**註解**</span><span class="sxs-lookup"><span data-stu-id="b7578-118">**Comments**</span></span>  
 <span data-ttu-id="b7578-119">(選擇性) 允許使用者輸入註解，以便說明解除警告的原因。</span><span class="sxs-lookup"><span data-stu-id="b7578-119">(Optional) Allows the user to type a comment that explains why you are dismissing the warning.</span></span>  
  
## <a name="dismissed-warnings-grid"></a><span data-ttu-id="b7578-120">已解除的警告方格</span><span class="sxs-lookup"><span data-stu-id="b7578-120">Dismissed Warnings Grid</span></span>  
 <span data-ttu-id="b7578-121">**[已解除的警告]** 方格會顯示所有已經從 **[錯誤清單]** 中解除的特定警告項目。</span><span class="sxs-lookup"><span data-stu-id="b7578-121">The **Dismissed Warnings** grid displays all specific warning occurrences that have been dismissed from the **Error List**.</span></span> <span data-ttu-id="b7578-122">若要重新啟用警告，請在方格中選取它，然後按一下 [重新啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7578-122">To re-enable a warning, select it in the grid, and then click **Re-enable**.</span></span>  
  
 <span data-ttu-id="b7578-123">**[已解除的警告]** 方格具有下列項目：</span><span class="sxs-lookup"><span data-stu-id="b7578-123">The **Dismissed Warnings** grid has the following :</span></span>  
  
 <span data-ttu-id="b7578-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="b7578-124">**Object**</span></span>  
 <span data-ttu-id="b7578-125">顯示代表物件類型和物件名稱的圖示。</span><span class="sxs-lookup"><span data-stu-id="b7578-125">Displays an icon that represents the object type and the object name.</span></span>  
  
 <span data-ttu-id="b7578-126">**型別**</span><span class="sxs-lookup"><span data-stu-id="b7578-126">**Type**</span></span>  
 <span data-ttu-id="b7578-127">顯示物件類型。</span><span class="sxs-lookup"><span data-stu-id="b7578-127">Displays the object type.</span></span>  
  
 <span data-ttu-id="b7578-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="b7578-128">**Description**</span></span>  
 <span data-ttu-id="b7578-129">顯示規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="b7578-129">Displays the name of the rule.</span></span>  
  
 <span data-ttu-id="b7578-130">**重要性**</span><span class="sxs-lookup"><span data-stu-id="b7578-130">**Importance**</span></span>  
 <span data-ttu-id="b7578-131">顯示指派給規則的重要性。</span><span class="sxs-lookup"><span data-stu-id="b7578-131">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="b7578-132">**註解**</span><span class="sxs-lookup"><span data-stu-id="b7578-132">**Comments**</span></span>  
 <span data-ttu-id="b7578-133">顯示解除警告時所輸入的註解。</span><span class="sxs-lookup"><span data-stu-id="b7578-133">Displays the comment that was entered when the warning was dismissed.</span></span> <span data-ttu-id="b7578-134">您可以在此新增或修改註解。</span><span class="sxs-lookup"><span data-stu-id="b7578-134">You can add or modify a comment here.</span></span>  
  
 <span data-ttu-id="b7578-135">**重新啟用**</span><span class="sxs-lookup"><span data-stu-id="b7578-135">**Re-enable**</span></span>  
 <span data-ttu-id="b7578-136">重新啟用選取的警告。</span><span class="sxs-lookup"><span data-stu-id="b7578-136">Re-enables the selected warnings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7578-137">如果某個物件具有警告，但是該物件處於無效狀態中，或者您已經手動從專案中移除該物件，則清單中的警告旁邊就會顯示一個錯誤圖示。</span><span class="sxs-lookup"><span data-stu-id="b7578-137">If an object has a warning, but the object is in an invalid state or was manually removed from the project, an error icon appears next to the warning in the list.</span></span> <span data-ttu-id="b7578-138">若要解除警告，請選取它，然後按一下 [重新啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b7578-138">To dismiss the warning, select it and then click **Re-enable**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7578-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7578-139">See Also</span></span>  
 <span data-ttu-id="b7578-140">[關閉警告對話方塊 &#40;Analysis Services-多維度資料&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="b7578-140">[Dismiss Warning Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="b7578-141">一般 &#40;資料庫設計工具&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="b7578-141">General &#40;Database Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
